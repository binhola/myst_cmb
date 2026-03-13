---
title: Compact Objects
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
date: 2026-03-13
---

## What are compact objects? How are they formed?

Compact objects are the final remnants of stellar evolution, born when normal stars exhaust their nuclear fuel and can no longer support themselves against gravitational collapse. They represent the ultimate fate of stars and are laboratories for extreme physics: high densities, strong gravity, and exotic states of matter.

### Stellar evolution in a nutshell

The fate of a star is determined primarily by its initial mass. The diagram below summarizes the main evolutionary paths:

```{mermaid}
flowchart TD
    A[Nebula] --> B{Protostar}
    B --> C[Main Sequence Star]
    C --> D{Initial Mass}
    
    D -->|Low/Medium Mass < 8 M☉| E[Red Giant]
    E --> F[Planetary Nebula]
    F --> G[White Dwarf]
    
    D -->|High Mass > 8 M☉| H[Red Supergiant]
    H --> I[Supernova]
    I --> J{Core Mass}
    J -->|1.4 M☉ < M < ~3 M☉| K[Neutron Star]
    J -->|M > ~3 M☉| L[Black Hole]
```

:::{note} Progenitor mass thresholds
- **Low/medium mass** ($M \lesssim 8 M_\odot$): End as white dwarfs
- **High mass** ($8 M_\odot \lesssim M \lesssim 20 M_\odot$): End as neutron stars
- **Very high mass** ($M \gtrsim 20 M_\odot$): End as black holes

These thresholds are approximate and depend on metallicity, rotation, and binary interactions.
:::

## What are they? Properties of compact objects

### Compactness parameter

A useful quantity to characterize compact objects is the **compactness**:

```{math}
C = \frac{GM}{R c^2}
```

This dimensionless parameter measures how close an object is to forming an event horizon (where $C = 0.5$ corresponds to the Schwarzschild radius $R_s = 2GM/c^2$).

| Object | Typical Radius (km) | Typical Mass ($M_\odot$) | Compactness $C$ | Density $\rho$ (g/cm³) |
|--------|---------------------|--------------------------|-----------------|------------------------|
| Sun | $7 \times 10^5$ | 1 | $\sim 10^{-6}$ | $\sim 1$ |
| White Dwarf | $\sim 10^4$ | 0.5–1.4 | $\sim 10^{-4}$ | $\sim 10^6$ |
| Neutron Star | $\sim 10$ | 1.2–2.2 | $\sim 0.1$–0.3 | $\sim 10^{14}$–$10^{15}$ |
| Black Hole | $R_s = 2GM/c^2$ | $\gtrsim 3$ | $0.5$ | Singularity |

### White Dwarfs

White dwarfs are the remnants of low- and medium-mass stars. They are supported against gravitational collapse by **electron degeneracy pressure**, a quantum mechanical effect arising from the Pauli exclusion principle.

```{important} Key properties
- **Composition**: Mainly carbon and oxygen (for typical white dwarfs), sometimes helium or oxygen-neon-magnesium for more massive progenitors.
- **Mass-radius relation**: Unlike normal stars, more massive white dwarfs are **smaller**:
  $$R \propto M^{-1/3}$$
- **Maximum mass**: The **Chandrasekhar limit** sets the maximum mass for a white dwarf supported by electron degeneracy pressure:
  $$M_{\text{Ch}} \approx 1.4 M_\odot$$
- **Cooling**: White dwarfs have no nuclear fusion; they simply cool over billions of years, gradually fading from view.
```

### Neutron Stars

Neutron stars are the remnants of core-collapse supernovae from massive stars. When the core collapses beyond white dwarf densities, electrons are captured by protons ($p + e^- \to n + \nu_e$), producing a star composed primarily of neutrons. They are supported by **neutron degeneracy pressure** and **nuclear repulsion** at supranuclear densities.

```{important} Key properties
- **Extreme density**: $\rho \sim 10^{14}$–$10^{15}$ g/cm³ — comparable to nuclear density.
- **Mass range**: Observed neutron star masses range from $\sim 1.1 M_\odot$ to $\sim 2.2 M_\odot$, with the most precisely measured being the Hulse-Taylor binary pulsar at $1.44 M_\odot$.
- **Maximum mass**: The Tolman-Oppenheimer-Volkoff (TOV) limit sets the maximum mass for a neutron star, above which it collapses to a black hole. The exact value depends on the unknown equation of state at supranuclear densities, but is around $2.2$–$2.5 M_\odot$.
- **Radius**: Typically $\sim 10$–$12$ km, remarkably independent of mass.
- **Rotation**: Neutron stars can spin extremely rapidly (periods from milliseconds to seconds) due to conservation of angular momentum during collapse.
- **Magnetic fields**: Extremely strong, up to $10^{15}$ G for magnetars.
- **Observations**: Pulsars (rotating neutron stars with beams of radiation), X-ray binaries, and gravitational wave events (binary neutron star mergers like GW170817).
```

