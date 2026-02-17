---
title: Linearized Gravity
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
date: 2026-02-09
---

# Linearized Gravity
*Reference: Bardeen (1980), PRD 22, 1882*

## 1. Perturbation Expansion

In cosmological perturbation theory, we decompose the metric and the stress‑energy tensor into a homogeneous, isotropic background plus small perturbations:

$$
g_{\mu \nu} = \bar{g}_{\mu \nu} + \delta g_{\mu \nu}, \qquad
T_{\mu \nu} = \bar{T}_{\mu \nu} + \delta T_{\mu \nu},
$$

where:
- $\bar{g}_{\mu \nu}$ is the Friedmann–Lemaître–Robertson–Walker (FLRW) metric,
- $\bar{T}_{\mu \nu}$ is the homogeneous stress‑energy tensor of the background cosmic fluid,
- $\delta g_{\mu \nu}$ and $\delta T_{\mu \nu}$ are small inhomogeneous perturbations.

## 2. The Gauge Problem

The split into “background” and “perturbation” is not unique.  
In practice, one defines the background by taking a **spatial average** on each constant‑time hypersurface.  
However, the choice of the time coordinate (the *slicing*) is coordinate‑dependent, so the correspondence between the perturbed quantity $\delta g_{\mu \nu}$ and the background $\bar{g}_{\mu \nu}$ becomes ambiguous.

### 2.1 Infinitesimal Coordinate Transformations

Consider an infinitesimal coordinate change:

$$
x^\mu \;\longrightarrow\; \tilde{x}^\mu = x^\mu + \epsilon^\mu(x),
\qquad |\epsilon^\mu| \ll 1 .
$$

Under such a transformation, the metric perturbation (see the details in [](../00-GR/05-Static%20and%20spherical%20spacetime.md)) changes as

$$
\delta \tilde{g}_{\mu \nu}
= \delta g_{\mu \nu} - \bar{\nabla}_{\!\mu}\epsilon_{\nu}
- \bar{\nabla}_{\!\nu}\epsilon_{\mu},
$$

where $\bar{\nabla}$ is the covariant derivative associated with the background metric $\bar{g}_{\mu \nu}$, and $\epsilon_\mu = \bar{g}_{\mu\nu}\epsilon^\nu$.  
The perturbation $\delta g_{\mu \nu}$ is not **gauge‑invariant**; different choices of $\epsilon^\mu$ (i.e., different time‑slicings) give different values for the perturbation, even though they describe the same physical spacetime.

### 2.2 Gauge Transformations for Scalars, Vectors and Tensors

The same logic applies to any matter or geometric quantity. For a generic tensor field $T$, the change in its perturbation due to an infinitesimal coordinate transformation is given by the Lie derivative of the background quantity:

$$
\delta \tilde{T} = \delta T - \mathcal{L}_\epsilon \bar{T}.
$$

Explicitly, for the cases relevant to cosmology:

```{important} Gauge transformations for perturbations
- **Scalar field** $S = \bar{S} + \delta S$:
  $$
  \delta \tilde{S} = \delta S - \epsilon^\mu \partial_\mu \bar{S}.
  $$

- **Covariant vector field** $V_\mu = \bar{V}_\mu + \delta V_\mu$:
  $$
  \delta \tilde{V}_\mu = \delta V_\mu - \epsilon^\rho \partial_\rho \bar{V}_\mu - \bar{V}_\rho \partial_\mu \epsilon^\rho.
  $$

- **Covariant rank‑2 tensor** $T_{\mu\nu} = \bar{T}_{\mu\nu} + \delta T_{\mu\nu}$:
  $$
  \delta \tilde{T}_{\mu\nu} = \delta T_{\mu\nu} - \epsilon^\rho \partial_\rho \bar{T}_{\mu\nu} - \bar{T}_{\rho\nu} \partial_\mu \epsilon^\rho - \bar{T}_{\mu\rho} \partial_\nu \epsilon^\rho.
  $$

For the metric itself, using $\bar{\nabla}_\mu \bar{g}_{\nu\rho}=0$, this reduces to the familiar form
$$
\delta \tilde{g}_{\mu\nu} = \delta g_{\mu\nu} - \bar{\nabla}_\mu \epsilon_\nu - \bar{\nabla}_\nu \epsilon_\mu.
$$
```

### 2.3 Mathematical Definition of Gauge Transformations

