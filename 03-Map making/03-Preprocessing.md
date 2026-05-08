# Simon Observatory ISO data
:::{important} Preprocessing
In practice, map-making is the final step of a longer data-reduction pipeline.

Before any map-making algorithm can be applied, the raw detector timestreams must be cleaned, calibrated, and validated. This is the **preprocessing** phase. 
:::
The full preprocessing pipeline on the Simons Observatory Small Aperture Telescope (SAT) data is performed on the `sotodlib` software package.

The two key configuration files that control the pipeline are:

- **The context file** (e.g. `use_this_local_260115.yaml`): tells `sotodlib` where to find all the metadata databases (detector calibration, pointing models, HWP angles, focal plane geometry, absolute calibration, etc). It is the entry point for loading any observation.
- **The preprocessing config file** (e.g. `preprocessing_config_20251216_init.yaml`): defines the full sequence of processing steps applied to the TOD, their parameters, and which outputs are saved to the archive.

#### The context file
The context file is a YAML file that acts as a manifest of all metadata databases associated with a given telescope (for example, `satp3`, the third SAT). It contains:

- **`obsfiledb`**: SQLite database mapping observation IDs to raw data files on disk.
- **`obsdb`**: SQLite database listing all observations with their timestamps, scan parameters, and tags.
- **`metadata`**: A list of database entries, each providing one type of per-detector or per-observation metadata. The key entries are summarised below.

| Label | Content | `on_missing` |
|---|---|---|
| `smurf` | SMURF readout channel assignments and detector set definitions | `fail` |
| `assignment` | Detector-to-pixel matching on the focal plane | `fail` |
| `wafer_info` | Wafer geometry and bandpass assignments | `fail` |
| `det_cal` | Per-detector calibration: $\tau_\text{eff}$, `phase_to_pW`, $R_n$, $R_\text{frac}$, $P_\text{sat}$ | `fail` |
| `relcal` | Relative calibration factors (atmosphere-derived) | `trim` |
| `pointing_model` | Telescope pointing correction coefficients | warn |
| `focal_plane` | Detector positions on the focal plane | `fail` |
| `hwp_model` | HWP angle model parameters | — |
| `hwp_solution` | Reconstructed HWP angles per sample | — |
| `abscal` | Absolute calibration in CMB temperature units | — |
| `wobble_params` | HWP wobble correction parameters | — |

```{note}
Entries with `on_missing: fail` will raise an exception if no matching database entry is found for a given observation. Entries with `on_missing: trim` will silently drop detectors that lack metadata. This asymmetry is intentional — missing calibration or pointing data is fatal, but missing relative calibration just means those detectors are excluded.
```

The `subobs` field controls how the TOD is split into sub-observations for parallel processing:

```yaml
subobs:
  use: ['wafer_slot', 'wafer.bandpass']
  label: wafer_slot
```

This means each wafer slot and frequency band is processed independently. For `satp3` with three wafers and two bands each, this produces up to six independent processing streams per observation.

#### The preprocessing pipeline

The preprocessing pipeline is a linear sequence of named steps. Each step can compute a quantity (`calc`), save it to the archive (`save`), flag or remove detectors (`select`), or modify the TOD in-place (`process`). Steps marked `skip_on_sim: True` are skipped when running on simulations.

The pipeline can be grouped into five logical phases.

```{figure} ../images/so_preprocessing_flowchart.svg
---
name: preprocessing-flowchart
alt: Preprocessing flowchart
---
Overview of the SO SAT preprocessing pipeline for `satp3`.
```

##### Phase 1 — Initialisation and instrument model

These steps reconstruct the instrument state from raw metadata before any signal processing.

**`pointing_model`** (`skip_on_sim: True`)
Applies the telescope pointing model to convert raw encoder angles into sky coordinates. The model is stored in the context file under `pointing_model`. This step is skipped for simulations because simulated data already has perfect pointing.

**`hwp_angle_model`** (`skip_on_sim: True`)
Reconstructs the HWP rotation angle $\psi_t$ at every sample from the optical encoder data and the model stored in `hwp_angle_model`. The `on_sign_ambiguous: fail` setting means the pipeline halts if the HWP rotation direction cannot be determined unambiguously — a sign error here would flip the sign of all $U$ maps.

**`correct_iir_params`**
Reads the IIR (infinite impulse response) filter parameters that the SMURF readout system applied to the detector timestreams in hardware. These parameters are needed later for the `fourier_filter` deconvolution step. This step does not modify the TOD; it just loads the parameters.

---

##### Phase 2 — Detector flagging and cuts