### Black Holes

When the remnant core exceeds the maximum mass for a neutron star, nothing can prevent complete gravitational collapse. A black hole forms, characterized by an **event horizon** — a surface from which nothing, not even light, can escape.

```{important} Key properties
- **Event horizon**: Located at the Schwarzschild radius $R_s = 2GM/c^2$ for a non-rotating (Schwarzschild) black hole.
- **No hair theorem**: Stationary black holes in general relativity are completely described by just three parameters: mass $M$, spin $J$, and electric charge $Q$ (though charge is negligible astrophysically).
- **Singularity**: At the center lies a singularity where density and curvature become infinite — a breakdown of classical general relativity requiring quantum gravity.
- **Observational signatures**: Black holes themselves emit no radiation, but can be observed through:
  - Accretion disks (X-ray binaries, active galactic nuclei)
  - Orbital motion of nearby stars (e.g., Sgr A* in our galaxy)
  - Gravitational waves from mergers (LIGO/Virgo events)
  - Black hole shadows (Event Horizon Telescope images of M87* and Sgr A*)
```

## How do we measure their properties?

### Determining the radius

```{prf:remark} Radius measurement techniques
- **Eclipsing binaries**: If a compact object is in a binary system that eclipses, the duration of eclipses gives information about the size.
- **Light curves**: Modeling the emission from accretion disks or pulsars can constrain the radius.
- **Thermal spectra**: For neutron stars, fitting their thermal X-ray emission to model atmospheres yields radius estimates.
- **Gravitational waves**: The tidal deformability measured in binary neutron star mergers (e.g., GW170817) constrains the radius.
- **X-ray bursts**: Type I X-ray bursts on neutron star surfaces provide radius constraints through Eddington limit measurements.
```

### Determining the mass

```{prf:remark} Mass measurement techniques
- **Binary systems (Newtonian/Keplerian)**: For a binary system, measuring the orbital period $P$ and semi-major axis $a$ gives the total mass via Kepler's law: $P^2 = \frac{4\pi^2 a^3}{G(M_1+M_2)}$.
- **Radial velocity curves**: For spectroscopic binaries, the Doppler shifts give the mass function, which provides a lower limit on the companion mass.
- **Double neutron star binaries**: When both objects are pulsars, precise timing yields the masses of both components with extraordinary accuracy.
- **Gravitational waves**: The chirp mass $\mathcal{M} = (m_1 m_2)^{3/5}/(m_1+m_2)^{1/5}$ is measured directly from the waveform; with additional information (higher harmonics, tidal effects), individual masses can be extracted.
- **Eclipsing X-ray binaries**: Combining eclipse duration with radial velocity measurements yields mass constraints.
```

## Stellar structure equations

The internal structure of a star (or compact object) in hydrostatic equilibrium is governed by two fundamental equations.

```{prf:definition} Mass continuity
$$\frac{dm(r)}{dr} = 4\pi r^2 \rho(r)$$
```

This equation simply states that the mass enclosed within radius $r$ increases with $r$ according to the density profile.

```{prf:definition} Hydrostatic equilibrium
$$\frac{dP(r)}{dr} = -\frac{G m(r) \rho(r)}{r^2}$$
```

This equation balances the inward force of gravity against the outward pressure gradient. For compact objects, the pressure $P$ is not thermal but comes from degeneracy or nuclear forces.

:::{note} General relativistic correction
For neutron stars and black holes, Newtonian hydrostatic equilibrium is insufficient. The correct description is given by the **Tolman-Oppenheimer-Volkoff (TOV) equation**:
$$\frac{dP}{dr} = -\frac{G m(r) \rho(r)}{r^2} \left(1 + \frac{P}{\rho c^2}\right) \left(1 + \frac{4\pi r^3 P}{m(r) c^2}\right) \left(1 - \frac{2G m(r)}{r c^2}\right)^{-1}$$
which includes relativistic corrections to both gravity and pressure.
:::

## The Chandrasekhar limit

The Chandrasekhar limit is the maximum mass of a white dwarf supported by electron degeneracy pressure. We derive it under simplifying assumptions using polytropic models and the Lane–Emden equation.