To clarify the concept, let us denote by $U$ the **real perturbed spacetime** and by $\bar{U}$ the **homogeneous background spacetime**.

A **gauge** is a mapping between $U$ and $\bar{U}$. We describe $U$ using coordinates $x^\mu$, i.e. a diffeomorphism
$$
x^\mu : U \longrightarrow \mathbb{R}^4 .
$$

A **change of gauge** corresponds to changing the identification between $\mathbb{R}^4$ and the physical spacetime $U$.

```{hint} Interpretation
:class: dropdown

The perturbation written in the coordinate system $x^\mu$ represents the
perturbation evaluated at the **same coordinate values** $x^\mu$, but
corresponding to a **different physical point** $M \in U$, because the
mapping between $\mathbb{R}^4$ and $U$ has changed.
```

```{important} Pure gauge transformation
A **pure gauge transformation** is defined as:
- a change in the mapping
  $$
  \mathbb{R}^4 \rightarrow U,
  $$
- while keeping the background identification
  $$
  \mathbb{R}^4 \rightarrow \bar{U}
  $$
  fixed.
```

In practice, a pure gauge transformation is simply an infinitesimal coordinate transformation that does not affect the background – it only changes the way we split a given physical spacetime into background plus perturbation. Such transformations are the source of the gauge ambiguity.

### 2.4 Constructing Gauge‑Invariant Variables

To obtain physically meaningful quantities, one must combine components of $\delta g_{\mu \nu}$ (and similarly $\delta T_{\mu \nu}$) into combinations that are unchanged by an infinitesimal coordinate transformation.  
Such combinations are called **gauge‑invariant variables**.  
Bardeen’s formalism (and later extensions) provides a systematic way to construct them.

The following simple 2‑dimensional example illustrates how a coordinate transformation can “absorb” a perturbation, making a perturbed universe appear perfectly homogeneous. It also shows why gauge‑invariant combinations are necessary.

#### A 2D Toy Example

```{exercise} Time‑slicing invariance in 2D
:label: time-slicing
Consider a two‑dimensional spacetime with coordinates $(t,x)$ and metric
$$
ds^2 = -dt^2 + \bigl[1 + h(x)\bigr] dx^2,
$$
where $h(x)$ is a small perturbation.  
Perform the coordinate transformation
$$
\begin{cases}
t' = t + \epsilon \sin x ,\\[4pt]
x' = x ,
\end{cases}
\qquad \epsilon \ll 1 .
$$

**Task**:  
Show that, to first order in $\epsilon$, a suitable choice of $h(x)$ can completely remove the perturbation, so that the metric in the new coordinates takes the homogeneous FLRW form $ds^2 = -dt'^2 + dx'^2$.
```

````{solution} time-slicing
:label: sol-time-slicing
:class: dropdown

First, compute the differentials:
$$
\begin{aligned}
dt &= dt' - \epsilon \cos x' \, dx', \\
dx &= dx'.
\end{aligned}
$$
````

## 3. Metric perturbations
Most general metric perturbations read:
$$
\boxed{
ds^2 = a^2(\tau) \left[ (1+2\phi) d\tau^2 - 2 B_i dx^i d\tau - ((1 - 2\psi)\delta_{ij} + H_{ij}) dx^i dx^j \right]
}
$$

### 3.1 Scalar, Vectors and Tensors
```{important} SVT decomposition
SVT decomposition separates perturbations into **scalar, vector, and tensor** parts.
At linear order they are independent, so we can study each one separately.
```

- In practice we care mostly about **scalar** and **tensor** modes.
- **Vector modes** are not produced in standard inflation and quickly decay as the Universe expands.
  They would create a preferred direction, which contradicts the observed homogeneity and isotropy of the early Universe.

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
\boxed{
B_i = \underbrace{\partial_i b}_{\text{scalar}} + \underbrace{\hat{b_i}}_{\text{vector}}
}
$$
with $\partial^i \hat{B_i} = 0$.
- Rank-2 tensor decomposition
$$
\boxed{
H_{ij} = \underbrace{2 \partial_{\langle i} \partial_{j \rangle} \mu}_{\text{scalar}} + \underbrace{2 \partial_{( i} \hat{A}_{j )}}_{\text{vector}} + \underbrace{2 \hat{H}_{ij}}_{\text{tensor}}
}
$$
where
$$
\partial_{\langle i} \partial_{j\rangle} \mu & \equiv\left(\partial_i \partial_j-\frac{1}{3} \delta_{i j} \nabla^2\right) \mu \\
\partial_{(i} \hat{A}_{j)} & \equiv \frac{1}{2}\left(\partial_i \hat{A}_j+\partial_j \hat{A}_i\right)
$$
with $\partial^i \hat{A_i} = 0$, $\partial^i \hat{H_{ij}} = 0$ (divergenceless) and $\hat{E^i_i} = 0$ (traceless).

