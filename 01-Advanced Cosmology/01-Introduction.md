# Brief Recalls on Homogeneous Cosmology

## 1. FLRW Metric and Friedmann Equations
### 1.1 The FLRW Metric
For a homogeneous and isotropic universe:
$$
ds^2 = dt^2 - a(t)^2 d\mathbf{x}^2
$$
where $a(t)$ is the scale factor.

### 1.2 The Friedmann Equation
From Einstein's equations for the FLRW metric:
$$
H^2 = \dfrac{8 \pi G}{3} \rho_{\rm tot} = \dfrac{8 \pi }{3 M_{pl}^2} \rho_{\rm tot}
$$
where $H = \dot{a}/a$ is the Hubble parameter, and $\rho_{\rm tot}$ is the total energy density.

## 2. Energy Constituents of the Universe
### 2.1 Matter, Radiation, and Cosmological Constant
The total density comprises:
- **Matter** (cold dark matter and baryons): $\rho_m = \rho_c +  \rho_b \propto a^{-3}$
- **Radiation** (photon and neutrino): $\rho_r = \rho_\gamma +  \rho_\nu \propto a^{-4}$
- **Cosmological constant**: $\rho_\Lambda \propto a^0$

### 2.2 Density Parameters and Their Evolution
Define the critical density today:
$$
\rho_{c,0} = \dfrac{3H_0^2}{8\pi G}
$$
The density parameter for component $i$ is:
$$
\Omega_i = \dfrac{\rho_i}{\rho_c}
$$
Today, we have:
$$
\Omega_{i,0} = \dfrac{\rho_{i,0}}{\rho_{c,0}}
$$
For a flat universe (as supported by observations):
$$
\sum_i \Omega_{i,0} = 1
$$
The Friedmann equation becomes:
$$
H^2 = H_0^2 \left[ \Omega_{m,0} a^{-3} + \Omega_{r,0} a^{-4} + \Omega_{\Lambda,0} \right]
$$
where we set $a_0 = 1$.

```{exercise} Derivation of $\sum \Omega_i = 1$ for flat universe
:class: dropdown
For $k=0$ (flat), the Friedmann equation is:
$$
H^2 = \dfrac{8\pi G}{3} \rho_{\rm tot}
$$
At present time $t_0$:
$$
H_0^2 = \dfrac{8\pi G}{3} \rho_{\rm tot,0}
$$
Dividing the general equation by $H_0^2$:
$$
\left(\dfrac{H}{H_0}\right)^2 = \dfrac{\rho_{\rm tot}}{\rho_{\rm tot,0}} \dfrac{\rho_{\rm tot,0}}{\rho_{c,0}} = \dfrac{\rho_{\rm tot}}{\rho_{\rm tot,0}} \Omega_{\rm tot,0}
$$
But $\rho_{\rm tot}/\rho_{\rm tot,0}$ is the evolution of total density. Alternatively, we can write:
$$
H^2 = H_0^2 \sum_i \Omega_{i,0} a^{-3(1+w_i)}
$$
where $w_i$ is the equation of state parameter. Evaluating at $t_0$ ($a=1$):
$$
H_0^2 = H_0^2 \sum_i \Omega_{i,0} \quad \Rightarrow \quad \sum_i \Omega_{i,0} = 1
$$
```

## 3. Radiation in the Early Universe
### 3.1 Photon Energy Density
For a relativistic boson with $g$ internal degrees of freedom:
$$
\rho = \dfrac{g}{(2\pi)^3} \int d^3p \, E(p) f(p)
$$
with Bose-Einstein distribution $f(p) = (e^{E/T} - 1)^{-1}$ and $E = p$ for massless particles.

For photons ($g_\gamma = 2$):
$$
\rho_\gamma = \dfrac{\pi^2}{15} T^4
$$

```{exercise} Detailed derivation of $\rho_\gamma$
:class: dropdown

We have:
$$
\rho_\gamma = \dfrac{g_\gamma}{(2\pi)^3} \int d^3p \, p \dfrac{1}{e^{p/T} - 1}
$$
In spherical coordinates:
$$
\rho_\gamma = \dfrac{g_\gamma}{2\pi^2} \int_0^\infty dp \dfrac{p^3}{e^{p/T} - 1}
$$
Set $\xi = p/T$:
$$
\rho_\gamma = \dfrac{g_\gamma}{2\pi^2} T^4 \int_0^\infty d\xi \dfrac{\xi^3}{e^\xi - 1}
$$
The integral is $\Gamma(4)\zeta(4) = 3! \cdot \dfrac{\pi^4}{90} = \dfrac{\pi^4}{15}$:
$$
\rho_\gamma = \dfrac{g_\gamma}{2\pi^2} T^4 \cdot \dfrac{\pi^4}{15} = \dfrac{\pi^2}{30} g_\gamma T^4
$$
For $g_\gamma = 2$: $\rho_\gamma = \dfrac{\pi^2}{15} T^4$.
```

