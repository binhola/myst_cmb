---
title: Linearized GR and Gravitational Waves
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
---

# Linearized Gravity with Sources and Gravitational Waves

## 1. Perturbation theory with sources

We consider a small perturbation around Minkowski spacetime:

$$
g_{\mu \nu} = \eta_{\mu \nu} + h_{\mu \nu}, \qquad |h_{\mu \nu}| \ll 1.
$$

The linearized Einstein equation in the presence of a stress-energy tensor $T_{\mu\nu}$ (taken to be first order in perturbations) is:

```{math}
:label: linear_E_eq
G^{(1)}_{\mu \nu}(h_{\alpha \beta}) = \frac{8 \pi G}{c^4} T^{(1)}_{\mu \nu},
```

where $G^{(1)}_{\mu \nu}$ is the linearized Einstein tensor. At zeroth order, $G_{\mu \nu}(\eta_{\alpha \beta}) = 0$ since Minkowski spacetime is a vacuum solution.

### 1.1 Trace-reversed perturbation

To simplify the left-hand side, we introduce the trace-reversed perturbation:

```{math}
\bar h_{\mu \nu} = h_{\mu \nu} - \frac{1}{2} \eta_{\mu \nu} h, \qquad h = \eta^{\mu \nu} h_{\mu \nu},
```

which satisfies $\bar h = -h$.

### 1.2 Lorenz gauge condition

We impose the Lorenz gauge condition (also called harmonic gauge):

```{math}
:label: lorenz_gauge
\partial_\mu \bar h^{\mu \nu} = 0.
```

In this gauge, the linearized Einstein equation simplifies dramatically to a wave equation:

```{math}
:label: wave_eq
\square \bar h_{\mu \nu} = -\frac{16 \pi G}{c^4} T_{\mu \nu},
```

where $\square = \eta^{\mu \nu} \partial_\mu \partial_\nu$ is the d'Alembertian operator, and we have dropped the superscript $(1)$ on $T_{\mu\nu}$ for simplicity.

### 1.3 Conservation of energy-momentum

The stress-energy tensor must satisfy the conservation equation $\nabla_\mu T^{\mu \nu} = 0$. To linear order, the Christoffel symbols are first-order in $h$, so products $\Gamma T$ are second-order and can be neglected. Thus:

```{math}
:label: eom
\partial_\mu T^{\mu \nu} = 0.
```

```{note}
At linear order, $h$ does not appear in the conservation equation. This means that while the source $T_{\mu\nu}$ generates gravitational radiation (i.e., $h_{\mu\nu}$), the backreaction of the waves on the source is not included—this requires going to second order.
```

## 2. Gauge freedom and the transverse-traceless gauge

The Lorenz gauge condition {eq}`lorenz_gauge` does not completely fix the coordinate invariance. There remains a residual gauge freedom: we can make an additional coordinate transformation $x^\mu \to x^\mu + \epsilon^\mu$ with $\square \epsilon^\nu = 0$, which preserves the Lorenz condition.

We can use this freedom to impose two further conditions:

```{math}
:label: transverse
\partial^i \bar h_{ij} = 0 \quad \text{(transverse condition)},
```

```{math}
:label: traceless
\bar h = 0 \quad \text{(traceless condition)}.
```

From the traceless condition $\bar h = -h = 0$, we obtain $h = 0$, and consequently:

```{math}
\bar h_{\mu \nu} = h_{\mu \nu}.
```

This combination of conditions (Lorenz + transverse + traceless) defines the **transverse-traceless (TT) gauge**.

```{exercise}
:label: ex1
Show that the conditions {eq}`lorenz_gauge`, {eq}`transverse`, and {eq}`traceless` are equivalent to:
$$
h_{0 \mu} = 0, \qquad h^i_i = 0, \qquad \partial^i h_{ij} = 0.
$$
```

```{important} Practical procedure for obtaining the physical wave:

1. First, solve the wave equation for the spatial components:
   :::{math}
   :label: LEE_ij
   \square \bar h_{ij} = -\frac{16 \pi G}{c^4} T_{ij}.
   :::

2. Then, project the solution onto its transverse-traceless part by imposing $h^i_i = 0$ and $\partial^i h_{ij} = 0$ via a linear projection operator.
```

## 3. Projection onto TT components