```{prf:proof} Derivation of the Chandrasekhar limit
:class: dropdown

**Assumptions**:
- The white dwarf is spherical and in hydrostatic equilibrium.
- The equation of state is that of a completely degenerate electron gas.
- The star is composed of fully ionized matter with mean molecular weight per electron $\mu_e$ (for helium, $\mu_e = 2$; for carbon‑oxygen, also $\mu_e = 2$).
- General relativistic effects are neglected.

### 1. Hydrostatic equilibrium and mass continuity

For a spherically symmetric star, the mass enclosed within radius $r$ is

:::{math}
\frac{dm(r)}{dr} = 4\pi r^2 \rho(r), \qquad m(0)=0.
:::

Hydrostatic equilibrium balances pressure against gravity:

:::{math}
\frac{dP(r)}{dr} = -\frac{G m(r) \rho(r)}{r^2}.
:::

Differentiating the second equation and using the first eliminates $m(r)$:

:::{math}
\frac{d}{dr}\left( \frac{r^2}{\rho} \frac{dP}{dr} \right) = -4\pi G r^2 \rho. \tag{1}
:::

### 2. Polytropic equation of state

For many equations of state it is convenient to adopt a **polytropic form**

:::{math}
P = K \rho^{1 + \frac{1}{n}},
:::

where $K$ is a constant and $n$ is the polytropic index.  
For white dwarfs:
- Non‑relativistic degenerate electrons: $P \propto \rho^{5/3}$  → $n = 3/2$.
- Ultra‑relativistic degenerate electrons: $P \propto \rho^{4/3}$ → $n = 3$.

The Chandrasekhar limit corresponds to the ultra‑relativistic case, so we focus on $n = 3$.

### 3. Dimensionless variables and the Lane–Emden equation

Introduce the dimensionless quantities

:::{math}
\rho(r) = \rho_c \theta^n(r), \qquad r = \alpha \xi,
:::

with $\rho_c$ the central density and $\alpha$ a length scale to be chosen. Substituting $P = K \rho_c^{1+1/n} \theta^{n+1}$ into Eq. (1) gives:

:::{math}
\frac{1}{\xi^2} \frac{d}{d\xi}\left( \xi^2 \frac{d\theta}{d\xi} \right) = -\theta^n,
:::

provided we set

:::{math}
\alpha = \left[ \frac{(n+1)K}{4\pi G} \rho_c^{\frac{1}{n}-1} \right]^{1/2}.
:::

Equation (2) is the **Lane–Emden equation**. The boundary conditions are $\theta(0)=1$, $\theta'(0)=0$ (regularity at the centre). The surface of the star is at the first zero $\xi_1$ where $\theta(\xi_1)=0$.

### 4. Mass of the polytrope

The total mass is

:::{math}
M = \int_0^R 4\pi r^2 \rho \, dr = 4\pi \rho_c \alpha^3 \int_0^{\xi_1} \xi^2 \theta^n \, d\xi.
:::

Using the Lane–Emden equation, the integral can be evaluated:

:::{math}
\int_0^{\xi_1} \xi^2 \theta^n \, d\xi = -\xi_1^2 \theta'(\xi_1).
:::

Hence

:::{math}
M = 4\pi \rho_c \alpha^3 \left[ -\xi_1^2 \theta'(\xi_1) \right]. \tag{3}
:::

For $n=3$, the Lane–Emden equation has been solved numerically; the results are

:::{math}
\xi_1 \approx 6.89685, \qquad -\xi_1^2 \theta'(\xi_1) \approx 2.01824.
:::

### 5. Electron degeneracy pressure in the ultra‑relativistic limit

For a completely degenerate electron gas, the pressure depends on the electron number density $n_e$. In the ultra‑relativistic limit ($p_F \gg m_e c$),

:::{math}
P = \frac{\hbar c}{12\pi^2} (3\pi^2 n_e)^{4/3}.
:::

The electron density is related to the mass density by $n_e = \dfrac{\rho}{\mu_e m_u}$, where $m_u \approx m_p$ is the atomic mass unit and $\mu_e = A/Z$ (for fully ionized matter). For typical white dwarf compositions (carbon‑oxygen), $Z/A = 1/2$, so $\mu_e = 2$.

Thus

:::{math}
P = \frac{\hbar c}{12\pi^2} \left( \frac{3\pi^2}{\mu_e m_p} \right)^{4/3} \rho^{4/3}.
:::

Comparing with the polytropic form $P = K \rho^{1+1/n}$ for $n=3$, we identify

:::{math}
K = \frac{\hbar c}{12\pi^2} \left( \frac{3\pi^2}{\mu_e m_p} \right)^{4/3}.
:::

### 6. Eliminating $\rho_c$ and $\alpha$ from the mass formula

From the definition of $\alpha$ for $n=3$:

:::{math}
\alpha^2 = \frac{4K}{4\pi G} \rho_c^{-2/3} = \frac{K}{\pi G} \rho_c^{-2/3}.
:::

Hence $\alpha^3 = \left( \dfrac{K}{\pi G} \right)^{3/2} \rho_c^{-1}$.

Substitute into Eq. (3):

:::{math}
M = 4\pi \rho_c \left( \frac{K}{\pi G} \right)^{3/2} \rho_c^{-1} \left[ -\xi_1^2 \theta'(\xi_1) \right]
   = 4\pi \left( \frac{K}{\pi G} \right)^{3/2} \left[ -\xi_1^2 \theta'(\xi_1) \right].
:::

Notice that $\rho_c$ has cancelled! This means that for $n=3$ the total mass is **independent** of the central density – a unique mass is obtained.

Insert the numerical factor and $K$:

:::{math}
M_{\text{Ch}} = 4\pi \left( \frac{1}{\pi G} \frac{\hbar c}{12\pi^2} \left( \frac{3\pi^2}{\mu_e m_p} \right)^{4/3} \right)^{3/2} \times 2.01824.
:::

### 7. Simplifying the constants

First, combine the powers:

:::{math}
\left( \frac{\hbar c}{12\pi^2} \right)^{3/2} \left( \frac{3\pi^2}{\mu_e m_p} \right)^2
= \frac{(\hbar c)^{3/2}}{(12\pi^2)^{3/2}} \frac{9\pi^4}{\mu_e^2 m_p^2}.
:::

Also $4\pi \times \left( \dfrac{1}{\pi G} \right)^{3/2} = 4\pi \times \pi^{-3/2} G^{-3/2} = 4\pi^{-1/2} G^{-3/2}$.

Thus

:::{math}
M_{\text{Ch}} = 2.01824 \times 4\pi^{-1/2} G^{-3/2} \frac{(\hbar c)^{3/2}}{(12\pi^2)^{3/2}} \frac{9\pi^4}{\mu_e^2 m_p^2}.
:::

Now combine the pure numbers. A careful evaluation (using $\pi \approx 3.1416$) gives

:::{math}
M_{\text{Ch}} = \frac{3.098}{\mu_e^2} \frac{(\hbar c)^{3/2}}{G^{3/2} m_p^2}.
:::

Inserting the physical constants in SI units:

- $\hbar = 1.055 \times 10^{-34}$ J·s,
- $c = 2.998 \times 10^8$ m/s,
- $G = 6.674 \times 10^{-11}$ m³/kg·s²,
- $m_p = 1.673 \times 10^{-27}$ kg,
- $M_\odot = 1.989 \times 10^{30}$ kg.

One finds

:::{math}
M_{\text{Ch}} = 1.457 \left( \frac{2}{\mu_e} \right)^2 M_\odot.
:::

For $\mu_e = 2$, this yields

:::{math}
\boxed{ M_{\text{Ch}} \approx 1.44 M_\odot }.
:::
```