### 3.2 Neutrino Energy Density and Temperature
Neutrinos are fermions with Fermi-Dirac distribution:
$$
f(p) = \dfrac{1}{e^{E/T} + 1}
$$
After electron-positron annihilation, the photon temperature increases relative to neutrinos.

```{exercise} Derivation of $T_\nu/T_\gamma = (4/11)^{1/3}$
:class: dropdown

Before annihilation ($T \gtrsim 1$ MeV), photons, electrons, positrons, and neutrinos are in thermal equilibrium with $T_\gamma = T_\nu = T_e$.

The entropy density is:
$$
s = \dfrac{\rho + p}{T} = \dfrac{2\pi^2}{45} g_{*s} T^3
$$
where $g_{*s}$ counts relativistic degrees of freedom.

Before annihilation: $g_{*s} = g_\gamma + \frac{7}{8}(g_e + g_{\bar{e}} + g_\nu + g_{\bar{\nu}})$:
- Photons: $g_\gamma = 2$
- Electrons and positrons: $g_e = g_{\bar{e}} = 2$ (each)
- Neutrinos: 3 flavors × 2 spin states = 6 (only left-handed)
- Antineutrinos: also 6

So:
$$
g_{*s}^{\text{before}} = 2 + \frac{7}{8}(2+2+6+6) = 2 + \frac{7}{8} \times 16 = 2 + 14 = 16
$$

After annihilation ($T \lesssim 0.5$ MeV), only photons and neutrinos remain relativistic:
- Photons: $g_\gamma = 2$
- Neutrinos: 3 flavors × 2 spin states = 6

But neutrinos have decoupled and don't receive the entropy from $e^+e^-$ annihilation. The entropy in photons and $e^+e^-$ is transferred to photons alone. Entropy conservation gives:
$$
g_{*s}^{\text{before}} T^3 a^3 = g_{*s}^{\text{after}} T'^3 a^3
$$
where $T'$ is the new photon temperature. After annihilation, for photons:
$$
g_{*s}^{\text{after, photons}} = 2
$$
For neutrinos, which decoupled earlier:
$$
g_{*s}^{\text{after, neutrinos}} = \frac{7}{8} \times 6 = \frac{42}{8} = 5.25
$$

But we consider the photon temperature change. Before annihilation, the entropy in photons+$e^+e^-$ is:
$$
s_{\gamma+e^\pm} = \frac{2\pi^2}{45} \left(2 + \frac{7}{8} \times 4\right) T^3 = \frac{2\pi^2}{45} \times \frac{11}{2} T^3
$$
After annihilation, only photons:
$$
s_{\gamma}' = \frac{2\pi^2}{45} \times 2 \times T'^3
$$
Entropy conservation (for the coupled plasma) gives:
$$
\frac{11}{2} T^3 a^3 = 2 T'^3 a^3 \quad \Rightarrow \quad \frac{T'}{T} = \left(\frac{11}{4}\right)^{1/3}
$$
Thus after annihilation:
$$
T_\nu = T, \quad T_\gamma = T' = \left(\frac{11}{4}\right)^{1/3} T
$$
So:
$$
\frac{T_\nu}{T_\gamma} = \left(\frac{4}{11}\right)^{1/3} \approx 0.714
$$
```

For neutrinos ($g_\nu = 6$):
$$
\rho_\nu = \dfrac{7}{8} \left( \dfrac{\pi^2}{30} g_\nu T_\nu^4 \right) = 3 \dfrac{7}{8} \left( \dfrac{T_\nu}{T_\gamma} \right)^{4} \rho_\gamma
$$
Using $(T_\nu/T_\gamma)^4 = (4/11)^{4/3}$:
$$
\rho_\nu = 3 \dfrac{7}{8} \left( \dfrac{4}{11} \right)^{4/3} \rho_\gamma
$$

## 4. The Epoch of Decoupling
### 4.1 Recombination and Photon Decoupling
Decoupling occurs at $z \simeq 1100$ ($t \sim 3.8 \times 10^{5}$ years). When $T \sim 3000$ K, electrons and protons combine:
$$
e^- + p \leftrightarrow H + \gamma
$$
The reduction of free electrons drops the Thomson scattering rate below the expansion rate.

