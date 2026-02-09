---
title: Introduction
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
date: 2026-02-09
---

# Brief Recalls on homogeneous cosmology

## Basic notions 
- FLRW metric:
$$
ds^2 = dt^2 - a(t)^2 d\mathbf{x}^2
$$
- Friedmann equation:
$$
H^2 = \dfrac{8 \pi G}{3} \rho_{\rm tot} = \dfrac{8 \pi }{3 M_{pl}^2} \rho_{\rm tot}
$$
where $\rho_{\rm tot} = \rho_m + \rho_r + \rho_\Lambda$.
  - Matter (cold dark matter and baryons): $$\rho_m = \rho_c +  \rho_b \propto a^{-3}$$
  - Radiation (photon and neutrino): $$\rho_r = \rho_\gamma +  \rho_\nu \propto a^{-4}$$
  - Cosmological constant: $$\rho_\Lambda \propto a^0$$

## Newly fixed quantities in $\Lambda$CDM
### Density of radiation
$$
\rho_\gamma = \dfrac{g_\gamma}{(2\pi)^3} \int d^3p \, E(p) f(p) = \dfrac{\pi^2}{30} g_\gamma T^4
$$
where 
  - $f(p) = \dfrac{1}{e^{(E - \mu)/T} - 1}$ for Bose-Einstein distribution. At early times, the chemical potentials of all particles are so small that they can be neglected.
  - $E(p) = \sqrt{p^2 + m^2} = p$ for radiation.

So, with $g_\gamma = 2$ (spin-1 massless particle):
$$
\rho_\gamma = \dfrac{\pi^2}{15} T^4
$$

```{note} Radiation density
:class: dropdown

We have
$$
\rho_\gamma = \dfrac{g_\gamma}{(2\pi)^3} \int d^3p \, E(p) f(p) = \dfrac{g}{2 \pi^2} \int dp \dfrac{p^3}{e^{p/T} - 1}
$$
Setting $\xi = p / T$
$$
\rho_\gamma = \dfrac{g_\gamma}{2 \pi^2} T^4 \int_0^\infty d\xi \dfrac{\xi^3}{e^\xi - 1} = \dfrac{g_\gamma}{2 \pi^2} T^4 \zeta(4) \Gamma(4) = \dfrac{g_\gamma}{2 \pi^2} T^4 \dfrac{\pi^4}{90} 3! = \dfrac{\pi^2}{30} g_\gamma T^4
$$
```

### Time of decoupling

Decoupling occurs shortly after recombination, about $3.8 \times 10^{5}$ years after the Big Bang ($z \simeq 1100$). As the Universe expands and cools to $T \sim 3000 \,\mathrm{K}$, electrons and protons combine to form neutral hydrogen. This process strongly reduces the number of free electrons, causing the photon–electron interaction rate to drop below the expansion rate of the Universe. As a result, photons decouple from the thermal plasma and begin to propagate freely through spacetime.
$$
e^- + p \leftrightarrow H + \gamma
$$

.... Saha equations here ....

## Quantities to be measured
- $a_\Lambda$: equality between $\Lambda$-dominated and matter-dominated era.
- $a_{eq}$: equality between matter-dominated and radiation-dominated era.
- $\{h, \Omega_b, \Omega_m\}$: abundance of baryons and CDM.
- primordial perturbation, star formation, etc.

### Definition
#### Hubble radius:
$$
R_H \equiv \dfrac{c}{H} = 3000 h^{-1} \, \rm Mpc
$$
which is the radius of curvature of ($t, x^i$) sections of spacetime.
```{caution}
if $a = \rm const$, then $R_H = \infty$. The definition only works for evolving scale factor.
```

```{note}
If the characteristic scale satisfies $\lambda \ll R_H$, spacetime curvature effects are negligible. One can then approximate the metric locally as flat and work in Minkowski spacetime.
```