The 10 degrees of freedom of the metric is decomposed into
$$
&\text{scalars}: \phi, \psi, b, \mu &\to \quad &\text{4 dof} \\
&\text{vectors}: \hat{b_i}, \hat{A_i} &\to \quad &\text{2 dof} \\
&\text{tensors}: \hat{H_{ij}} &\to \quad &\text{2 dof}
$$

```{hint} Gauge-invariant perturbations: Bardeen variables
:class: dropdown
$$
\Psi & \equiv A+\mathcal{H}\left(B-E^{\prime}\right)+\left(B-E^{\prime}\right)^{\prime}, \quad \hat{\Phi}_i \equiv \hat{E}_i^{\prime}-\hat{B}_i, \quad \hat{E}_{i j}, \\
\Phi & \equiv-C-\mathcal{H}\left(B-E^{\prime}\right)+\frac{1}{3} \nabla^2 E .
$$
```

### 3.2 Scalar gauge-transformation laws
The impact of gauge transformations can be computed from previous formulas for tensors
of Lorentz:
$$
\delta g'_{\mu \nu} = \delta g_{\mu \nu} - \partial_\mu \epsilon^\rho \bar g_{\rho \nu} - \partial_\nu \epsilon^\rho \bar g_{\mu \rho} - \epsilon^\rho \partial_\rho \bar g_{\mu \nu}
$$
Let
$$
x^\mu \to x^\mu + \epsilon^\mu
$$
where
$$
\begin{cases}
\epsilon^0 &= \alpha \\
\epsilon^i &= \partial^i \beta + \hat \beta^i 
\end{cases}
$$
We have
$$
\begin{cases}
\phi' &= \phi - \dot \alpha  - \mathcal{H} \alpha \\
b' &= b + \dot \beta - \alpha \\
\psi' &= \psi + \dfrac{1}{3} \nabla^2 \beta + \mathcal{H} \alpha \\
\mu' &= \mu - \beta
\end{cases}
$$

where $. = \dfrac{\partial}{\partial \eta}$

:::{prf:proof} Scalar transformation laws
:class: dropdown

Given $\bar g_{\mu \nu} = \begin{pmatrix}
  a^2 & 0 \\ 0 & -a^2 \delta_{ij}