These steps identify and remove bad detectors and bad samples before any signal cleaning. The order matters: coarser cuts come first so that later, more expensive steps do not waste time on detectors that will be cut anyway.

**`smurfgaps_flags`** (`skip_on_sim: True`)
Flags samples where the SMURF readout dropped packets (data gaps). A buffer of 200 samples around each gap is also flagged to avoid edge effects from later filtering steps.

**`dark_dets`**
Identifies detectors that are not optically coupled (dark detectors). These are identified by their anomalously low response and are removed from further processing.

**`fp_flags`**
Applies focal plane quality flags from the `det_cal` database. This removes detectors that are known to be non-functional based on characterisation data taken outside of science observations.

**`detcal_nan_cuts`**
Removes any detector for which any of the key calibration parameters (`tau_eff`, `phase_to_pW`, `r_n`, `r_frac`, `p_sat`) is NaN. These detectors cannot be calibrated and must be excluded.

**`flag_turnarounds`**
Flags the scan turnaround periods — the brief intervals at the end of each left-right scan stroke when the telescope decelerates and reverses direction. The turnarounds are identified by a drop in scan speed below threshold, with a 4-second buffer on each side. Turnaround samples are masked in all subsequent steps and excluded from the final maps.

**`det_bias_flags`**
Checks that each detector is operating in a valid bias state by verifying that:
- $R_\text{frac} \in [0.05, 0.95]$ (detector is superconducting transition, not normal or fully SC)
- $P_\text{sat} \in [1\,\mu\text{W},\, 20\,\mu\text{W}]$ (reasonable saturation power)
- $R_n \in [0, 0.1]\,\Omega$ (reasonable normal resistance)
- $S_I \in [-10^9, -10]\,\text{A/W}$ (negative responsivity, as expected for a TES)

Detectors outside these ranges are flagged and removed.

**`trends`**
Detects detectors with excessively large linear drifts over 10-second intervals (threshold: 2.5 in normalised units). A strongly trending detector is usually thermally unstable or has a bias point problem. Any detector flagged by this step is removed.

---

##### Phase 3 — Jump detection and glitch filling

Detector timestreams from TES bolometers can contain two types of discontinuities: slow jumps (thermal events, cosmic rays) and fast $2\pi$ phase jumps (phase-unwrapping errors in the SMURF readout). Both are handled in two separate passes.

**Pass 1 — Slow jumps**

**`jumps` (slow_jumps)**
Scans the TOD with an 800-sample rolling window for jumps larger than 20$\sigma$. These are typically cosmic ray glitches or sudden thermal events.

**`fix_jumps`** (`skip_on_sim: True`)
Attempts to correct the detected slow jumps in-place by fitting a step model and subtracting it. Uses PCA with 1 mode across neighbouring detectors to estimate the common-mode component of each jump.

**`glitchfill` (for slow jumps)** (`skip_on_sim: True`)
For jumps that cannot be cleanly corrected, replaces the flagged samples with a PCA-based interpolation using the surrounding unflagged samples (`nbuf=10` samples on each side).

**Pass 2 — $2\pi$ phase jumps**

**`jumps` (twopi_jumps)**
Scans with a 30-sample window for jumps consistent with integer multiples of $2\pi$ in the SMURF phase (threshold: $10\sigma$). These are readout artefacts and are more frequent than slow jumps.

**`fix_jumps` and `glitchfill` ($2\pi$)**
Same procedure as for slow jumps, applied to the $2\pi$ jump flags.

```{note}
The jump detection and filling is run twice in this order — slow jumps first, then $2\pi$ jumps — because $2\pi$ jumps are smaller in amplitude and can be masked by the presence of a nearby slow jump if the order is reversed.
```

---

##### Phase 4 — HWPSS estimation and subtraction

This is the most critical preprocessing step for polarisation analysis. The HWP synchronous signal (HWPSS) is a large, spurious polarised signal that arises from emission and reflection of the HWP itself. It appears at harmonics of $4f_\text{HWP}$ in the demodulated TOD and must be removed before map-making.

The HWPSS subtraction is performed **twice** — a coarse first pass before glitch filling, and a refined second pass after — to avoid the HWPSS template being contaminated by unfilled glitches.

**`detrend` (first pass)**
Subtracts the median trend from each detector timestream. This is done before HWPSS estimation to prevent a large DC offset from biasing the template fit.

**`glitches` (pre-HWPSS)**
Detects glitches in the TOD before HWPSS subtraction using a high-pass filter at 6 Hz and a $30\sigma$ threshold over 7 ms windows, evaluated per subscan. Detectors with more than 1000 pre-HWPSS glitches are cut.

