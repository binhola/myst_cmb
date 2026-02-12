# Introduction

## Goal of this lecture

Describe the inhomogeneous universe
- Perturbation in the metric $\sim 10^{-5}$
- Anisotropies in photon distribution
- Inhomogeneities in matter distribution (linear regime)

## Some basis notions
### Lights and horizons
- The size of a causal patch of space determined how far light can travel in a certain amount of time.
- In an expanding spacetime, the propagation of light is studied in conformal time, in the radial direction ($\theta = \phi = 0$)
$$
ds^2 = a^2(\tau) [d\tau^2 - d\chi^2]
$$
where $d\chi = \dfrac{dr}{\sqrt{1 - kr^2}}$ with $\begin{cases} k = 1 \quad \text{spherical} \\ k = 0 \quad \text{flat} \\ k = 1 \quad \text{hyperbolic} \end{cases}$.

Photon follows null geodesics $ds^2 = 0$, light rays correspond to straight lines at $45\degree$ angles in $\chi-\tau$ coordinates.
```{figure} ../images/astrocosmo/horizon_baumann.png
---
width: 80%
name: horizon
---
```
- **Particle horizon**: the maximal comoving distance that light can travel since the Big Bang ($\tau_i \equiv 0$)
$$
\chi_{ph}(\tau) = \tau - \tau_i = \int_{t_i}^t \dfrac{dt}{a(t)}
$$
This is *(comoving) particle horizon*.

- **Event horizon**: the maximal comoving distance that light can travel to the future ($\tau_f$)
$$
\chi_{eh}(\tau) = \tau_f - \tau = \int_{t}^{t_f} \dfrac{dt}{a(t)}
$$
This is *(comoving) event horizon*. This can be finite even if the physical time is infinite ($\tau_f = \infty$)

### Hubble radius
We can rewrite the *particle horizon* as
$$
\chi_{ph}(\tau) = \int_{t_i}^t \dfrac{dt}{a(t)} = \int_{a_i}^a \dfrac{da}{a \dot a} = \int_{\ln a_i}^{\ln a} (aH)^{-1} d \ln a
$$

The causal structure of spacetime is related to the *comoving Hubble radius*
$$
\boxed{(aH)^{-1}
}
$$

```{note} Hubble radius
For a universe dominated by a fluid with constant equation of state $\omega = P/\rho$
$$
(aH)^{-1} = H_0^{-1} a^{1/2 (1+3\omega)} \quad, \quad \chi_{ph}(t) = \dfrac{2}{1+3\omega} (aH)^{-1}
$$
So for normal matters (e.g. baryons, CDM, radiation) with $\omega > 0$:
- Hubble radius increases as the universe expands. 
- Particle horizon is similar to Hubble radius $\chi_{ph} \sim (aH)^{-1}$ in standard cosmology.
```

```{important} Horizon problem
In standard cosmology, the Hubble radius grows as the Universe expands.
Looking backward in time, the particle horizon becomes very small, meaning that widely separated regions of the early Universe were never in causal contact.
However, observations of the Cosmic Microwave Background show that the temperature is homogeneous across the sky at the level
$$
\frac{\delta T}{T} \sim 10^{-5},
$$
which appears inconsistent with this lack of causal connection.
```

### Solution to Horizon Problem
There must be an early phase where the **comoving Hubble radius decreases**.
This phase is called **inflation**.
If inflation lasts long enough, regions that we see today were once in causal contact.

$$
\frac{d}{dt}(aH)^{-1} < 0 .
$$

During this time, the Universe expands with acceleration ((\ddot a>0)).
Physical distances grow very fast, faster than the Hubble scale, so a small connected region is stretched to very large scales.
```{figure} ../images/astrocosmo/decreasing_hubble_sphere.png
---
width: 80%
---
```
##### Consequence
* We get **more conformal time** between the Big Bang and photon decoupling.
* We need an exotic component with equation of state
  $
  w=\frac{p}{\rho}<-\frac{1}{3}.
  $
* In conformal time, the Big Bang is pushed to very early time
  $
  \tau_i \to -\infty,
  $
  so past light-cones can overlap.

## The inhomogeneous universe
### Stage 1: Perturbation in the metric
$$
g_{\mu \nu} = \underbrace{\bar g_{\mu \nu}}_{\text{FLRW metric}} + \underbrace{\delta g_{\mu \nu}}_{\text{perturbation}}
$$

The perturbed metric can then be written as
$$
ds^2 = a^2(\tau) \left[ (1+2A) d\tau^2 - 2 B_i dx^i d\tau - (\delta_{ij} + h_{ij}) dx^i dx^j \right]
$$
where $A$, $B_i$ and $h_{ij}$ are functions of space and time.

#### Scalar, Vectors and Tensors
* SVT decomposition separates perturbations into **scalar, vector, and tensor** parts.
  At linear order they are independent, so we can study each one separately.

```{important} 

- In practice we care mostly about **scalar** and **tensor** modes.
- **Vector modes** are not produced in standard inflation and quickly decay as the Universe expands.
  They would create a preferred direction, which contradicts the observed homogeneity and isotropy of the early Universe.
```