\end{pmatrix}$ and $\begin{cases}
\epsilon^0 &= \alpha \\
\epsilon^i &= \partial^i \beta + \epsilon^i_{jk}\partial^j \beta^k
\end{cases}$
- **$00$-component**
$$
\delta g_{00}' &= \delta g_{00} - \epsilon^0 \alpha \bar g_{00} - \partial_0 \epsilon^0 \bar g_{00} - \epsilon^0 \partial_0 \bar g_{00} \\
2a^2 \phi ' &= 2 a^2 \phi - 2 \dot \alpha a^2 - 2 \dfrac{\dot a}{a} a^2 \alpha \\
&\boxed{
\phi' = \phi - \dot \alpha - \mathcal{H} \alpha
}
$$
- **$0i$-component**
$$
\delta g_{0i}' &= \delta g_{0i} - \partial_0 \epsilon^j \bar g_{ji} - \partial_i \epsilon^0 \bar g_{00} \\
a^2 \partial_i b' &= a^2 \partial_i b + \partial_0(\partial^j \beta) a^2 \delta_{ij} - \partial_i \epsilon^0 a^2 \\
\partial_i b' &= \partial_i b + \partial_0 \partial_i \beta - \partial_i \alpha \\
&\boxed{b' = b + \dot \beta - \alpha}
$$
- **$ij$-component (trace part)**
$$
\delta g_{ij}' &= \delta g_{ij} - \partial_i \epsilon^k \bar g_{jk} - \partial_j \epsilon^k \bar g_{ik} - \epsilon^0 \partial_0 \bar g_{ij} \\
a^2[2\psi' - H'_{ij}] &= a^2[2\psi - H_{ij}] + \partial_i \partial^k \beta a^2 \delta_{jk} + \partial_j \partial^k \beta a^2 \delta_{ik} + \alpha 2 \dfrac{\dot a}{a} a^2 \delta_{ij} \\
2 \psi' \delta_{ij} - H'_{ij} &= 2\psi \delta_{ij} - H_{ij} + 2\partial_i \partial_j \beta + 2 \mathcal{H} \alpha \delta_{ij}
$$
Contracting with $\delta^{ij}$ to remove $H_{ij}$ and $H'_{ij}$
$$
&6 \psi' = 6 \psi + 2\nabla^2 \beta + 6 \mathcal{H} \alpha \\
&\boxed{\psi' = \psi + \dfrac{1}{3} \nabla^2 \beta + \mathcal{H} \alpha}
$$
- **$ij$-component (traceless part)**

  From the previous part, we have
$$
2(\psi' - \psi) \delta_{ij} - H'_{ij} &= - H_{ij} + 2 \partial_i \partial_j \beta + 2\mathcal{H} \alpha \delta_{ij} \\
2 \left( \dfrac{1}{3} \nabla^2 \beta + \mathcal{H} \alpha \right) \delta_{ij} - H'_{ij} &= - H_{ij} + 2 \partial_i \partial_j \beta + 2\mathcal{H} \alpha \delta_{ij} \\
H'_{ij} &= H_{ij} - 2\partial_i \partial_j \beta + \dfrac{2}{3} \nabla^2 \beta \delta_{ij} \\
2 \left( \partial_i \partial_j - \dfrac{1}{3} \nabla^2 \right) \mu' &= 2 \left( \partial_i \partial_j - \dfrac{1}{3} \nabla^2 \right) \mu - 2\partial_i \partial_j \beta + \dfrac{2}{3} \nabla^2 \beta \delta_{ij} \\
2 \left( \partial_i \partial_j - \dfrac{1}{3} \nabla^2 \right) \mu' &= 2 \left( \partial_i \partial_j - \dfrac{1}{3} \nabla^2 \right) (\mu - \beta) \\
$$
  So
$$
\boxed{\mu' = \mu - \beta}
$$
:::

### 3.3 Gauge fixing
To solve the gauge problem, we *fix the gauge* and keep track of all perturbations (metric and matter).
### 3.4 Newton Gauge
Choose
$$
\hat b_i &= 0 \quad \text{\small constant-time hypersurfaces orthogonal to worldlines of observers at rest} \\
\mu &= 0 \quad \text{\small induced geometry of the constant-time is isotropic}
$$

The metric
$$
\boxed{
ds^2 = a^2(\eta) [(1 + 2\phi) d\eta^2 - (1-2\psi) \delta_{ij} dx^i dx^j]
}
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

## 4. Linearized Einstein Equation
We will work with Newton gauge.

### Connection Coefficients
The connection coefficients associated with the Newton-gauge metric are
$$
\Gamma^0_{00} &= \mathcal{H} + \dot \phi \\
\Gamma^0_{i0} &= \partial_i \phi \\
\Gamma^i_{00} &= \delta^{ij} \partial_j \phi \\
\Gamma^0_{ij} &= \mathcal{H}\delta_{ij} - [\dot \psi + 2 \mathcal{H}(\psi + \phi)]\delta_{ij} \\
\Gamma^i_{j0} &= [\mathcal{H} - \dot \psi] \delta^i_j \\
\Gamma^i_{jk} &= -2 \delta^i_{(j} \partial_{k)} \psi + \delta_{jk} \delta^{il} \partial_l \psi \\
$$

:::{prf:proof} Connection coefficients
:class: dropdown

The equation for connection coefficients
$$\Gamma^\alpha_{\mu \nu} &= \dfrac{1}{2} g^{\alpha \beta} (\partial_\mu g_{\beta \nu} + \partial_\nu g_{\mu \beta} - \partial_\beta g_{\mu \nu}) 
$$
We will only consider everything to the first order.

$$
\Gamma^0_{00} &= \dfrac{1}{2} g^{00} \partial_0 g_{00} \\
&= \dfrac{1}{2} a^{-2} (1 - 2\phi) 2a^2[ \mathcal{H} (1 + 2\phi) + \dot \phi ] \\
&= \boxed{\mathcal{H} + \dot \phi} \\
\Gamma^0_{i0} &= \dfrac{1}{2} g^{00} \partial_i g_{00} \\
&= \dfrac{1}{2} a^{-2} (1 - 2\phi) 2 a^2 \partial_i \phi \\
&= \boxed{\partial_i \phi} \\
\Gamma^i_{00} &= - \dfrac{1}{2} g^{ij} \partial_j g_{00} \\
&= \dfrac{1}{2} a^{-2} (1 + 2 \psi) \delta^{ij} 2 a^2 \partial_j \phi \\
&= \boxed{\delta^{ij} \partial_j \phi} \\
\Gamma^0_{ij} &= -\dfrac{1}{2} g^{00} \partial_0 g_{ij} \\
&= \dfrac{1}{2} a^{-2} (1 - 2\phi) 2a^2[\mathcal{H}(1-2\psi) - \dot \psi] \delta_{ij} \\
&= \boxed{\mathcal{H}\delta_{ij} - [\dot \psi + 2 \mathcal{H}(\phi + \psi)]\delta_{ij}} \\
\Gamma^i_{j0} &= \dfrac{1}{2} g^{ik} \partial_0 g_{jk} \\
&= \dfrac{1}{2} a^{-2} (1+2\psi) \delta^{ik} 2a^2[\mathcal{H}(1-2\psi) - \dot \psi] \delta_{jk} \\ 
&= \boxed{[\mathcal{H} - \dot \psi] \delta^i_j} \\
\Gamma^i_{jk} &= \dfrac{1}{2} g^{il}[\partial_j g_{lk} + \partial_k g_{jl} - \partial_l g_{jk}] \\
&=  \dfrac{1}{2} a^{-2} (1+2\psi) \delta^{il} 2 a^2[-\partial_j \psi \delta_{lk} - \partial_k \psi \delta_{jl} + \partial_l \psi \delta_{jk}] \\
&= \boxed{-2 \delta^i_{(j} \partial_{k)} \psi + \delta_{jk} \delta^{il} \partial_l \psi}
$$
:::

### Ricci tensor
**Ricci tensor** can be expressed in terms of the connection as
$$
R_{\mu \nu} = \partial_\lambda \Gamma^\lambda_{\mu \nu} - \partial_\nu \Gamma^\lambda_{\mu \lambda} + \Gamma^\lambda_{\lambda \rho} \Gamma^\rho_{\mu \nu} - \Gamma^\rho_{\mu \lambda} \Gamma^\lambda_{\nu \rho}
$$

Substituting the perturbed connection coefficients, we find
$$
R_{00} &= -3 \dot{\mathcal{H}} + \nabla^2 \phi + 3 \mathcal{H}(\dot \phi + \dot \psi) + 3 \ddot{\psi}\\
R_{0i} &= 2 \partial_i(\dot \psi + \mathcal{H} \phi)\\
R_{ij} &= [\mathcal{\dot H} + 2\mathcal{H}^2 - \ddot{\psi} + \nabla^2 \psi - 2(\mathcal{\dot H} + 2\mathcal{H}^2)(\phi + \psi) - \mathcal{H}\dot \phi - 5 \mathcal{H} \dot \psi]\delta_{ij} + \partial_i \partial_j(\psi - \phi)\\
$$

:::{prf:proof} perturbed Ricci tensors
:class: dropdown

$$
R_{00} = \partial_\rho \Gamma^\rho_{00} - \partial_0 \Gamma^\rho_{0\rho} + \Gamma^\alpha_{00} \Gamma^\rho_{\alpha \rho} - \Gamma^\alpha_{0\rho} \Gamma^\rho_{0 \alpha}
$$
The term with $\rho=0$ cancels out, we sum over $\rho = i$ only
$$
R_{00} &= \partial_i \Gamma^i_{00} - \partial_0 \Gamma^\rho_{0i} + \Gamma^\alpha_{00} \Gamma^i_{\alpha i} - \Gamma^\alpha_{0i} \Gamma^i_{0 \alpha} \\
&= \partial_i \Gamma^i_{00} - \partial_0 \Gamma^i_{0i} + \Gamma^0_{00} \Gamma^i_{0 i} + \underbrace{\Gamma^j_{00} \Gamma^i_{ji}}_{\mathcal{O(2)}} - \underbrace{\Gamma^0_{0i} \Gamma^i_{00}}_{\mathcal{O(2)}} - \Gamma^j_{0i} \Gamma^i_{0 j} \\
&= \nabla^2 \phi - 3 \partial_0 (\mathcal{H} - \dot \psi) + 3(\mathcal{H} + \dot \phi)(\mathcal{H} - \dot \psi) - (\mathcal{H} - \dot \psi)^2 \delta^j_i \delta^i_j \\
&= \boxed{-3 \dot{\mathcal{H}} + \nabla^2 \phi + 3 \mathcal{H}(\dot \phi + \dot \psi) + 3 \ddot{\psi}} \\
R_{0i} &= \partial_\rho \Gamma^\rho_{0i} - \partial_i \Gamma^\rho_{0\rho} + \Gamma^\rho_{\rho \alpha} \Gamma^\alpha_{0i} - \Gamma^\rho_{0\alpha} \Gamma^\alpha_{i\rho} \\
&= [\partial_i(\dot \phi - \dot \psi) ]-[ \partial_i \dot \phi - 3 \partial_i \dot \psi ] + [5 \mathcal{H} \partial_i \phi - 3 \mathcal{H} \partial_i \psi] - [3 \mathcal{H} \partial_i(\phi - \psi)] \\
&= \boxed{2 \partial_i (\dot \psi + H \phi)} \\
R_{ij} &= \partial_\rho \Gamma^\rho_{ij} - \partial_j \Gamma^\rho_{i\rho} + \Gamma^\rho_{\rho \alpha} \Gamma^\alpha_{ij} - \Gamma^\rho_{i\alpha} \Gamma^\alpha_{j\rho} \\
&= \bigl[\dot{\mathcal{H}} - \ddot\psi - 2\dot{\mathcal{H}}(\phi+\psi) - 2\mathcal{H}(\dot\phi+\dot\psi) + \nabla^2\psi\bigr]\delta_{ij} - 2\partial_i\partial_j\psi \\ 
& \quad + \partial_i\partial_j\phi - 3\partial_i\partial_j\psi \\
& \quad + 4\mathcal{H}^2\delta_{ij} + \bigl[\mathcal{H}\dot\phi - 7\mathcal{H}\dot\psi - 8\mathcal{H}^2(\phi+\psi)\bigr]\delta_{ij} \\ 
& \quad + 2\mathcal{H}^2\delta_{ij} - 4\mathcal{H}\bigl[\dot\psi + \mathcal{H}(\phi+\psi)\bigr]\delta_{ij} \\
&= \boxed{[\mathcal{\dot H} + 2\mathcal{H}^2 - \ddot{\psi} + \nabla^2 \psi - 2(\mathcal{\dot H} + 2\mathcal{H}^2)(\phi + \psi) - \mathcal{H}\dot \phi - 5 \mathcal{H} \dot \psi]\delta_{ij} + \partial_i \partial_j(\psi - \phi)}
$$
:::

### Ricci scalar
**Ricci scalar** can be computed as
$$
\boxed{
R = \dfrac{1}{a^2} \left[ -6(\mathcal{\dot H} + \mathcal{H}^2) + 2\nabla^2 \phi - 4\nabla^2 \psi + 12(\mathcal{\dot H} + \mathcal{H}^2)\phi + 6 \ddot{\psi} + 6 \mathcal{H}(\dot \phi + 3 \dot \psi) \right]}
$$
:::{prf:proof} Ricci scalar
:class: dropdown

$$
R &= g^{\mu \nu} R_{\mu \nu} \\
&= g^{00} R_{00} + 2 \underbrace{g^{0i} R_{0i}}_{\mathcal{O(2)}} + g^{ij} R_{ij}
$$
We have
$$
a^2R &= (1-2\phi)R_{00} - (1+2\psi)\delta^{ij}R_{ij} \\
&= (1-2\phi)\bigl[-3\dot{\mathcal{H}} + \nabla^2\phi + 3\mathcal{H}(\dot\phi + \dot\psi) + 3\ddot\psi\bigr] \\
& \quad - 3(1+2\psi) \left[\dot{\mathcal{H}} + 2\mathcal{H}^2 - \ddot\psi + \nabla^2\psi - \mathcal{H}\dot\phi - 5\mathcal{H}\dot\psi - 2(\dot{\mathcal{H}}+2\mathcal{H}^2)(\phi+\psi)\right] \\
& \quad - (1 + 2\psi) \nabla^2 (\psi - \phi)
$$
Cancel the non-linear term
$$
a^2 R = -6(\mathcal{\dot H} + \mathcal{H}^2) + 2 \nabla^2 \phi - 4 \nabla^2 \psi + 12(\mathcal{\dot H} + \mathcal{H}^2)\phi + 6 \ddot{\psi} + 6 \mathcal{H} (\dot \phi + 3 \dot \psi) \\
$$
:::

### Equation of motions (DraftXXX)
The equations of motion for the matter perturbations come from conservation of the stress tensor
$$
\boxed{
\nabla^\mu T_{\mu \nu} = 0}
$$
Developing the covariant derivative
$$
\nabla^\mu T_{\mu \nu} = \partial_\mu T^\mu_\nu + \Gamma^\mu_{\mu \alpha} T^{\alpha}_\nu - \Gamma^\alpha_{\mu \nu} T^\mu_\alpha = 0
$$
For $\nu = 0$, we have the equation of density perturbation evolution
$$
\boxed{
\partial_\eta \delta \rho = -3 \mathcal{H} (\delta \rho + \delta P) + 3 \dot \psi (\bar \rho + \bar P) - \partial_i ((\bar \rho + \bar P)v^i)}
$$
For $\nu = i$, we have the equation of momentum perturbation evolution
$$
\boxed{
\partial_\eta ((\bar{\rho} + \bar{P})v^i) = -4 \mathcal{H} (\bar{\rho} + \bar{P})v^i - (\bar \rho + \bar P ) \partial^i \phi - \partial^i \delta P - \partial_j \Pi^{ij}
}
$$
:::{prf:proof} Equation of motion 
:class: dropdown

- Density perturbation evolution
:::
### Einstein tensors
From the equation
$$
G_{\mu \nu} = R_{\mu \nu} - \dfrac{1}{2} R g_{\mu \nu}
$$

This is just a basic substitution problem:
$$
\delta G^0_0 = 2 \nabla^2 \psi - 6 \mathcal{H} (\dot \psi + \mathcal{H}\phi)
$$
### Einstein equation for perturbations (DraftXXX)
:::{important} Einstein equation for perturbation
$$
\delta G^\mu_{\nu} = 8\pi G \delta T^\mu_{\nu}
$$
:::

The 00-component of Einstein equation reads
$$
\boxed{
  \underbrace{\nabla^2 \psi}_{\text{Newtonian}} - \underbrace{3 \mathcal{H} (\dot \psi + \mathcal{H} \phi)}_{\text{GR correction}} = 4 \pi G a^2 \delta \rho 
}
$$
This is **generalized relativistic Poission** equation.

:::{hint} Interpretation
- For subhorizon modes ($k \gg \mathcal{H}$), we have
$$
| \nabla^2 \psi | \gg |3 \mathcal{H} (\dot \psi + \mathcal{H} \phi)| \quad \text{(in Fourier modes } |\nabla^2| \simeq k^2)
$$
So we reduce to *Poisson* equation
$$
\nabla^2 \psi \approx 4 \pi G a^2 \delta \rho 
$$
- The GR correction term is important in superhorizon scales.
:::

The $ij$-component of Einstein equation reads
$$
\boxed{
  \nabla^2 (\psi - \phi) = -8\pi G a^2 (\bar \rho + \bar P) \sigma
}
$$
where $\sigma$ is the anisotropic stress.

:::{hint} Important remarks
- Perfect fluids have zero anisotropic stress.
- Dark matter and baryons can be described as perfect fluids.
- Photons started as a perfect fluid, but developed an anisotropic stress component during the matter-dominated era when their energy density is subdominant.
- The only relevant source for anisotropic stress in the early universe is neutrino (*But the level is small so we will ignore them for this course*).
:::

### Evolution equation for metric potential (XXXDraft)
$$
\boxed{
\ddot \psi + 3\mathcal{H} \dot \psi + (2\mathcal{\dot H} + \mathcal{H}^2) \psi = 4\pi G a^2 \delta P
}
$$

:::{hint} Remarks
- If there is anisotropic stress, there is additional source term because the right hand side is sources by pressure perturbation.
- On subhorizon scales ...
- On superhorizon scales ...
:::