If $\bar h_{ij}$ is a solution of {eq}`LEE_ij`, we obtain the physical transverse-traceless part $h^{TT}_{ij}$ through a linear projection:

```{math}
h^{TT}_{ij} = \Lambda_{ij}^{\,\,\, kl}(\mathbf{n}) \, \bar h_{kl},
```

where $\mathbf{n}$ is the direction of propagation of the wave.

Define the transverse projection operator with respect to a unit vector $\mathbf{n}$:

```{math}
P_{ij}(\mathbf{n}) = \delta_{ij} - n_i n_j.
```

Properties:
- $P_{ij} = P_{ji}$ (symmetric)
- $P_{ij} n^j = 0$ (transverse to $\mathbf{n}$)
- $P_{ij} P^{jk} = P_i^{\,k}$ (projector)
- $P_{ij}A^i = A^T_j$
for any vector $A^i = \underbrace{A n^i}_{\text{longitudinal}} + \underbrace{A^{i}_T}_{\text{tranverse}}$

The TT projection operator for a rank-2 tensor is:

```{math}
\Lambda_{ij}^{\,\,\, kl}(\mathbf{n}) = P_i^{\,k} P_j^{\,l} - \frac{1}{2} P_{ij} P^{kl}.
```

This operator extracts the transverse, traceless part of a symmetric tensor.
:::{exercise}
:label: ex2

Check that
1. $\Lambda_{ijkl} \delta^{ij} = 0$ (traceless)
2. $\Lambda_{ijkl} n^i = 0$ (tranverse)
:::

::::{solution} ex2
:class: dropdown

1. $\Lambda^i_{\, \, ikl} = P^i_k P_{il} - \dfrac{1}{2} P^i_i P_{kl} = P_{kl} - P_{kl} = 0$
2. $P_{ik} P_{jl} n^i - \dfrac{1}{2} P_{ij} P_{kl} n^i = 0 - 0 = 0$
::::

We have 
$$
h^{TT}_{ij} = \Lambda_{ij}^{\,\,\, kl}(\mathbf{n}) \, \bar h_{kl} = P_{ik} \bar h^{kl} P_{lj} - \dfrac{1}{2} P_{ij} (P_{lk} \bar h^{kl})
$$
:::{important} Matrix form of $h^{TT}_{ij}$
$$\mathbf{h}^{TT} = \mathbf{P} \mathbf{h} \mathbf{P} - \dfrac{1}{2} \mathbf{P} \rm \, Tr(\mathbf{P} \mathbf{h})$$
:::

:::{exercise}
:label: ex3
Given a binary system is in $(x, z)$ plane we want $h^{TT}_{ij}$ where the detector is on $y$-axis.
:::

::::{solution} ex3
:class: dropdown

- $$\mathbf{n} = 
\begin{pmatrix}
    0 \\ 1 \\ 0 
\end{pmatrix} \Rightarrow 
P_{ij} = \begin{pmatrix}
    1 & 0 & 0 \\
    0 & 1 & 0 \\
    0 & 0 & 1 
\end{pmatrix} - 
\begin{pmatrix}
    0 & 0 & 0 \\
    0 & 1 & 0 \\
    0 & 0 & 0 
\end{pmatrix} = 
\begin{pmatrix}
    1 & 0 & 0 \\
    0 & 0 & 0 \\
    0 & 0 & 1 
\end{pmatrix}
$$
- $$\mathbf{P} \mathbf{h} \mathbf{P} = 
\begin{pmatrix}
    1 & 0 & 0 \\
    0 & 0 & 0 \\
    0 & 0 & 1 
\end{pmatrix}
\begin{pmatrix}
    h_{11} & h_{12} & h_{13} \\
    h_{12} & h_{22} & h_{23} \\
    h_{13} & h_{23} & h_{33} 
\end{pmatrix}
\begin{pmatrix}
    1 & 0 & 0 \\
    0 & 0 & 0 \\
    0 & 0 & 1 
\end{pmatrix} =
\begin{pmatrix}
    h_{11} & 0 & h_{13} \\
    0 & 0 & 0 \\
    h_{13} & 0 & h_{33} 