```{note} Vector: Helmholtz Hodge Decomposition theorem
:class: dropdown

For any vector field $\mathbf{B}$ in $\mathbb{R}^3$:

$$
\mathbf{B} = \nabla B + \mathbf{\tilde{B}}
$$

where:
- $\nabla B$ is the **gradient** (curl-free, "longitudinal")
- $\mathbf{\tilde{B}}$ is **divergence-free** ($\nabla \cdot \mathbf{\tilde{B}} = 0$, "transverse")

> - In Fourier space: $B_i(\mathbf{k}) = i k_i B(\mathbf{k}) + \tilde{B}_i(\mathbf{k})$
> - $i k_i B(\mathbf{k})$ points along $\mathbf{k}$ (scalar mode)
> - $\tilde{B}_i(\mathbf{k})$ has $\mathbf{k} \cdot \mathbf{\tilde{B}}(\mathbf{k}) = 0$ (vector mode)
```



```{note} **Tensor Decomposition**
:class: dropdown

> For a symmetric tensor $h_{ij}$: "What are its irreducible components?"

1. **The Trace**
$$
h^a_a = 3C \quad \Rightarrow \quad C = \frac{1}{3}h^a_a
$$
This is a **scalar**, the simplest piece.

2. **Remove the Trace**
Define the traceless part:
$$
S_{ij} = h_{ij} - C\delta_{ij}
$$
Now $S^a_a = 0$, so we have 5 independent components.

3. **Decompose $S_{ij}$ Further**
> *"What's the most general traceless symmetric tensor I can build from derivatives of scalar/vector functions?"*

Consider all possible derivatives:

* **From a scalar $E$**:
   $$
   \partial_i\partial_j E \quad \text{but this has trace!}
   $$
   $\nabla^2 E = \partial^a\partial_a E$ appears in the trace. So make it **traceless**:
   $$
   \partial_i\partial_j E - \frac{1}{3}\delta_{ij}\nabla^2 E
   $$
   This is pure scalar origin but traceless.

* **From a vector $F_i$**:
   The symmetric derivative $\partial_{(i}F_{j)} = \frac{1}{2}(\partial_i F_j + \partial_j F_i)$
   
   This also has a trace $\partial^a F_a$ is in the trace.
   
   So we must impose $\partial^a F_a = 0$ (divergence-free) to keep it traceless.
* **Tensor $\tilde{h}_{ij}$**:
    What remains is $\tilde{h}_{ij}$, automatically traceless and transverse
```

- Vector decomposition
$$
B_i = \underbrace{\partial_i B}_{\text{scalar}} + \underbrace{\hat{B_i}}_{\text{vector}}
$$
with $\partial^i \hat{B_i} = 0$.
- Rank-2 tensor decomposition
$$
h_{ij} = 2C \delta_{ij} + 2 \partial_{\langle i} \partial_{j \rangle} E + 2 \partial_{( i} \hat{E}_{j )} + 2 \hat{E}_{ij}
$$
where
$$
\partial_{\langle i} \partial_{j\rangle} E & \equiv\left(\partial_i \partial_j-\frac{1}{3} \delta_{i j} \nabla^2\right) E \\
\partial_{(i} \hat{E}_{j)} & \equiv \frac{1}{2}\left(\partial_i \hat{E}_j+\partial_j \hat{E}_i\right)
$$
with $\partial^i \hat{E_i} = 0$, $\partial^i \hat{E_{ij}} = 0$ (divergenceless) and $\hat{E^i_i} = 0$ (traceless).

The 10 degrees of freedom of the metric is decomposed into
$$
&\text{scalars}: A, B, C, E &\to \quad &\text{4 dof} \\
&\text{vectors}: \hat{B_i}, \hat{E_i} &\to \quad &\text{2 dof} \\
&\text{tensors}: \hat{E_{ij}} &\to \quad &\text{2 dof}
$$

#### Gauge fixing
```{important} Gauge problem
:class: dropdown

Metric perturbations are **not uniquely defined** because they depend on the choice of coordinates (the gauge).

* We choose how to slice spacetime into constant-time hypersurfaces.
* We choose spatial coordinates on each slice.
* A bad gauge choice can create **fictitious perturbations** or hide real ones.

$\Rightarrow$ We need a physical description of perturbations that does not depend on coordinates.
So we define **gauge-invariant perturbations**, which remain unchanged under a change of coordinates.
```

```{hint} Gauge-invariant perturbations: Bardeen variables
:class: dropdown
$$
\Psi & \equiv A+\mathcal{H}\left(B-E^{\prime}\right)+\left(B-E^{\prime}\right)^{\prime}, \quad \hat{\Phi}_i \equiv \hat{E}_i^{\prime}-\hat{B}_i, \quad \hat{E}_{i j}, \\
\Phi & \equiv-C-\mathcal{H}\left(B-E^{\prime}\right)+\frac{1}{3} \nabla^2 E .
$$
```
To solve the gauge problem, we *fix the gauge* and keep track of all perturbations (metric and matter).
##### Newton Gauge
Choose
$$
B &= 0 \quad \text{\small constant-time hypersurfaces orthogonal to worldlines of observers at rest} \\
E &= 0 \quad \text{\small induced geometry of the constant-time is isotropic}
$$

