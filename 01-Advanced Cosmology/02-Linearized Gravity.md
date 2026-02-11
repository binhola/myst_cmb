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
g_{\mu \nu} = \bar g_{\mu \nu} + \delta g_{\mu \nu}, \qquad
T_{\mu \nu} = \bar T_{\mu \nu} + \delta T_{\mu \nu}
$$

where:
- $\bar g_{\mu \nu}$ is the Friedmann–Lemaître–Robertson–Walker (FLRW) metric,
- $\bar T_{\mu \nu}$ is the homogeneous stress‑energy tensor of the background cosmic fluid,
- $\delta g_{\mu \nu}$ and $\delta T_{\mu \nu}$ are small inhomogeneous perturbations.

## 2. The Gauge Problem

The split into “background” and “perturbation” is not unique.  
In practice, one defines the background by taking a **spatial average** on each constant‑time hypersurface.  
However, the choice of the time coordinate (the *slicing*) is coordinate‑dependent, so the correspondence between the perturbed quantity $\delta g_{\mu \nu}$ and the background $\bar g_{\mu \nu}$ becomes ambiguous.

### 2.1 Infinitesimal Coordinate Transformations

Consider an infinitesimal coordinate change:

$$
x^\mu \;\longrightarrow\; \tilde{x}^\mu = x^\mu + \epsilon^\mu(x),
\qquad |\epsilon^\mu| \ll 1 .
$$

Under such a transformation, the metric perturbation changes as

$$
\delta g_{\mu \nu} \;\longrightarrow\; \delta \tilde{g}_{\mu \nu}
= \delta g_{\mu \nu} - \bar\nabla_{\!\mu}\epsilon_{\nu}
- \bar\nabla_{\!\nu}\epsilon_{\mu},
$$

where $\bar\nabla$ is the covariant derivative associated with the background metric $\bar g_{\mu \nu}$.  
The perturbation $\delta g_{\mu \nu}$ is not **gauge‑invariant**; different choices of $\epsilon^\mu$ (i.e., different time‑slicings) give different values for the perturbation, even though they describe the same physical spacetime.

### 2.2 Constructing Gauge‑Invariant Variables

To obtain physically meaningful quantities, one must combine components of $\delta g_{\mu \nu}$ (and similarly $\delta T_{\mu \nu}$) into combinations that are unchanged by an infinitesimal coordinate transformation.  
Such combinations are called **gauge‑invariant variables**.  
Bardeen’s formalism (and later extensions) provides a systematic way to construct them.

#### A 2D Toy Example

The following exercise illustrates how a coordinate transformation can “absorb” a perturbation, making a perturbed universe appear perfectly homogeneous.

```{exercise} Time‑slicing invariance in 2D
:label: time-slicing
Consider a two‑dimensional spacetime with coordinates $(t,x)$ and a metric perturbation that depends on $x$.  
Perform the coordinate transformation

$$
\begin{cases}
t' = t + \epsilon \sin x ,\\[4pt]
x' = x ,
\end{cases}
\qquad \epsilon \ll 1 .
$$

**Task**:  
Show that, to first order in $\epsilon$, a suitable perturbation in the original metric can be completely removed by this transformation, so that the metric in the new coordinates takes the homogeneous FLRW form.
```

````{solution} time-slicing
:label: sol-time-slicing

$$
\begin{cases}
dt = dt' - \epsilon \cos x' \, dx' \\
dx = dx'
\end{cases}
$$

````