\end{pmatrix}
$$
- $$\dfrac{1}{2} \mathbf{P} \rm \, Tr(\mathbf{P} \mathbf{h}) = 
\begin{pmatrix}
    \dfrac{h_{11} + h_{33}}{2} & 0 & 0 \\
    0 & 0 & 0 \\
    0 & 0 & \dfrac{h_{11} + h_{33}}{2}
\end{pmatrix}
$$
So $$ \mathbf{h}^{TT} = \begin{pmatrix}
    \dfrac{h_{11} - h_{33}}{2} & 0 & h_{13} \\
    0 & 0 & 0 \\
    h_{13} & 0 & -\dfrac{h_{11} - h_{33}}{2}
\end{pmatrix} $$
This is indeed traceless and tranverse to $\mathbf{y}$-direction.
::::
## 4. Solution of the wave equation with source

Assume the source $T_{ij}$ is localized in a region of characteristic size $L$, and the detector is at a distance $d$ from the source, with $d \gg L$ (far-field regime).

```{figure} ../images/astrocosmo/GW_setup.png
---
width: 70%
align: center
name: fig-gw-setup
---
Geometry for gravitational wave emission: source localized near origin, detector at position $\mathbf{x} = d \mathbf{n}$ with $d \gg L$.
```

The solution to {eq}`wave_eq` is obtained using the retarded Green's function:

```{math}
\bar h_{ij}(t, \mathbf{x}) = \frac{4G}{c^4} \int d^3 y \, \frac{1}{|\mathbf{x} - \mathbf{y}|} \, T_{ij}\left(t - \frac{|\mathbf{x} - \mathbf{y}|}{c}, \mathbf{y}\right).
```

In the far-field limit $d \gg L$, we can approximate 
$$
|\mathbf{x} - \mathbf{y}| &\approx d - \mathbf{n} \cdot \mathbf{y}
$$

:::{prf:proof} Expansion of $|\mathbf{x} - \mathbf{y}|$
:class: dropdown

$$|\mathbf{x} - \mathbf{y}| &= \sqrt{\mathbb{x}^2 - 2 \mathbf{x} \cdot \mathbf{y} + \mathbf{y}^2} \\
&= d \sqrt{1 - 2 \dfrac{\mathbf{x} \cdot \mathbf{y}}{d^2} + \underbrace{\dfrac{\mathbf{y}}{d^2}}_0} \\
&\approx d \left(1 - 2 \dfrac{\mathbf{x} \cdot \mathbf{y}}{d^2} \right)^{1/2} \\
&\approx d - \mathbf{n} \cdot \mathbf{y}$$
:::
giving:

```{math}
\bar h_{ij}(t, \mathbf{x}) \approx \frac{4G}{c^4 d} \int d^3 y \, T_{ij}\left(t - \frac{r}{c} + \frac{\mathbf{n} \cdot \mathbf{y}}{c}, \mathbf{y}\right).
```

Expanding in powers of $\mathbf{n} \cdot \mathbf{y}/c$ (the slow-motion approximation) and using the conservation equations $\partial_\mu T^{\mu\nu}=0$, one can show that the leading contribution comes from the second moment (quadrupole) of the energy distribution. The result is the **quadrupole formula**:

:::{important} Quadrupole formula
```{math}
h^{TT}_{ij}(t, \mathbf{x}) = \frac{2G}{c^4 d} \Lambda_{ij}^{\,\,\, kl}(\mathbf{n}) \, \ddot{I}_{kl}\left(t - \frac{r}{c}\right),
```

where $I_{kl}$ is the quadrupole moment tensor of the source:

```{math}
I_{kl}(t) = \int d^3 y \, \rho(t, \mathbf{y}) T_{00}\left( t - \dfrac{d}{c}, \mathbf{y} \right) y_k y_l,
```

This formula describes the generation of gravitational waves by time-varying mass quadrupoles.
:::

:::{prf:proof} Quadrupole formula 
:class: dropdown
- Expansion of $T_{ij}$
   $$
   T_{ij} \left( t - \dfrac{|\mathbf{x} - \mathbf{y}|}{c}, \mathbf{y} \right) &= T_{ij} \left( t - \dfrac{d}{c}, \mathbf{y} \right) + \dfrac{\mathbf{y} \cdot \mathbf{n}}{c} \partial_t T_{ij} \left( t - \dfrac{d}{c}, \mathbf{y} \right) + \dotsb
   $$
