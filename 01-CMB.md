# Introduction

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
< 0.032$ has been obtained from a joint analysis of Planck and BICEP/Keck data [Tristam (2022)](https://arxiv.org/abs/2112.07961).

When inflation ends, the perturbation modes continue to evolve in the plasma of dark matter, protons, electrons, photons, and neutrinos. Dark matter deepens the potential wells left by density perturbations, while photons and baryons, tightly coupled by Thomson scattering, create pressure that counteracts gravitational collapse. This results in acoustic oscillations between baryons and photons. The evolution of perturbation modes depends on their scale and the cosmological horizon. Sub-horizon modes evolve, while super-horizon modes remain static. This evolution ceases at recombination when photons decouple and form the last scattering surface, known as CMB.