**`source_flags`**
Flags samples where the telescope beam is within 20° of the Moon. These samples are excluded from the HWPSS template estimation and from the final maps.

**`combine_flags` (pre_hwpss_flags)**
Combines all flags computed so far into a single `pre_hwpss_flags` mask. This mask is passed to `estimate_hwpss` to exclude contaminated samples from the template fit.

**`calibrate` (phase to pW)**
Converts the raw detector signal from SMURF phase units (radians) to physical power units (pW) using the `phase_to_pW` calibration factor from `det_cal`. This must be done before HWPSS estimation because the template amplitude is stored in physical units.

**`estimate_hwpss` (first pass)**
Fits a template model of the HWPSS as a function of HWP angle $\psi$, using the unflagged samples. The template is a Fourier series in $\psi$ evaluated at harmonics of $f_\text{HWP}$. The fitted template amplitudes are stored as `pre_hwpss_stats`.

**`subtract_hwpss` (first pass)**
Subtracts the fitted HWPSS template from the signal TOD. After this step, the dominant periodic signal at $4f_\text{HWP}$ is largely removed.

**`glitchfill` (post first-pass subtraction)** (`skip_on_sim: True`)
Fills the glitches identified by `glitches_pre_hwpss` and `source_flags` using PCA interpolation.

**`glitches` (post-HWPSS)**
Runs a second glitch detection pass on the HWPSS-subtracted TOD. The threshold is tighter here (max 100 glitches per detector, versus 1000 before) because residual large excursions after HWPSS subtraction indicate a genuine data quality problem.

**`combine_flags` (glitch_flags)**
Combines all glitch and jump flags into the final `glitch_flags` mask.

**`estimate_hwpss` (second pass)**
Re-estimates the HWPSS template using the cleaner, glitch-filled TOD and the updated `glitch_flags` mask. This produces a better template (`post_hwpss_stats`) because the glitches no longer bias the fit.

**`subtract_hwpss` (second pass)**
Subtracts the refined HWPSS template. After this step, the HWPSS residual should be at the noise floor for most detectors.

**`glitchfill` (post second-pass)** (`skip_on_sim: True`)
Final glitch fill pass for any remaining flagged samples.

**`detrend` (second pass)**
Subtracts the median trend again after HWPSS subtraction, as the subtraction can introduce a small residual offset.

```{important}
The two-pass HWPSS subtraction is necessary because the initial glitch detection (pass 1) is done on data that still contains the HWPSS. A glitch sitting on top of the HWPSS waveform can be misidentified or missed. After the first HWPSS subtraction, glitches are much more visible, and the second pass produces a cleaner template and a more complete glitch mask.
```

---

##### Phase 5 — Final cuts, calibration, and demodulation

**`ptp_flags`**
Flags detectors or subscans where the peak-to-peak amplitude or kurtosis of the signal exceeds threshold after HWPSS subtraction. High kurtosis indicates non-Gaussian noise, which typically signals a contaminated subscan.

**`psd` and `noise`**
Computes the power spectral density of the cleaned TOD and fits the $1/f$ noise model:

$$
P(f) = \sigma^2\left[1 + \left(\frac{f_\text{knee}}{f}\right)^\alpha\right]
$$

The white noise level $\sigma^2$ is estimated in the band $[5, 20]$ Hz. The fit uses fixed white noise with free $f_\text{knee} \in [0.3, 20]$ Hz and $\alpha \in [1, 6]$. Detectors are cut if their white noise is outside $[2, 80]\,\mu\text{K}\sqrt{\text{s}}$ or their $f_\text{knee} > 7$ Hz.

```{note}
The noise model parameters are saved as `noiseT` and are used downstream by the map-maker (as `inv_noise` in `ATOPMapMaker`) to apply optimal $\mathbf{N}^{-1}$ weighting. Getting this fit right is therefore important — a poor noise model leads to suboptimal weighting and potentially correlated noise in the maps.
```

**`cut_bad_dist`**
Removes detectors whose white noise level is an outlier within the array distribution, even if it passes the absolute cuts above. This catches detectors that are anomalously noisy relative to their neighbours.

**`calibrate` (relative calibration)**
Applies the relative calibration factor `relcal.rel_factor` to equalise detector responses across the array. Detectors missing this factor are cut.

**`fourier_filter` (IIR deconvolution)**
Deconvolves the IIR anti-aliasing filter that was applied in hardware by the SMURF readout. Applied in Fourier space as a multiplication by $1/H_\text{IIR}(f)$.