#### Age
- Hubble parameter: $$H = \dfrac{\dot a}{a} = H_0 \sqrt{\Omega_{m,0} \, a^{-3} + \Omega_{r,0} \, a^{-4} + \Omega_\Lambda}$$
- Redshift: $$ 1 + z = \dfrac{a_0}{a}$$
- Age of the universe:
$$
t = \int_{t_{BB}}^{t_0} dt = \int_{a_{BB}}^{a_0} \dfrac{da}{a H(a)} = \int_{0}^\infty \dfrac{dz}{(1+z)H(z)} = ({\text{number of order 1}}) \times R_H
$$

#### Conformal age
Define
$$
d\eta = \dfrac{dt}{a(t)}
$$
So
$$
ds^2 = a^2(\eta) (d\eta^2 - d \mathbf{x}^2)
$$
where
$$
\eta - \eta_{BB} = \int_{\eta_{BB}}^{\eta} d\eta = \int_{t_{BB}}^{t} \dfrac{dt}{a} = \int_z^{z_{BB} = \infty} \dfrac{dz}{H(z)}
$$
If we see $\eta_{BB} = 0$, the conformal time today:
$$
\eta_0 =  \int_0^\infty \dfrac{dz}{H(z)}
$$
#### Causal horizon
$$
d(t_1, t_2) = a(t_2) \int_{t_1}^{t_2} \dfrac{dt}{a}
$$
#### Radius of observable universe
$$
d_{obs} = a_0 \int_{t_{dec}}^{t_0} \dfrac{dt}{a} = d(t_{dec}, t_0)
$$
We set $a_0 = 1$
$$
d_{obs} = \int_{0}^{1} \dfrac{da}{a^2 H(a)} = \int_0^\infty \dfrac{dz}{H(z)}
$$

```{exercise} Radiation-dominated universe
:label: rad_universe
For radiation dominated universe and flat universe
$$\Omega_r = \Omega_{r,0} a^{-4} \quad \text{and} \quad \Omega_{r,0} = 1$$
The first Friedmann equation becomes
$$
H^2 = H_0^2 \Omega_r = H_0^2 a^{-4}
$$
The distance becomes
$$
d_{obs} = \int_0^1 \dfrac{c da}{a^2 H_0 a^{-2}} = R_{H_0} \int_0^1 da = R_{H_0}
$$
where $R_{H_0} = \dfrac{c}{H_0}$ is the current Hubble radius.
```

```{exercise} Einstein-de Sitter universe
:label: matter_universe
For matter dominated universe and flat universe
$$\Omega_m = \Omega_{m,0} a^{-3} \quad \text{and} \quad \Omega_{m,0} = 1$$
The first Friedmann equation becomes
$$
H^2 = H_0^2 \Omega_m = H_0^2 a^{-3}
$$
The distance becomes
$$
d_{obs} =  R_{H_0} \int_0^1 da \, a^{-1/2} = R_{H_0} 2 a^{1/2} \mid_0^1 = 2 R_{H_0}
$$
```

Your formula is correct. I’ll just rewrite it **cleanly and completely**, in the same style, and add the missing context so it’s unambiguous.

---

## Fourier expansion

We decompose perturbations into comoving Fourier modes with wavenumber (k).
The corresponding **physical wavelength** evolves with the expansion as
$$
\boxed{
\lambda(t) = a(t)\,\lambda_{\rm com}
= a(t)\,\frac{2\pi}{k}
}
$$
where
* $k$: **comoving** wavenumber (constant in time)
* $\lambda_{\rm com} = 2\pi/k$: comoving wavelength

```{note}
1. Only the physical wavenumber
$$
k_{\rm phys} = \frac{k}{a}
$$
has physical meaning.
2. Horizon crossing occurs when the physical wavelength equals the Hubble radius:
$$
\lambda(t) \simeq H^{-1}(t)
$$
3. This condition is equivalently written in comoving form as
$$
k \simeq aH
$$
4. The comoving Hubble radius is
$$
(aH)^{-1}
$$
Since
$$
H = \frac{\dot a}{a}
\quad \Rightarrow \quad
aH = \dot a
$$
the quantity $aH$ sets the horizon scale in comoving units.
```

```{important}
Modes are labeled by constant comoving $k$, while their physical size grows as $a(t)$

* $k \gg aH$: **sub-horizon** (causal microphysics)
* $k \ll aH$: **super-horizon** (frozen evolution)

```