The metric
$$
ds^2 = a^2(\tau) [(1 + 2\psi) d\eta^2 - (1-2\phi) \delta_{ij} dx^i dx^j]
$$
We just renamed the remaining two metric perturbations,
$$
A &\equiv \psi \\
C &\equiv -\phi
$$

```{note}
For perturbations decay at spatial infinity, 
- Newton gauge is unique
- Physics is simple
- In absence of anisotropic stress
$$
\psi = \phi
$$
```

### Stage 2: Perturbation Einstein equations

#### Adiabatic fluctuations
Single–field inflation predicts **adiabatic initial fluctuations**.

This means all perturbations come from the **same local shift in time** of the background Universe.
At each point $(\tau, \mathbf{x})$, the perturbed Universe looks like the unperturbed one evaluated at a slightly different time $\tau + \delta \tau(\mathbf{x})$.

The local density of species $I$ is
$$
\delta \rho_I(\tau, \mathbf{x}) \equiv \bar{\rho}_I(\tau + \delta \tau(\mathbf{x})) - \bar{\rho}_I(\tau) ,.
$$

For small $\delta \tau$, this becomes
$$
\delta \rho_I = \bar{\rho}_I' , \delta \tau(\mathbf{x}) ,.
$$

The key point is that the **same $\delta \tau$ applies to all species**:
$$
\delta \tau = \frac{\delta \rho_I}{\bar{\rho}_I'} = \frac{\delta \rho_J}{\bar{\rho}_J'} \quad \text{for all } I,J 
$$

This means all components fluctuate together, with **no relative perturbation between species**, which defines an **adiabatic mode**.

Using $$\bar{\rho_I}' \propto (1 + \omega_I) \rho_I$$ and define $$\delta_I \equiv \dfrac{\delta \rho_I}{\bar{\rho_I}}$$
We have
$$
\dfrac{\delta_I}{1 + \omega_I} = \dfrac{\delta_J}{1 + \omega_J}
$$
For matter and radiation components
$$
\delta_r = \dfrac{4}{3} \delta_m
$$
Total density perturbation is dominated by background species since $\delta_I$ are comparable.
$$
\rm \delta \rho_{tot} = \bar{\rho}_{tot} \delta_{tot} = \sum_I \bar{\rho_{I}} \delta_I
$$

#### Brief on Evolution of fluctuations
Evolution can be related to whether the particles are causally connected to each other.

```{note} Hubble horizon crossing
A standard way to measure whether two particles are **causally connected** to each other at a given moment is comparing the *comoving separation* $\lambda$ with *comoving Hubble radius* $(aH)^{-1}$
$$&\lambda \gg (aH)^{-1} \quad \to \quad &\text{\textbf{not} causally connected} \quad \to \quad &\text{superhorizon} \\
&\lambda \ll (aH)^{-1} \quad \to \quad &\text{causally connected} \quad \to \quad &\text{subhorizon}$$

Also, by defining the *comoving wave number* (scale)
$$
\lambda = \dfrac{2\pi}{k} \sim \dfrac{1}{k}
$$
We can compare $k$ with $aH$
$$&k \ll (aH) \quad \to \quad &\text{\textbf{not} causally connected} \quad \to \quad &\text{superhorizon} \\
&k \gg (aH) \quad \to \quad &\text{causally connected} \quad \to \quad &\text{subhorizon}$$
```

<!-- Define $$\mathcal{H} = aH$$
Closed form evolution equation in Newton gauge with the gravitational potential $\phi$ reads
$$
\boxed{
    \phi "  + 3(1 + \omega) \mathcal{H} \phi' + \omega k^2 \phi = 0
}
$$ -->
1. **During inflation:** Superhorizon modes
- Adiabatic 
- Nearly gaussian
- scale-invariant fourier spectrum

For primordial fluctuation
- No vector modes produced
- Tensor modes produced by primordial gravitational waves.
$\Rightarrow$ leave B-modes in CMB.

2. **During radiation-dominated era**
- Superhorizon modes $\to$ initial conditions
- Subhorizon modes
$$
\delta_m \propto 
\begin{cases}
    \ln a \quad &k\eta \ll 1 \\
    1 \quad &k\eta \gg 1
\end{cases}
$$
- Evolution of $\delta_r \to $ Boltzmann equations

3. **During matter-dominated era**
- Superhorizon modes $\to$ remain constant but amplitude suppressed.
- Subhorizon modes
$$
\delta_m \propto a \to \text{growing modes}
$$

```{figure} ../images/astrocosmo/grav_potential_evolution.png
---
width: 70%

---
```

```{figure} ../images/astrocosmo/matter_density_constrast_evolution.png
---
width: 70%

---
```