- **Characteristic time scale** of the source
$$
\partial_t T_{ij} \sim \dfrac{T_{ij}}{t_c}
$$
- **Characteristic velocity**
$$
v_c = \dfrac{L}{t_c}
$$
- Approximation of $T_{ij}$, with $|\mathbf{y}| = L$
$$
T_{ij} + \dfrac{L}{c} \dfrac{T_{ij}}{t_c} + \dotsb = T_{ij}\left(1 + \dfrac{v_c}{c} + \dotsb \right)
$$
- Impose the non-relativistic (slow moving) source $v_c \ll c$
$$
h^{TT}_{ij}(t, \mathbf{x}) &= \Lambda_{ij}^{kl} \dfrac{4 G}{c^4 d} \int d^3 \mathbf{y} T_{kl} \left(t - \dfrac{d}{c}, \mathbf{y} \right)
$$
- We define
$$
I_{ij}(t) = \int d^3 \mathbf{y} \, T^{00}(t, \mathbf{y}) \, y_i \, y_j
$$
and
$$
S_{ij} = \int d^3 \mathbf{y} T_{ij}(t, \mathbf{y})
$$
- From equation of motion $\partial_\mu T^{\mu \nu}$, we have
$$
\begin{cases}
    \partial_0 T^{00} + \partial_k T^{k0} &= 0 \\
    \partial_0 T^{0j} + \partial_k T^{kj} &= 0 
\end{cases} \Rightarrow
\begin{cases}
    \partial_0 T^{00} &= - \partial_k T^{k0}  \\
    \partial_0 T^{0j} &= - \partial_k T^{kj} 
\end{cases}
$$
- We have
$$
\dot I_{ij} &= \int d^3 \mathbf{y} \partial_0 T^{00} \, y_i \, y_j \\
&= - \int d^3 \mathbf{y} \partial_k T^{k0} \, y_i \, y_j
$$
Integration by part
$$
\dot I_{ij} &= \int d^3 \mathbf{y} T^{k0} [(\partial_k y_i) y_j + y_i (\partial_k y_j)] \\
&= \int d^3 \mathbf{y} T^{k0} [\delta_{ki} y_j + y_i \delta_{kj}] \\
&= \int d^3 \mathbf{y} [T_i^0 y_j + T_j^0 y_i]
$$
- Second derivative
$$
\ddot{I_{ij}} &= \int d^3 \mathbf{y} [(\partial_0 T^{i0}) y_j + (\partial_0 T^{j0})y_i] \\
&= - \int d^3 \mathbf{y} (\partial_k T^{ki} y_j + \partial_k T^{kj} y_i) \\
&= 2 S_{ij} \quad (\text{Integral by part again!})
$$
:::

## 5. Application to a binary system in circular Kepler orbit

We now apply the linearized theory to the most important source of gravitational waves for ground‑based detectors: a compact binary system (two black holes or neutron stars) in a circular orbit.

### 5.1 Setup and definitions

Consider two point masses $m_1$ and $m_2$ in a circular Keplerian orbit.  
Define the centre‑of‑mass frame with total mass $M = m_1 + m_2$ and reduced mass $\mu = \dfrac{m_1 m_2}{M}$.  
The relative separation vector is  

$$
\mathbf{r} = \mathbf{y}_1 - \mathbf{y}_2,
$$

and the individual positions are  

$$
\mathbf{y}_1 = \frac{m_2}{M}\mathbf{r},\qquad \mathbf{y}_2 = -\frac{m_1}{M}\mathbf{r}.
$$

For a circular orbit of radius $r$ (constant) in the $x$–$y$ plane,  

$$
\mathbf{r}(t) = r\bigl(\cos(\Omega t),\; \sin(\Omega t),\; 0\bigr),
$$