### 4.2 The Saha Equation
For the reaction $e^- + p \leftrightarrow H + \gamma$, equilibrium gives:
$$
\dfrac{n_e n_p}{n_H} = \left( \dfrac{m_e T}{2\pi} \right)^{3/2} e^{-B/T}
$$
where $B = 13.6$ eV is the binding energy. Defining the ionization fraction $X_e = n_e/(n_e + n_H)$ and using $n_b = n_p + n_H$:
$$
\dfrac{X_e^2}{1 - X_e} = \dfrac{1}{n_b} \left( \dfrac{m_e T}{2\pi} \right)^{3/2} e^{-B/T}
$$
At $z \simeq 1100$, $X_e$ drops sharply (from nearly 1 to $\sim 10^{-3}$).

## 5. Cosmological Distances and Times
### 5.1 Hubble Radius
$$
R_H \equiv \dfrac{c}{H} = 3000 h^{-1} \, \rm Mpc
$$
is the radius of curvature of spatial sections.

```{caution}
If $a = \rm const$, then $R_H = \infty$. This definition only works for evolving scale factor.
```

```{note}
If $\lambda \ll R_H$, spacetime curvature effects are negligible and Minkowski approximation holds.
```

### 5.2 Age of the Universe
- **Hubble parameter**:
  $$
  H = H_0 \sqrt{\Omega_{m,0} a^{-3} + \Omega_{r,0} a^{-4} + \Omega_\Lambda}
  $$
- **Redshift**: $1 + z = a_0/a$
- **Age**:
  $$
  t = \int_0^{t_0} dt = \int_0^{a_0} \dfrac{da}{a H(a)} = \int_0^\infty \dfrac{dz}{(1+z)H(z)}
  $$

### 5.3 Conformal Time
Define $d\eta = dt/a(t)$, so:
$$
ds^2 = a^2(\eta) (d\eta^2 - d\mathbf{x}^2)
$$
Conformal time elapsed:
$$
\eta = \int \dfrac{dt}{a} = \int \dfrac{da}{a^2 H} = \int \dfrac{dz}{H(z)}
$$
Setting $\eta_{\rm BB} = 0$, conformal time today:
$$
\eta_0 = \int_0^\infty \dfrac{dz}{H(z)}
$$

### 5.4 Causal Horizons
- **Particle horizon** (comoving distance traveled since $t=0$):
  $$
  d_h(t) = a(t) \int_0^t \dfrac{dt'}{a(t')}
  $$
- **Observable universe** (distance to decoupling surface):
  $$
  d_{\rm obs} = a_0 \int_{t_{\rm dec}}^{t_0} \dfrac{dt}{a} = \int_{a_{\rm dec}}^{1} \dfrac{da}{a^2 H(a)} = \int_0^{z_{\rm dec}} \dfrac{dz}{H(z)}
  $$

```{exercise} Radiation-dominated universe
:class: dropdown

For a flat, radiation-dominated universe ($\Omega_{r,0}=1$):
$$
H^2 = H_0^2 a^{-4}
$$
The observable distance (setting $c=1$):
$$
d_{\rm obs} = \int_0^1 \dfrac{da}{a^2 H_0 a^{-2}} = \dfrac{1}{H_0} \int_0^1 da = R_{H_0}
$$
where $R_{H_0} = c/H_0$ (restoring $c$, $d_{\rm obs} = c/H_0$).
```

```{exercise} Matter-dominated (Einstein-de Sitter) universe
:class: dropdown

For a flat, matter-dominated universe ($\Omega_{m,0}=1$):
$$
H^2 = H_0^2 a^{-3}
$$
Then:
$$
d_{\rm obs} = \dfrac{1}{H_0} \int_0^1 \dfrac{da}{a^2 a^{-3/2}} = \dfrac{1}{H_0} \int_0^1 da \, a^{-1/2} = \dfrac{2}{H_0} \left[ a^{1/2} \right]_0^1 = 2 R_{H_0}
$$
```

## 6. Fourier Decomposition and Horizon Crossing
We decompose perturbations into comoving Fourier modes with wavenumber $k$. The **physical wavelength** evolves as:
$$
\lambda(t) = a(t) \lambda_{\rm com} = a(t) \dfrac{2\pi}{k}
$$
where $\lambda_{\rm com} = 2\pi/k$ is the comoving wavelength.

```{note}
- The physical wavenumber is $k_{\rm phys} = k/a$.
- **Horizon crossing** occurs when:
  $$
  \lambda(t) \simeq H^{-1}(t) \quad \Leftrightarrow \quad k \simeq aH
  $$
- The comoving Hubble radius is $(aH)^{-1} = (\dot{a})^{-1}$.
```

```{important}
Modes are labeled by constant comoving $k$:
- $k \gg aH$: **sub-horizon** (microphysics operates)
- $k \ll aH$: **super-horizon** (frozen, no causal contact)
```
