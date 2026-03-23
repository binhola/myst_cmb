# Moriond Talks

## CMB Blind component separation - Alessandro
- ILC component separation $\to$ remove foreground
- Problems:
  - Complex spatial structure
  - Complex spectral structure

- Need a component separation with **minimal assumptions**.
  - ILC: minimize the *variance*, need the *covariance* of the data $$\mathbf{w} = [A_{CMB}^T C^{-1}A_{CMB}]^{-1} A_{CMB}^T C^{-1}$$
  - MultiClustering-ILC (MC-ILC) $\to$ improve the fit on the large scales.
  - Generalized-ILC $\to$ improve on the noise, fit for $F$ instead of A $$A = F + N $$

- Check the biases on different $r$ values and foreground models
- Include the template of foregrounds into likelihood.

- Broom packages 

- Blind detection of systematic residuals after component separation.

- Frontier?
  - Apply to SO data $\to$ transfer function. (some preliminary results)
  - Apply Broom to Planck data.

### Questions
- Why using templates ? Can not model statistically ? 
  - Alessandro: even using the templates it wouldn't leak into the variance ? 
  
## Spectral Distortion, Bayronic feedback, FIRAS - Fabbian Guillio
Spectral Distortion from perfect blackbody of CMB. Distortions when energy is injected or redistributed and the photon do not have enough time to thermolize. 

- Compton scattering (before recombination)
- SZ effect (after recombination)

The last experiment is COBE (1990s) - FIRAS. Can we do better with the modern techniques? (170 channels)
- Original efforts
  - Correlations between different components $\to$ need to be careful when do separation.
  - Original: template fitting $\to$ prone to error because they use very high-frequency extrapolation
  - Refit: adding the distortion.

- Current efforts
  - Foregrounds 100x distortions
  - Monopole modeling, MCMC

Results
- $\langle y \rangle$-distortions measurements (new measurement after 30 years)
- reduce the impact of foreground residuals.

Why it is important?
- probe of gas thermodynamics (AGN/SN feedback)
- physics of the gas in the dark matter halo
- Compare with BAO, weak lensing
- Modeling with hydrodynamic simulation
- Constraint on galaxy formation models
  - Direct constrains are weak ? $\to$ likelihood-free inference

- Galaxy lensing ????

:::{seealso}
[Constraint on spectral distortions from FIRAS data](https://arxiv.org/html/2512.03038v1)
:::
## Spectral distortion future missions, FOSSIL - Bruno Maffei
Status
- Proposal: PIXIE (NASA), PRISTINE (ESA), FOSSIL (ESA)

Goals of FOSSIL
- $\mu$-distortion: probing density perturbations + dark sectors
  - Little red dots, BH mergers
- $y$-distortion: ....
- Star formation + dust 
- Instruments: more frequency bands (30-2000 GHz) $\to$ understand the foreground much better ? 

Plans
- Launch 2041

### Questions

## The Simons Observatory - Daniel Dutcher
- LAT, SAT
- LF 30/40 GHz, MF 90/150 GHz, UHF 220/280 

Science goals
- Tensor to scalar ratio $\to$ primordial GWs, inflation
- Non-gaussianity
- Neutrino mass
- Cluster catalog
:::{seealso}
[SO forecast](https://arxiv.org/pdf/2503.00636)
:::

- LAT $\to$ start to take data
  - 6m telescope
  - LAT receiver - the largest cryogenic mm-wave camera.
  - Optics Tube is much powerful than ACT 

- SAT $\to$ already have data
  - 3 instruments with 2 MF, 1 UHF
  - 12000 detectors in each instruments 
  - Half-wave plate
  - TES detector (go-to for 20 years) $\to$ improve on the sensitivity ? 

Initial data: 90/150 GHz SATs
- Few months of data $\to$ but very good agreement with other experiments

LATs
- detector performance >= sensitivity targets in all bands
- Lensing $600$ deg$^2$

Results
- Got the temperature map in 180 hours comparable with ACT in 5 years
  - see the points sources (good resolution)

Upgrades
- 13 optic tubes: 30000 $\to$ 60000 (NSF grant) (Jan 2026)
- 3 more SATs: 1 LF, 2 MF: 24000 $\to$ 48000