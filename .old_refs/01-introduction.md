# Introduction (XXX Draft)

## The Inflationary Universe

Over the past 50 years, cosmology has evolved from a data-starved field into a precision science [Turner (2022)](https://arxiv.org/abs/2201.04741). The most successful model, named the "hot Big Bang model" by physicist Steven Weinberg, describes the evolution from an early hot soup of hadrons to the current expanding space-time, populated with galaxies.

Modern cosmology's foundation dates back about 100 years when Albert Einstein introduced General Relativity. In the 1920s, solutions for both static (Einstein, de Sitter) and dynamic universes (Friedmann, Lemaitre) were proposed. Hale and Ritchey invented the modern reflecting telescope, enabling Hubble to discover the expanding universe model.

The "hot" aspect of the Big Bang model comes from the discovery of CMB radiation, estimated at 3.5K by Penzias and Wilson in 1964. Earlier, [Gamow (1948)](https://journals.aps.org/pr/abstract/10.1103/PhysRev.74.505.2) had proposed a hot beginning to explain the origin of chemical elements. A Princeton team, including Dicke and Peebles, interpreted Penzias and Wilson's discovery, suggesting the universe started in a hot, dense state filled with a plasma of particles. As the universe expanded and cooled to $\sim 3000$ K, neutral atoms formed and photons traveled freely about 380,000 years after the Big Bang [Peebles (1968)](https://ui.adsabs.harvard.edu/abs/1968ApJ...153....1P).

The CMB is a powerful tool for probing the early universe. Measurements of CMB anisotropy and polarization have accurately determined six cosmological parameters but also highlighted issues like the horizon and flatness problems. The horizon problem questions the CMB's homogeneity since only points within a small $2^\circ$ cone in the sky are causally connected. The flatness problem arises from the universe's extraordinary flatness, with the total density parameter finely tuned to 1 at a $10^{-40}$ level. To address these issues, [Guth (1981)](https://journals.aps.org/prd/abstract/10.1103/PhysRevD.23.347) proposed the theory of inflation.

Inflation suggests a period of exponential expansion of space around $10^{-36}$ seconds after the Big Bang. This expansion magnified initial quantum fluctuations into perturbations, which evolved into the cosmic structures observed today. Perturbations can be decomposed into scalar, vector, and tensor modes. Due to the universe's expansion, vector perturbations are dissipated and typically ignored in models.

```{note} FLRW Metric
:open:
The scalar and tensor modes are characterized by the FLRW metric tensor:

$$
g_{\mu \nu} = -(1+2\psi)dt^2 + a^2(1+2\phi)dx^i d_y^j(\delta_{ij} + h_{ij})
$$

where:
- $a$ is the scale factor
- $\psi$ and $\phi$ are scalar perturbations, analogous to the potential in Newtonian mechanics. They can be linked to the under and over-density of species in the primordial universe
- $h_{ij} = \begin{bmatrix} 1 - h_{+} & h_{\times} & 0 \\ h_{\times} & 1- h_{+} & 0 \\ 0 & 0 & 1 \end{bmatrix}$ represents the tensor perturbation with the effect similar to gravitational waves with polarization $h_{+}$ and $h_{\times}$, stretching the spacetime as it crosses through.
```

The scalar mode is the main contributor to the CMB spectra as well as to the distribution of galaxy clusters and large-scale structure formation. The primordial power spectrum of scalar perturbation is parameterized in Fourier space with an amplitude $A_S$ and scalar tilt $n_S$:

```{math}
P_S = A_S \left( \dfrac{k}{k_0} \right)^{n_S - 1}
```

Tensor mode provides a much smaller amplitude than the previous scalar mode. The primordial power spectrum of tensor perturbation is parameterized similarly as:

```{math}
P_h = A_T \left( \dfrac{k}{k_0} \right)^{n_T} 
```

We can define a new parameter called the tensor-to-scalar ratio $r = \dfrac{A_T}{A_S}$, which is connected to the energy scale of the slow-rolling inflation field [Linde (2017)](https://arxiv.org/abs/1402.0526):

```{math}
V_{\rm inflation} \sim (1.04 \times 10^{16} \text{GeV})^4 \left( \dfrac{r}{0.01} \right)
```

The parameter $r$ is crucial in inflationary theory, as it is related to both the steepness of the inflation potential and the duration of inflation. Constraining $r$ at the $\mathcal{O}(10^{-3})$ level could reveal new physics of inflation or potentially rule out a vast majority of theoretical models. Currently, the best constraint, $r
< 0.032$ has been obtained from a joint analysis of Planck and BICEP/Keck data by [Tristam (2022)](https://journals.aps.org/prd/abstract/10.1103/PhysRevD.105.083524).

When inflation ends, the perturbation modes continue to evolve in the plasma of dark matter, protons, electrons, photons, and neutrinos. Dark matter deepens the potential wells left by density perturbations, while photons and baryons, tightly coupled by Thomson scattering, create pressure that counteracts gravitational collapse. This results in acoustic oscillations between baryons and photons. The evolution of perturbation modes depends on their scale and the cosmological horizon. Sub-horizon modes evolve, while super-horizon modes remain static. This evolution ceases at recombination when photons decouple and form the last scattering surface, known as CMB.

## Cosmic Microwave Background Polarization

The CMB map was first detected by the COBE satellite [Smoot et al. (1992)](https://ui.adsabs.harvard.edu/abs/1992ApJ...396L...1S). It represents the best-measured thermal black body radiation in nature [Fixsen (2009)](https://arxiv.org/abs/0911.1955), with an average temperature of 2.725 K over all points in the sky. CMB has dipole distortion in temperature due to the motion of the Solar System at about 370 km/s with respect to the CMB. After subtracting the Doppler dipole, the temperature fluctuation is at the scale of $10^{-5} \, \text{K}$, proving the fact that the universe is extremely homogeneous and isotropic.

Due to local quadrupole anisotropy during decoupling, the CMB radiation is polarized at the 10% level. The polarization can be divided into two types: rotational-free E-mode and gradient-free B-mode, analogous to electric and magnetic fields. Large-amplitude scalar perturbations give rise to CMB temperature anisotropies and E-modes. Small-amplitude primordial gravitational waves are expected to generate both E-modes and B-modes. Because only primordial gravitational waves can produce B-modes, it becomes the probe for cosmic inflation. The E-mode polarization comes at a tiny fluctuation scale of $10^{-6}$ K, and B-mode polarization is expected to be $\sim 10-100$ times smaller.

```{figure} ../images/cmb_decomposition.png
---
width: 100%
name: cmb-decomposition
---
Illustration of CMB at different scales, from monopole to polarized anisotropies, decomposed into E-mode and B-mode. *Source:* Josquin Errard.
```

The observed quantities that we use to measure CMB are so-called Stokes parameters $\begin{bmatrix} I \\ Q \\ U \\ V \end{bmatrix}$, where $I$ encodes the temperature, $Q$ and $U$ encode the linear polarization, and $V$ encodes the circular polarization. $Q$ includes the horizontal and vertical directions of polarization, and $U$ includes the $45^\circ$ direction of polarization. $V$ is expected to vanish as Thomson scattering does not generate this type of polarization.

```{figure} ../images/litebird_angular_spectrum.png
---
width: 70%
name: litebird-spectrum
---
*Solid line:* CMB power spectra of temperature anisotropy (top), E-mode polarization (middle), and B-mode polarization (bottom) with present measurements (colored points). *Dashed line:* primordial B-mode spectrum from scale-invariant tensor perturbation with $r = 0.004$ with expected measurement of LiteBIRD (black points). *Source:* [LiteBIRD Collaboration](https://academic.oup.com/ptep/article/2023/4/042F01/6835420?login=false).
```

The statistical properties of the CMB map, which show nearly Gaussian fluctuations, are predominantly described by the 2-point correlation functions. Assuming isotropy in the underlying probability distribution, correlations between anisotropies at different points in the sky depend only on the angle between them. To analyze these correlations, temperature and linear polarization are typically expanded in terms of spherical harmonics:

```{math}
:label: temp-expansion
\Delta T (\hat{n}) = \sum_{l,m} a^T_{lm} Y_{lm}(\hat{n})
```

```{math}
:label: polarization-expansion
Q(\hat{n}) + iU(\hat{n}) = - \sum_{l,m} (a^E_{lm} + ia^B_{lm}) \, {}_2Y_{lm}(\hat{n})
```

The index $\ell$ represents the degree, corresponding to the angular separation $\theta \sim \pi \ell$ in the map, while index $m$ represents the order linked to orientation. The intensity map is expanded using standard spherical harmonics $Y_{lm}$, whereas the polarization map is expanded using spin-weighted spherical harmonics $_{\pm 2}Y_{lm}$.

We can form the angular power spectra from the expansion coefficients $a^T_{lm}$, $a^E_{lm}$, and $a^B_{lm}$ as:

```{math}
:label: angular-power-spectra
C_l^{XY} = \dfrac{1}{2l+1} \sum_m a_{lm}^X a_{lm}^{Y*}
```

where $X$ and $Y$ are either T, E, or B.

The best results of CMB anisotropies and E-modes including $C_l^{TT}$, $C_l^{TE}$, and $C_l^{EE}$ come from WMAP [Bennett et al. (2013)](https://arxiv.org/abs/1212.5225) and [Planck Collaboration (2020)](https://arxiv.org/abs/1807.06209), covering a huge multipole $l$ range. Lensing B-mode was discovered through cross-correlation by South Pole Telescope [Hanson et al. (2013)](https://arxiv.org/abs/1307.5830) with the help of Herschel Space Observatory, then directly measured by POLARBEAR [Ade et al. (2014)](https://arxiv.org/abs/1312.6646), ACT and BICEP/Keck [Ade et al. (2015)](https://arxiv.org/abs/1502.00612) experiments. The primordial $C_l^{BB}$ remains the target for the next generation of CMB experiments since it would be direct evidence for inflationary gravitational waves.

## Challenge of Instrumental Effects for the Inflationary B-modes

Upcoming projects such as ground-based SO, CMB-S4, and spaceborne LiteBIRD, with the expectation of reaching $r \sim \mathcal{O}(10^{-3})$, require us to accurately distinguish the CMB blackbody from other sources: astrophysical sources (polarized dust and synchrotron), atmosphere for ground-based telescopes, and instrumental systematic effects.

```{figure} ../images/cmb_components.png
---
width: 80%
name: cmb-contaminants
---
Illustration of various contaminants affecting the CMB signal before it reaches the detectors. These contaminants include astrophysical sources, atmospheric interference, instrumental systematic effects and noise. *Source:* Josquin Errard.
```

The main framework that has been proven to be successful in precedent experiments is the component separation method, including two main approaches: blind and parametric. The blind method imposes conditions on spectra and separates the components based on their statistical properties; some examples include `SMICA`, `NILC`, and `SEVEM`. The parametric method introduces a model based on the physical nature of the phenomena, such as emission laws of foregrounds or multiplication of the gains of instruments. Notable examples are `FGBuster` and `Commander`.

With the deployment of more detectors in new CMB instruments, sensitivity, and data volume have increased significantly, leading to greater instrumental complexity. Consequently, there are challenges in characterizing and calibrating systematic effects that do not average out over time and contaminate measurements. Numerous instrumental effects must be accounted for in the calibration process, including the optical reflection on the cover of a telescope, the beam's far side lobes [Leloup et al. (2023)](https://arxiv.org/abs/2306.00001), gains, bandpasses [Ghigna et al. (2020)](https://arxiv.org/abs/2007.01933), polarization angles [Abitbol et al. (2021)](https://arxiv.org/abs/2103.05616), and electronic cross-talk [Fabbian et al. (2021)](https://arxiv.org/abs/2104.08133). These well-known hardware characteristics can broadly lead to two main effects on the Stokes parameters: Intensity-to-Polarization leakage (I-to-P or $T \rightarrow E, B$), and Cross-Polarization ($E \leftrightarrow B$).

**XXX Draft**