with orbital angular frequency $\Omega = \sqrt{GM/r^{3}}$ (Kepler's law).

### 5.2 Quadrupole moment and its second time derivative

The (mass) quadrupole moment is defined by  

$$
I_{ij}(t) = \int d^3y\; T_{00}(t,\mathbf{y})\, y_i y_j,
$$

where for point masses $T_{00} = \rho$ (in units with $c=1$). Using the centre‑of‑mass relations,

$$
I_{ij} = m_1 y_{1i} y_{1j} + m_2 y_{2i} y_{2j}
      = \mu \, r_i r_j.
$$

Thus  

$$
I_{ij}(t) = \mu\, r^2 \begin{pmatrix}
\cos^2\Omega t & \cos\Omega t\sin\Omega t & 0\\
\cos\Omega t\sin\Omega t & \sin^2\Omega t & 0\\
0 & 0 & 0
\end{pmatrix}.
$$

```{important} Second time derivative of the quadrupole moment
:label: quad-second-derivative
For a circular binary in the $x$–$y$ plane, the second time derivative of the quadrupole moment is

$$
\ddot I_{ij}(t) = -2\mu r^2 \Omega^2
\begin{pmatrix}
\cos(2\Omega t) & \sin(2\Omega t) & 0\\
\sin(2\Omega t) & -\cos(2\Omega t) & 0\\
0 & 0 & 0
\end{pmatrix}.
$$

Notice the appearance of $2\Omega$: gravitational waves are emitted at **twice the orbital frequency**.
```

```{prf:proof} Derivation of $\ddot I_{ij}$
:class: dropdown
Starting from $I_{ij} = \mu r_i r_j$ with $\mathbf{r} = r(\cos\Omega t,\sin\Omega t,0)$:

$$
\begin{aligned}
\dot I_{ij} &= \mu(\dot r_i r_j + r_i \dot r_j),\\
\ddot I_{ij} &= \mu(\ddot r_i r_j + r_i \ddot r_j + 2\dot r_i \dot r_j).
\end{aligned}
$$

For circular motion,
$$
\mathbf{r} = r(\cos\theta,\sin\theta,0),\quad
\dot{\mathbf{r}} = r\Omega(-\sin\theta,\cos\theta,0),\quad
\ddot{\mathbf{r}} = -r\Omega^2(\cos\theta,\sin\theta,0),
$$
with $\theta = \Omega t$. Substituting:

- For $i=j=x$: $\ddot I_{xx} = \mu[(-r\Omega^2\cos\theta)(r\cos\theta) + (r\cos\theta)(-r\Omega^2\cos\theta) + 2(r\Omega(-\sin\theta))(r\Omega(-\sin\theta))]$
  $$
  = \mu r^2[-\Omega^2\cos^2\theta -\Omega^2\cos^2\theta + 2\Omega^2\sin^2\theta] = -2\mu r^2\Omega^2(\cos^2\theta - \sin^2\theta) = -2\mu r^2\Omega^2\cos2\theta.
  $$

- For $i=j=y$: similarly $\ddot I_{yy} = -2\mu r^2\Omega^2(\sin^2\theta - \cos^2\theta) = +2\mu r^2\Omega^2\cos2\theta$.

- For $i=x,j=y$: $\ddot I_{xy} = \mu[(-r\Omega^2\cos\theta)(r\sin\theta) + (r\cos\theta)(-r\Omega^2\sin\theta) + 2(r\Omega(-\sin\theta))(r\Omega\cos\theta)]$
  $$
  = \mu r^2[-\Omega^2\cos\theta\sin\theta -\Omega^2\cos\theta\sin\theta - 2\Omega^2\sin\theta\cos\theta] = -4\mu r^2\Omega^2\cos\theta\sin\theta = -2\mu r^2\Omega^2\sin2\theta.
  $$

The remaining components vanish. This yields the matrix above.
```

```{note}
The quadrupole formula (derived in the previous section) gives the transverse‑traceless wave amplitude at a distance $d$ in the direction $\mathbf{n}$ as  

$$
h^{TT}_{ij}(t,\mathbf{x}) = \frac{2G}{c^4 d}\,\Lambda_{ij}^{\,\,\,kl}(\mathbf{n})\, \ddot I_{kl}\!\left(t - \frac{d}{c}\right).
$$

For a binary observed face‑on (i.e. along the orbital axis), the projection is trivial and the two independent polarisations are simply proportional to the components of $\ddot I_{ij}$.
```

### 5.3 Wave amplitude and the chirp mass

The non‑zero components of $\ddot I_{ij}$ oscillate with amplitude $2\mu r^2 \Omega^2$. For a face‑on binary, the wave amplitude (the magnitude of $h_{ij}$) is therefore

$$
h_0 = \frac{2G}{c^4 d}\, (2\mu r^2 \Omega^2).
$$

We now eliminate $r$ using Kepler's law $\Omega^2 = GM/r^3$. Solving for $r$:

$$
r = \left(\frac{GM}{\Omega^2}\right)^{1/3}.
$$

Substituting into the amplitude:

$$
h_0 = \frac{4G\mu}{c^4 d} \left(\frac{GM}{\Omega^2}\right)^{2/3} \Omega^2
    = \frac{4G\mu}{c^4 d} (GM)^{2/3} \Omega^{2 - 4/3}
    = \frac{4G\mu}{c^4 d} (GM)^{2/3} \Omega^{2/3}.
$$

It is convenient to introduce the **chirp mass**, which combines the two masses in a way that simplifies the expression:

$$
\mathcal{M} = \frac{(m_1 m_2)^{3/5}}{(m_1+m_2)^{1/5}} = \mu^{3/5} M^{2/5}.
$$

From this definition, we have $\mu = \mathcal{M}^{5/3} M^{-2/3}$. Substituting into $h_0$:

$$
h_0 = \frac{4G}{c^4 d} \mathcal{M}^{5/3} M^{-2/3} (GM)^{2/3} \Omega^{2/3}
    = \frac{4G}{c^4 d} \mathcal{M}^{5/3} G^{2/3} \Omega^{2/3}.
$$

Finally, note that the gravitational wave frequency $f$ is twice the orbital frequency: $f = \Omega/\pi$. Replacing $\Omega = \pi f$ gives the standard form:

```{important}
:label: gw-amplitude-binary
The amplitude of gravitational waves from a circular binary, observed at a distance $d$ with frequency $f$, is  

$$
\boxed{ h_0 = \frac{4(G\mathcal{M})^{5/3}}{c^4 d} (\pi f)^{2/3} }.
$$

Here $G\mathcal{M}$ has dimensions of (mass)×(length³/time²), so the combination $(G\mathcal{M})^{5/3}$ has the correct dimensions for an amplitude.
```

```{note} Key features of the inspiral gravitational-wave signal:
- The strain amplitude scales as  
  $$
  h \propto \frac{1}{d},
  $$
  so the signal becomes weaker with increasing **distance** to the source.

- The amplitude also increases with frequency as  
  $$
  h \propto f^{2/3},
  $$
  meaning the wave grows stronger as the binary tightens.

- During an inspiral, gravitational-wave emission removes energy, causing the orbit to shrink.  
  ⇒ Both the **frequency** and the **amplitude** increase with time, producing the characteristic **“chirp”** signal.

- The evolution of this chirp is governed by a single combination of masses, the **chirp mass**
  $$
  \mathcal{M},
  $$
  which controls:
  - how fast the frequency rises,
  - how the amplitude evolves.

**Therefore, $\mathcal{M}$ is the primary parameter directly measured from the waveform.**
```

## 6. Energy carried by gravitational waves

Gravitational waves transport energy and cause the orbit of a binary system to shrink.  However, because of the equivalence principle, one cannot define a local stress‑energy tensor for gravity, at any point one can choose a locally inertial frame where the gravitational field (and hence its energy) vanishes.  Nevertheless, a meaningful *averaged* energy‑momentum pseudotensor can be constructed, provided the average is taken over several wavelengths of the radiation.

### 6.1 The stress‑energy pseudotensor

For a weak gravitational wave $h_{\mu\nu}$ propagating on a flat background, the effective stress‑energy tensor of the waves (in the transverse‑traceless gauge) is given by the **Landau–Lifshitz** or **Isaacson** averaged expression:

```{math}
:label: gw_pseudotensor
t_{\mu\nu} = \frac{c^4}{32\pi G}\, \big\langle \partial_\mu h_{\alpha\beta}\,\partial_\nu h^{\alpha\beta} \big\rangle,
```

where $\langle \cdots \rangle$ denotes an average over a region large compared to the wavelength but small compared to the curvature scale.  For a plane wave propagating in the $z$ direction, this yields an energy flux (the $t^{0z}$ component) proportional to the square of the time derivatives of the wave amplitudes.

```{note}
- The pseudotensor is gauge‑dependent, but its average over several wavelengths is gauge‑invariant and physically meaningful.
- The factor $c^4/(32\pi G)$ ensures that the energy lost by the source matches the energy carried to infinity.
- For a monochromatic wave, one finds that the energy flux $F = c\,t^{00}$ equals $\frac{c^3}{32\pi G}\omega^2 (h_+^2 + h_\times^2)$, where $h_+,\;h_\times$ are the two polarisation amplitudes.
```

### 6.2 Energy loss from a binary system

The quadrupole formula derived earlier gives the wave amplitude $h^{TT}_{ij}$.  From it one can compute the total power (luminosity) carried away by gravitational waves.  For a general source, the power is

```{math}
P_{\mathrm{GW}} = \frac{G}{5c^5} \big\langle \ddot  I_{ij} \ddot I^{ij} \big\rangle,
```

where $I_{ij}$ is the traceless quadrupole moment.  For a binary in a circular orbit, using the expression for $\ddot I_{ij}$ and noting that $\ddot I_{ij}$ oscillates with frequency $2\Omega$, one obtains after averaging over an orbit:

```{important} Gravitational wave luminosity of a circular binary
:label: gw_power_binary
The gravitational wave luminosity of a circular binary is

$$
P_{\mathrm{GW}} = \frac{32}{5}\frac{G^4}{c^5} \frac{\mu^2 M^3}{r^5}
                = \frac{32}{5}\frac{c^5}{G} \left(\frac{G\mathcal{M}\Omega}{c^3}\right)^{10/3}.
$$

Here $\mathcal{M} = \mu^{3/5} M^{2/5}$ is the chirp mass, and $\Omega = \sqrt{GM/r^3}$ is the orbital angular frequency.
```

```{prf:proof} Derivation of the power
:class: dropdown
Starting from $\ddot I_{ij}$ (Eq. {eq}`quad-second-derivative`), the traceless quadrupole is $I_{ij} = I_{ij} - \frac{1}{3}\delta_{ij} I^k_{\;k}$.  For a binary in the $x$-$y$ plane, $I^k_{\;k} = \mu r^2$, so

$$
I_{ij} = \mu r^2 \begin{pmatrix}
\cos^2\Omega t - \frac13 & \cos\Omega t\sin\Omega t & 0\\
\cos\Omega t\sin\Omega t & \sin^2\Omega t - \frac13 & 0\\
0 & 0 & -\frac13
\end{pmatrix}.
$$

Differentiating three times and averaging over an orbit (using $\langle \cos^2 2\Omega t\rangle = \langle \sin^2 2\Omega t\rangle = \frac12$ and $\langle \cos 2\Omega t\sin 2\Omega t\rangle = 0$) yields

$$
\big\langle \ddot I_{ij} \ddot I^{ij} \big\rangle = \frac{32}{5} \mu^2 r^4 \Omega^6.
$$

Inserting $r^3 = GM/\Omega^2$ and $\mu = \mathcal{M}^{5/3} M^{-2/3}$ gives the second form in terms of $\mathcal{M}$ and $\Omega$.
```

### 6.3 Orbital decay and the chirp formula

The total energy of the binary (in the Newtonian approximation) is

$$
E = -\frac{G\mu M}{2r}.
$$

As the system loses energy to gravitational waves, $r$ decreases and the orbital frequency increases.  Equating the energy loss rate to the GW luminosity:

$$
-\frac{dE}{dt} = P_{\mathrm{GW}}.
$$

Using $dE/dr = + \frac{G\mu M}{2r^2}$ (since $E$ is negative, its magnitude increases as $r$ decreases), we obtain

$$
\frac{dr}{dt} = -\frac{64}{5}\frac{G^3\mu M^2}{c^5 r^3}.
$$

Now relate the gravitational wave frequency $f = \Omega/\pi$ to $r$ via Kepler's law: $f = \frac{1}{\pi}\sqrt{\frac{GM}{r^3}}$.  Differentiating with respect to time gives

$$
\frac{df}{dt} = \frac{3}{2\pi}\sqrt{GM}\, r^{-5/2} \left(-\frac{dr}{dt}\right).
$$

Substituting $dr/dt$ and expressing everything in terms of $f$ and the chirp mass $\mathcal{M}$ leads to the celebrated **chirp formula**:

```{important} Rate of change of the gravitational wave frequency
:label: chirp_formula
The rate of change of the gravitational wave frequency for a circular binary is

$$
\boxed{ \frac{df}{dt} = \frac{96}{5} \pi^{8/3} \left(\frac{G\mathcal{M}}{c^3}\right)^{5/3} f^{11/3} }.
$$

This equation shows that the frequency increases (“chirps”) on a time scale $\tau = f/\dot f \propto f^{-8/3} \mathcal{M}^{-5/3}$.  Measuring both $f$ and $\dot f$ from the observed waveform allows a direct determination of the chirp mass $\mathcal{M}$.
```

```{prf:proof} Derivation of the chirp formula
:class: dropdown
Start from Kepler’s law: $\Omega^2 = \frac{GM}{r^3}$ with $\Omega = \pi f$.  Hence

$$
r = \left(\frac{GM}{(\pi f)^2}\right)^{1/3}.
$$

The binary energy is $E = -\frac{G\mu M}{2r} = -\frac{G\mu M}{2} \left(\frac{(\pi f)^2}{GM}\right)^{1/3}$.  Differentiate with respect to time:

$$
\frac{dE}{dt} = -\frac{G\mu M}{2} \cdot \frac{1}{3} \left(\frac{(\pi f)^2}{GM}\right)^{-2/3} \cdot 2\pi^2 f \frac{df}{dt} \cdot \frac{1}{GM}
            = -\frac{\pi^2}{3} \mu \left(\frac{GM}{(\pi f)^2}\right)^{2/3} f \frac{df}{dt}.
$$

Now use the relation between $\mu$, $M$ and the chirp mass: $\mu = \mathcal{M}^{5/3} M^{-2/3}$.  Also note that $(GM/(\pi f)^2)^{2/3} = (GM)^{2/3} (\pi f)^{-4/3}$.  Hence

$$
\frac{dE}{dt} = -\frac{\pi^2}{3} \mathcal{M}^{5/3} M^{-2/3} (GM)^{2/3} (\pi f)^{-4/3} f \frac{df}{dt}
             = -\frac{\pi^{2-4/3}}{3} \mathcal{M}^{5/3} G^{2/3} f^{1-4/3} \frac{df}{dt}
             = -\frac{1}{3} \pi^{2/3} (G\mathcal{M})^{5/3} f^{-1/3} \frac{df}{dt}.
$$

Set this equal to the GW luminosity from Eq. {eq}`gw_power_binary`:

$$
P_{\mathrm{GW}} = \frac{32}{5} \frac{c^5}{G} \left(\frac{G\mathcal{M}\Omega}{c^3}\right)^{10/3}
                = \frac{32}{5} \frac{c^5}{G} (G\mathcal{M})^{10/3} (\pi f)^{10/3} c^{-10}
                = \frac{32}{5} (G\mathcal{M})^{10/3} (\pi f)^{10/3} \frac{1}{G c^5}.
$$

Equating $-dE/dt = P_{\mathrm{GW}}$ (the minus sign because $E$ is negative and becomes more negative) gives

$$
\frac{1}{3} \pi^{2/3} (G\mathcal{M})^{5/3} f^{-1/3} \frac{df}{dt}
    = \frac{32}{5} (G\mathcal{M})^{10/3} (\pi f)^{10/3} \frac{1}{G c^5}.
$$

Cancel a factor $(G\mathcal{M})^{5/3}$ and solve for $df/dt$:

$$
\frac{df}{dt} = 3 \cdot \frac{32}{5} (G\mathcal{M})^{5/3} \pi^{10/3 - 2/3} f^{10/3 + 1/3} \frac{1}{G c^5}
              = \frac{96}{5} \pi^{8/3} \left(\frac{G\mathcal{M}}{c^3}\right)^{5/3} f^{11/3}.
$$

All factors of $G$ and $c$ now appear in the combination $G\mathcal{M}/c^3$, which has dimensions of time (mass in geometric units).
```

```{note}
- The chirp formula is the basis for matched‑filtering searches in gravitational wave data analysis.  By fitting the observed $f(t)$ to this differential equation, one extracts $\mathcal{M}$ and, with additional information (e.g. from higher harmonics), the individual masses.
- The derivation assumes the orbit remains circular and that the radiation reaction is slow (adiabatic approximation), which is excellent during the inspiral phase.
```