```{important} Physical interpretation
The Chandrasekhar limit arises because electron degeneracy pressure becomes ineffective at extremely high densities:
- As mass increases, the star contracts and electrons become relativistic ($p_e \sim m_e c$)
- Relativistic degeneracy pressure scales as $P \propto \rho^{4/3}$, which is the same scaling as the pressure required for hydrostatic equilibrium ($P \propto \rho^{4/3}$)
- The proportionality constants are such that a critical mass exists where the two are equal; above this mass, gravity wins and collapse proceeds
```

## Beyond white dwarfs: neutron stars and the TOV limit

For neutron stars, the situation is more complex due to:
- General relativistic effects (strong gravity)
- Unknown equation of state at supranuclear densities
- Possible exotic matter (hyperons, quark matter)

The maximum mass for a neutron star (the TOV limit) is typically $2.2$–$2.5 M_\odot$, with the exact value providing crucial constraints on nuclear physics.

## Summary and key takeaways

```{important} Key takeaways
1. **Compact objects** are the final remnants of stellar evolution: white dwarfs, neutron stars, and black holes.
2. **Compactness** $C = GM/Rc^2$ quantifies how relativistic an object is, ranging from $10^{-6}$ (Sun) to $0.5$ (black hole).
3. **White dwarfs** are supported by electron degeneracy pressure, with a maximum mass $M_{\text{Ch}} \approx 1.4 M_\odot$.
4. **Neutron stars** are supported by neutron degeneracy pressure and nuclear forces, with masses $1.1$–$2.2 M_\odot$ and radii $\sim 10$ km.
5. **Black holes** are characterized by an event horizon and described by just mass, spin, and charge.
6. **Mass and radius measurements** come from binary dynamics, thermal spectra, eclipses, and gravitational waves.
7. The **Chandrasekhar limit** follows from balancing gravity with relativistic degeneracy pressure and explains why white dwarfs cannot exceed $\sim 1.4 M_\odot$.
```

These extreme objects continue to challenge our understanding of physics and provide unique laboratories for testing general relativity, nuclear physics, and quantum mechanics in regimes inaccessible on Earth.