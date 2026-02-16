---
title: Static and spherical spacetime (part 1)
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
date: 2026-02-15
---

# Symmetries of spacetime

Solutions of Einstein equations are very difficult to find because they are non-linear PDEs.  
Therefore, we enforce symmetries (related to physical coordinates) to simplify the problem!  
We look for integrability conditions.

How to define symmetries in a theory where coordinates have no physical meaning?

In classical physics, a quantity $F$ which is invariant does not depend on some coordinate. Assume that $F(t, x, y, z)$:
- $F$ is static: $\partial_t F = 0$,
- $F$ is spherically symmetric: $\partial_\theta F = \partial_\phi F = 0$.

How to make these properties coordinate-independent?

## Lie derivative

### Variation of a vector

Let $v = v^\mu \partial_\mu$ be a vector field.  
Let $C(\lambda)$ be a curve parameterized by $\lambda \in \mathbb{R}$ such that $u^\mu = \dfrac{dx^\mu}{d\lambda}$ is tangent to $C(\lambda)$.

#### Variation of $v$ along a curve
$$
\begin{aligned}
\delta v &= v(Q) - v(P) \\
&= \bigl(v^\mu \partial_\mu\bigr)(Q) - \bigl(v^\mu \partial_\mu\bigr)(P) \\
&= v^\mu(Q)\,\partial_\mu(Q) - v^\mu(P)\,\partial_\mu(P),
\end{aligned}
$$
with  
- $\partial_\mu(P)$ or $\partial_\mu(Q)$ a basis of the tangent space at $P$ and $Q$,  
- $P(x^\mu)$,  
- $Q(x'^\mu = x^\mu + \delta\lambda\, u^\mu)$.

$$
\partial_\mu(Q) = \frac{\partial}{\partial x'^\mu}
= \frac{\partial x^\nu}{\partial x'^\mu}\frac{\partial}{\partial x^\nu}
= \bigl(\delta^\nu_\mu - \delta\lambda\,\partial_\mu u^\nu\bigr)\frac{\partial}{\partial x^\nu}
= \frac{\partial}{\partial x^\mu} - \delta\lambda\,(\partial_\mu u^\nu)\frac{\partial}{\partial x^\nu}.
$$

#### Variation of the components
$$
\begin{aligned}
v^\mu(Q) &= v^\mu(x^\nu + \delta\lambda\, u^\nu) \\
&= v^\mu(x^\nu) + \delta\lambda\, u^\nu \partial_\nu v^\mu \\
&= v^\mu(P) + \delta\lambda\, u^\nu \partial_\nu v^\mu.
\end{aligned}
$$

#### Variation of $v$
$$
\begin{aligned}
\delta v &= \bigl[v^\mu(P) + \delta\lambda\, u^\nu \partial_\nu v^\mu\bigr]
           \bigl[\partial_\mu(P) - \delta\lambda\,(\partial_\mu u^\nu)\partial_\nu(P)\bigr] \\
&= \delta\lambda\Bigl[-v^\mu(P)(\partial_\mu u^\nu)\partial_\nu(P) + u^\nu \partial_\nu v^\mu \partial_\mu(P)\Bigr] + \mathcal{O}(\delta\lambda^2),
\end{aligned}
$$
so
$$
\delta v = \delta\lambda\,\bigl[u^\nu \partial_\nu v^\mu - v^\nu \partial_\nu u^\mu\bigr] \partial_\mu(P).
$$

```{important} Definition of Lie derivative
The Lie derivative of $v$ along $u$ is
$$
\mathcal{L}_u v = \lim_{\delta\lambda\to 0} \frac{\delta v}{\delta\lambda}
= \bigl(u^\nu \partial_\nu v^\mu - v^\nu \partial_\nu u^\mu\bigr)\partial_\mu.
$$
```

### Covariant version
```{important}
The Lie derivative is a tensor:
$$
\mathcal{L}_u v^\mu = u^\nu \nabla_\nu v^\mu - v^\nu \nabla_\nu u^\mu.
$$
```
**Proof:**  
We have $\nabla_\nu v^\mu = \partial_\nu v^\mu + \Gamma^\mu_{\nu\rho} v^\rho$.  
The Lie derivative is given by $\mathcal{L}_u v^\mu = u^\nu \partial_\nu v^\mu - v^\nu \partial_\nu u^\mu$.  
Hence
$$
\mathcal{L}_u v^\mu = u^\nu \nabla_\nu v^\mu - v^\nu \nabla_\nu u^\mu + C^\mu,
$$
where $C^\mu = \underbrace{\Gamma^\mu_{\nu\rho}}_{\text{symmetric}}\;
\underbrace{(v^\nu u^\rho - v^\rho u^\nu)}_{\text{antisymmetric}} = 0$.

```{important} Invariance of a vector
$v$ is invariant along $u$ if and only if
$$
\mathcal{L}_u v = 0.
$$
```

### Generalization to tensors

We proceed the same way:

- For a 1‑form $T = T_\mu dx^\mu$:
  $$
  \mathcal{L}_u T_\mu = u^\nu \nabla_\nu T_\mu + T_\nu \nabla^\nu u_\mu.
  $$

- For a rank‑2 tensor $T = T_{\alpha\beta}\, dx^\alpha \otimes dx^\beta$:
  
$$
  \mathcal{L}_u T_{\alpha\beta} = u^\nu \nabla_\nu T_{\alpha\beta}
  + (\nabla_\alpha u^\mu) T_{\mu\beta}
  + (\nabla_\beta u^\mu) T_{\alpha\mu}.
$$

## Killing vector fields

We are interested in symmetries of spacetime – symmetries of the metric.

### Definition
$k = k^\mu \partial_\mu$ is a Killing vector field of the metric $g_{\alpha\beta}$ iff
$$
\mathcal{L}_k g_{\alpha\beta} = 0.
$$
Equivalently,

$$
\begin{aligned}
\mathcal{L}_k g_{\alpha\beta} &= 0 \\
\Leftrightarrow\quad k^\mu \underbrace{\nabla_\mu g_{\alpha\beta}}_{=0}
+ (\nabla_\alpha k^\mu) g_{\mu\beta} + (\nabla_\beta k^\mu) g_{\alpha\mu} &= 0.
\end{aligned}
$$

Now $(\nabla_\alpha k^\mu) g_{\mu\beta} = \nabla_\alpha (k^\mu g_{\mu\beta}) = \nabla_\alpha k_\beta$, so
$$
\mathcal{L}_k g_{\alpha\beta} = \nabla_\alpha k_\beta + \nabla_\beta k_\alpha = 0.
$$

Physically: "$g_{\mu\nu}$ is invariant under translations in the $k$ direction".

### Examples

Consider a 2‑dimensional flat metric
$$
ds^2 = dx^2 + dy^2 = g_{\mu\nu} dx^\mu dx^\nu
\quad\Rightarrow\quad g_{\mu\nu} = \begin{pmatrix}1&0\\0&1\end{pmatrix}.
$$
This metric admits two Killing vectors:
- It does not depend on $x$: $k^{(1)} = \partial_x$  $\Leftrightarrow$ $k^{(1)x}=1,\; k^{(1)y}=0$.
  Check: $\nabla_\alpha k_\beta^{(1)}+\nabla_\beta k_\alpha^{(1)} = \partial_\alpha k_\beta^{(1)}+\partial_\beta k_\alpha^{(1)} = 0$.
- It does not depend on $y$: $k^{(2)} = \partial_y$.

In polar coordinates $(r,\theta)$:
$$
ds^2 = dr^2 + r^2 d\theta^2
\quad\Rightarrow\quad g_{\mu\nu} = \begin{pmatrix}1&0\\0&r^2\end{pmatrix}.
$$
Now there is one Killing vector because the metric does not depend on $\theta$:
$$
k^{(2)} = \partial_\theta = x\partial_y - y\partial_x.
$$

Check in Cartesian coordinates:
$$
k^{(3)}_x = -y,\qquad k^{(3)}_y = x.
$$
Then
$$
\nabla_\alpha k_\beta^{(3)} - \nabla_\beta k_\alpha^{(3)} = \partial_\alpha k_\beta^{(3)} - \partial_\beta k_\alpha^{(3)}.
$$
Evaluating:
- $(\alpha,\beta)=(x,x)$: $\partial_x k_x^{(3)} + \partial_x k_x^{(3)} = 0$,
- $(\alpha,\beta)=(y,y)$: $\partial_y k_y^{(3)} + \partial_y k_y^{(3)} = 0$,
- $(\alpha,\beta)=(x,y)$: $\partial_x(x) + \partial_y(-y) = 1-1 = 0$.

### Killing vectors and geodesics

Killing vectors imply conserved quantities along geodesics (motion of a free particle).

Let $k$ be a Killing vector: $\nabla_\alpha k_\beta + \nabla_\beta k_\alpha = 0$,  
and $u^\mu$ be tangent to a geodesic: $u^\nu \nabla_\nu u^\mu = 0$.

Then $C = k^\mu u_\mu$ is conserved along the geodesic.

**Proof:** The variation of $C$ along $u^\mu$ is
$$
\begin{aligned}
u^\mu \nabla_\mu C &= u^\mu \nabla_\mu (k^\nu u_\nu) \\
&= u^\mu\bigl[(\nabla_\mu k_\nu) u^\nu + k_\nu (\nabla_\mu u^\nu)\bigr] \\
&= (\nabla_\mu k_\nu) u^\mu u^\nu + k_\nu \underbrace{u^\mu \nabla_\mu u^\nu}_{=0} \\
&= \frac12 (\underbrace{\nabla_\mu k_\nu + \nabla_\nu k_\mu}_{=0}) u^\mu u^\nu = 0.
\end{aligned}
$$

## Stationary spacetime

Stationary spacetimes are expected to describe astrophysical objects at equilibrium (stars, black holes, ECOs).

### Definition
- A spacetime is **stationary** if it admits a timelike Killing vector $k$ (i.e. $k^2 = k_\mu k^\mu < 0$).  
  We choose a coordinate system such that $k = \partial_t$:
  $$
  ds^2 = g_{00}(x^a)\, dt^2 + g_{0i}(x^a)\, dt\, dx^i + g_{ij}(x^a)\, dx^i dx^j,
  $$
  where $g_{\mu\nu}$ does not depend on $t$.

### Static spacetime
A spacetime is **static** if, in addition, it satisfies the discrete symmetry
$$
t \mapsto -t,\qquad g_{\mu\nu} \to g_{\mu\nu}.
$$
This implies $g_{0i}=0$, so
$$
ds^2 = g_{00}(x^a)\, dt^2 + g_{ij}(x^a)\, dx^i dx^j.
$$
**Remark:** Such a metric cannot describe rotating astrophysical objects.

### Spherical symmetry
A static and spherically symmetric spacetime is associated to a point $O$ in spacetime (the centre of a compact object). In spherical coordinates,
$$
\begin{aligned}
ds^2 &= -A(r)\, dt^2 + B(r)\, dr^2 + r^2 d\Omega^2, \\
d\Omega^2 &= d\theta^2 + \sin^2\theta\, d\varphi^2.
\end{aligned}
$$
It has two Killing vectors:
- $\partial_t = k^{(1)}$ (stationarity),
- $\partial_\varphi = k^{(2)}$ (spherical symmetry).

#### Geodesic motion
A particle follows a geodesic $x^\mu(\lambda) = \bigl(t(\lambda), r(\lambda), \theta(\lambda), \varphi(\lambda)\bigr)$ with tangent
$$
u^\mu = (\dot{t}, \dot{r}, \dot{\theta}, \dot{\varphi}), \qquad \dot{} = \frac{d}{d\lambda}.
$$
Two conserved quantities exist:
- Energy:
  $$
  E = -k_\mu^{(1)} u^\mu = -k^{(1)t} u_t = -1 \cdot g_{tt} u^t = A(r)\,\dot{t}.
  $$
- Angular momentum:
  $$
  L = k_\mu^{(2)} u^\mu = k_\varphi^{(2)} u^\varphi = k^{(2)\varphi} g_{\varphi\varphi} u^\varphi = 1 \cdot r^2\sin^2\theta \,\dot{\varphi}.
  $$