**`fourier_filter` (time constant deconvolution)**
Deconvolves the detector time constant $\tau_\text{eff}$ (the thermal response time of the TES bolometer). The transfer function is $H_\tau(f) = 1/(1 + 2\pi i f \tau_\text{eff})$, so the deconvolution multiplies each Fourier mode by $1 + 2\pi i f \tau_\text{eff}$.

**`calibrate` (absolute calibration)**
Applies the absolute calibration factor `abscal.abscal_cmb` to convert from pW to CMB temperature units ($\mu\text{K}_\text{CMB}$).

**`apodize`**
Applies a cosine taper to the first and last 2000 samples of each detector timestream. This suppresses ringing at the edges of the TOD when the Fourier filters are applied in `demodulate`.

**`demodulate`**
This is the step that extracts the polarisation signal. The raw TES signal after HWPSS subtraction contains the sky signal modulated at $4f_\text{HWP}$:

$$
d_t \approx I + Q\cos(4\psi_t) + U\sin(4\psi_t)
$$

Demodulation extracts $Q$ and $U$ by multiplying the TOD by $\cos(4\psi_t)$ and $\sin(4\psi_t)$ respectively, then applying a low-pass filter at $1.9\,f_\text{HWP}$ to isolate the baseband polarisation signal. A band-pass filter centred at $4f_\text{HWP}$ with width $3.8\,f_\text{HWP}$ is applied first to isolate the modulated signal before demodulation. The output consists of three timestreams per detector: `dsT` (total intensity), `demodQ`, and `demodU`.

After demodulation, the sample rate is effectively halved (Nyquist of the low-pass filter is $\sim 1.9\,f_\text{HWP}$).

**`tod_stats`**
Computes per-subscan statistics (mean, std, skew, kurtosis, peak-to-peak) for each of `dsT`, `demodQ`, and `demodU`. These are used by the next step.

**`noisy_subscan_flags`**
Flags individual subscans (not entire detectors) where the demodulated statistics indicate a problem:
- `nstd_lim = 3.0`: subscan std more than $3\times$ the median across subscans
- `ptp_lim = 0.8`: peak-to-peak fraction above 0.8
- `kurt_lim = 0.5`, `skew_lim = 0.5`: non-Gaussianity thresholds
- `noisy_detector_lim = 0.5`: detector flagged if more than 50% of its subscans are bad

**`combine_flags` (final)**
Produces three final flag combinations for the three scan directions (left, right, combined), incorporating all previously computed flags. These are the masks passed to the map-maker.

---

#### Summary of outputs

After preprocessing, the archive contains for each observation:

- Three demodulated TOD arrays: `dsT`, `demodQ`, `demodU`
- Final sample masks: `glitch_flags`, `glitch_flags_left`, `glitch_flags_right`
- Noise model parameters: `noiseT` ($\sigma^2$, $f_\text{knee}$, $\alpha$ per detector)
- Pointing information and HWP angles (loaded from context at map-making time)

These are the direct inputs to the map-maker. The `ATOPMapMaker` described in the previous section stores `demodQ` and `demodU`, uses `glitch_flags` as its sample mask, and uses `noiseT` to construct the $\mathbf{N}^{-1}$ operator.

<!-- ```{note}
`dsT` (the total intensity demodulated timestream) is **not** used by `ATOPMapMaker` because POMME marginalises over the unpolarised signal — it is absorbed into the template amplitudes $\mathbf{a}$. The intensity channel is saved for diagnostic purposes and for cross-checks, but the polarisation maps are derived from `demodQ` and `demodU` only.
``` -->

<!-- #### Common failure modes

The pipeline will abort or produce suspicious results in several well-known situations. Checking these first saves a lot of debugging time.

**The job completes but produces no valid detectors.** Usually caused by a mismatch between the context file version and the observation date. Check that `det_cal`, `assignment`, and `focal_plane` all have entries for the observation in question by querying the SQLite databases directly.

**$f_\text{knee}$ cut removes most detectors.** If a large fraction of detectors fails `max_fknee: 7.0`, the atmosphere was likely very bad during the observation, or the HWPSS subtraction failed (leaving residual signal that appears as $1/f$ noise). Check the HWPSS residual and the weather log for that observation.

**`hwp_angle_model` fails with `on_sign_ambiguous: fail`.** The HWP rotation direction could not be determined. This usually means the HWP was not spinning during the observation (stowed or starting up). These observations should be excluded from the map-making entirely.

**Maps show stripes aligned with the scan direction.** The $\tau \cdot f_\text{knee}$ product is too large — the POMME template blocks are longer than the noise coherence time, introducing inter-pixel correlations. Reduce `atop_tau` in the map-making config, or check whether `max_fknee` should be tighter to exclude high-noise observations. -->