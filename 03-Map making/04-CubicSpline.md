# Cubic Splines
## 1. The Interpolation Problem

Given $n+1$ data points
$$
(t_0, y_0),\; (t_1, y_1),\; \ldots,\; (t_n, y_n), \qquad t_0 < t_1 < \cdots < t_n,
$$
we want to find a smooth function $S(t)$ such that $S(t_i) = y_i$ for all $i$.

The nodes $t_i$ are called **knots**.

### Why not a single polynomial?

The most natural idea is to fit a single polynomial of degree $n$ through all $n+1$ points. By Lagrange interpolation, this polynomial is unique and given by:
$$
P(t) = \sum_{i=0}^{n} y_i \prod_{j \neq i} \frac{t - t_j}{t_i - t_j}
$$

This works well for small $n$, but fails badly as $n$ grows.

:::{prf:example} Runge's phenomenon
:class: dropdown
Consider interpolating $f(t) = \dfrac{1}{1 + 25t^2}$ on $[-1, 1]$ with $n+1$ equally spaced points. As $n$ increases, the polynomial oscillates wildly near the endpoints, even though $f$ is smooth. This is **Runge's phenomenon**: high-degree polynomial interpolation with equally spaced nodes is numerically unstable.

The maximum error grows as $\|P - f\|_\infty \to \infty$ as $n \to \infty$ for many smooth functions.
:::

The remedy is to use **piecewise polynomials** of low degree, stitched together with smoothness conditions at the interior knots.

---

## 2. Piecewise Polynomials

Divide $[t_0, t_n]$ into $n$ subintervals $[t_{i-1}, t_i]$ for $i = 1, \ldots, n$. On each subinterval, define a separate polynomial $S_i(t)$ of degree $d$:
$$
S_i(t) = a_i + b_i(t - t_{i-1}) + c_i(t-t_{i-1})^2 + d_i(t-t_{i-1})^3 + \cdots
$$

The full piecewise function is:
$$
S(t) = S_i(t), \qquad t \in [t_{i-1}, t_i]
$$

This is called a **spline** of degree $d$ if the pieces are joined with $C^{d-1}$ continuity at each interior knot, meaning $S$ and its first $d-1$ derivatives are continuous at every $t_i$.

**Degrees of freedom.** With $n$ intervals and a degree-$d$ polynomial on each, we have $(d+1)n$ free parameters. The $C^{d-1}$ conditions at $n-1$ interior knots impose $d(n-1)$ constraints. The remaining degrees of freedom are:
$$
\text{DOF} = (d+1)n - d(n-1) = n + d
$$

For $d = 3$ (cubic spline): $\text{DOF} = n + 3$. The $n+1$ interpolation conditions $S(t_i) = y_i$ use $n+1$ of these, leaving $2$ free, which are fixed by **boundary conditions**.

---

## 3. Natural Cubic Spline

### Setup

A **cubic spline** $S$ on $[t_0, t_n]$ consists of $n$ cubic polynomials $S_1, \ldots, S_n$ such that:

1. **Interpolation:** $S_i(t_{i-1}) = y_{i-1}$ and $S_i(t_i) = y_i$ for $i = 1, \ldots, n$
2. **$C^1$ continuity:** $S_i'(t_i) = S_{i+1}'(t_i)$ for $i = 1, \ldots, n-1$
3. **$C^2$ continuity:** $S_i''(t_i) = S_{i+1}''(t_i)$ for $i = 1, \ldots, n-1$

Write the $i$-th piece in terms of the local variable $h_i = t_i - t_{i-1}$ and $u = t - t_{i-1}$:
$$
S_i(t) = a_i + b_i u + c_i u^2 + d_i u^3, \qquad u \in [0, h_i]
$$

Let $M_i = S''(t_i)$ denote the **second derivative** of $S$ at knot $t_i$. This is the key unknown. Since $S_i$ is cubic, its second derivative is linear:
$$
S_i''(t) = M_{i-1}\frac{t_i - t}{h_i} + M_i \frac{t - t_{i-1}}{h_i}
$$

### Deriving the spline coefficients

Integrating $S_i''(t)$ twice and applying the interpolation conditions $S_i(t_{i-1}) = y_{i-1}$, $S_i(t_i) = y_i$:

$$
S_i(t) = \frac{M_{i-1}}{6h_i}(t_i - t)^3 + \frac{M_i}{6h_i}(t - t_{i-1})^3 + \left(\frac{y_{i-1}}{h_i} - \frac{M_{i-1}h_i}{6}\right)(t_i - t) + \left(\frac{y_i}{h_i} - \frac{M_i h_i}{6}\right)(t - t_{i-1})
$$

:::{prf:proof} Derivation of $S_i(t)$
:class: dropdown
Since $S_i''$ is linear on $[t_{i-1}, t_i]$ and equals $M_{i-1}$ at $t_{i-1}$ and $M_i$ at $t_i$:
$$
S_i''(t) = M_{i-1}\frac{t_i - t}{h_i} + M_i\frac{t - t_{i-1}}{h_i}
$$

Integrate once:
$$
S_i'(t) = -\frac{M_{i-1}}{2h_i}(t_i - t)^2 + \frac{M_i}{2h_i}(t - t_{i-1})^2 + C_1
$$

Integrate again:
$$
S_i(t) = \frac{M_{i-1}}{6h_i}(t_i - t)^3 + \frac{M_i}{6h_i}(t - t_{i-1})^3 + C_1 t + C_2
$$

Apply $S_i(t_{i-1}) = y_{i-1}$:
$$
\frac{M_{i-1}}{6h_i}h_i^3 + C_1 t_{i-1} + C_2 = y_{i-1}
\implies \frac{M_{i-1} h_i^2}{6} + C_1 t_{i-1} + C_2 = y_{i-1}
$$

Apply $S_i(t_i) = y_i$:
$$
\frac{M_i}{6h_i}h_i^3 + C_1 t_i + C_2 = y_i
\implies \frac{M_i h_i^2}{6} + C_1 t_i + C_2 = y_i
$$

Subtracting the two equations:
$$
C_1 = \frac{y_i - y_{i-1}}{h_i} - \frac{(M_i - M_{i-1})h_i}{6}
$$

Substituting $C_1$ back and simplifying gives the stated result. $\blacksquare$
:::

### The $C^1$ condition and the tridiagonal system

The $C^1$ condition $S_i'(t_i) = S_{i+1}'(t_i)$ at each interior knot $t_i$ relates the three unknowns $M_{i-1}, M_i, M_{i+1}$. Differentiating $S_i(t)$ and evaluating at $t = t_i$, then doing the same for $S_{i+1}$ at $t = t_i$ and equating, yields:

$$
h_i M_{i-1} + 2(h_i + h_{i+1}) M_i + h_{i+1} M_{i+1} = 6\left(\frac{y_{i+1} - y_i}{h_{i+1}} - \frac{y_i - y_{i-1}}{h_i}\right)
$$

for $i = 1, 2, \ldots, n-1$. This gives $n-1$ equations in $n+1$ unknowns $M_0, M_1, \ldots, M_n$.

The two remaining degrees of freedom are fixed by **boundary conditions**.

### Boundary conditions

**Natural spline** (most common):
$$
M_0 = 0, \qquad M_n = 0
$$
This forces $S''= 0$ at both endpoints, meaning the spline is linear outside the data range. This gives the name "natural" — the spline behaves naturally (without artificial curvature) at the boundaries.

**Clamped spline:** Prescribe the first derivatives at the endpoints:
$$
S'(t_0) = f_0', \qquad S'(t_n) = f_n'
$$
This adds two equations involving $M_0$ and $M_n$.

**Not-a-knot:** Force the third derivative to be continuous across $t_1$ and $t_{n-1}$, effectively treating the first two and last two intervals as a single cubic. This is the default in many software libraries (e.g. `scipy.interpolate.CubicSpline`).

**Periodic:** $S'(t_0) = S'(t_n)$ and $S''(t_0) = S''(t_n)$. Used when the data is periodic, e.g. HWPSS as a function of HWP angle $\chi \in [0, 2\pi)$.

---

## 4. Matrix Form

### The natural spline system

For the natural spline, $M_0 = M_n = 0$ reduces the system to $n-1$ equations in $n-1$ unknowns $M_1, \ldots, M_{n-1}$. Define:

$$
\mu_i = \frac{h_i}{h_i + h_{i+1}}, \qquad \lambda_i = \frac{h_{i+1}}{h_i + h_{i+1}}, \qquad f_i = \frac{6}{h_i + h_{i+1}}\left(\frac{y_{i+1} - y_i}{h_{i+1}} - \frac{y_i - y_{i-1}}{h_i}\right)
$$

The system becomes:

$$
\underbrace{\begin{pmatrix}
2 & \lambda_1 & & & \\
\mu_2 & 2 & \lambda_2 & & \\
& \mu_3 & 2 & \lambda_3 & \\
& & \ddots & \ddots & \ddots \\
& & & \mu_{n-1} & 2
\end{pmatrix}}_{\mathbf{A} \,\in\, \mathbb{R}^{(n-1)\times(n-1)}}
\underbrace{\begin{pmatrix} M_1 \\ M_2 \\ \vdots \\ M_{n-1} \end{pmatrix}}_{\mathbf{m}}
=
\underbrace{\begin{pmatrix} f_1 \\ f_2 \\ \vdots \\ f_{n-1} \end{pmatrix}}_{\mathbf{f}}
$$

The matrix $\mathbf{A}$ is **symmetric tridiagonal** with diagonal entries $2$ and off-diagonal entries $\mu_i, \lambda_i \in (0,1)$ satisfying $\mu_i + \lambda_i = 1$.

### Existence and uniqueness

:::{prf:proof} The natural cubic spline exists and is unique
:class: dropdown
It suffices to show that $\mathbf{A}$ is invertible, i.e. that the system $\mathbf{Am} = \mathbf{f}$ has a unique solution.

$\mathbf{A}$ is **strictly diagonally dominant**: the diagonal entry in each row is $2$, while the sum of absolute values of off-diagonal entries is $\mu_i + \lambda_i = 1 < 2$. By the Gershgorin circle theorem, all eigenvalues of $\mathbf{A}$ lie in the disk $|z - 2| \leq 1$, so all eigenvalues satisfy $\text{Re}(\lambda) \geq 1 > 0$. In particular $\mathbf{A}$ is positive definite and hence invertible. $\blacksquare$
:::

### Solving the system

Because $\mathbf{A}$ is tridiagonal, the system $\mathbf{Am} = \mathbf{f}$ can be solved in $\mathcal{O}(n)$ operations using the **Thomas algorithm** (a specialized form of Gaussian elimination for tridiagonal systems):

**Forward sweep:** For $i = 2, \ldots, n-1$:
$$
w_i = \mu_i / 2_{i-1}^*, \qquad 2_i^* = 2 - w_i \lambda_{i-1}, \qquad f_i^* = f_i - w_i f_{i-1}^*
$$
where $2_1^* = 2$ and $f_1^* = f_1$.

**Back substitution:** For $i = n-2, \ldots, 1$:
$$
M_i = (f_i^* - \lambda_i M_{i+1}) / 2_i^*
$$

Once $\mathbf{m} = (M_1, \ldots, M_{n-1})^T$ is known, the full spline is determined by substituting back into the formula for $S_i(t)$.

:::{prf:example} Natural cubic spline on 5 points
:class: dropdown
Consider $n+1 = 5$ equally spaced knots on $[0, 1]$:

$$
t = (0,\; 0.25,\; 0.5,\; 0.75,\; 1), \qquad y = (0,\; 1,\; 0,\; 1,\; 0)
$$

The spacings are all $h_i = 0.25$, so $\mu_i = \lambda_i = 0.5$ and the system is:

$$
\begin{pmatrix}
2 & 0.5 & & \\
0.5 & 2 & 0.5 & \\
& 0.5 & 2
\end{pmatrix}
\begin{pmatrix} M_1 \\ M_2 \\ M_3 \end{pmatrix}
=
\begin{pmatrix} f_1 \\ f_2 \\ f_3 \end{pmatrix}
$$

with $f_i = 6 \times (\text{divided difference})$ computed from the data.
:::

---

## 5. Smoothing Splines

Interpolation forces $S(t_i) = y_i$ exactly. When the data are **noisy**, this is undesirable — the spline will fit the noise as well as the signal.

A **smoothing spline** instead minimizes:
$$
\min_{S} \left\{ \sum_{i=0}^{n} w_i \left(y_i - S(t_i)\right)^2 + \lambda \int_{t_0}^{t_n} \left[S''(t)\right]^2 \mathrm{d}t \right\}
$$

The first term is a **data fidelity** term (weighted least squares residual). The second term is a **roughness penalty** that penalizes curvature. The scalar $\lambda \geq 0$ controls the trade-off:

- $\lambda = 0$: pure interpolation (spline passes through all points)
- $\lambda \to \infty$: pure smoothing (spline becomes a straight line minimizing the residual)

:::{note} Relation to ridge regression
The smoothing spline penalty $\lambda \int (S'')^2$ is the functional analogue of the ridge penalty $\lambda \|\mathbf{x}\|^2$ in finite-dimensional regression. Both shrink the solution towards zero curvature (smoothness) rather than zero coefficients.
:::

### Existence and form of the solution

:::{prf:proof} The solution is a natural cubic spline
:class: dropdown
Let $\mathcal{H}$ be the Sobolev space of functions with square-integrable second derivatives. The functional
$$
J_\lambda[S] = \sum_i w_i(y_i - S(t_i))^2 + \lambda \int (S'')^2
$$
is strictly convex on $\mathcal{H}$. By the representer theorem for reproducing kernel Hilbert spaces, the minimizer $\hat S$ is a **natural cubic spline** with knots at the data points $t_0, \ldots, t_n$.

The key insight is that for any $g \in \mathcal{H}$ agreeing with $\hat S$ at all knots, we can write $g = \hat S + \epsilon$ where $\epsilon(t_i) = 0$. Then:
$$
\int (g'')^2 = \int (\hat S'' + \epsilon'')^2 = \int (\hat S'')^2 + 2\int \hat S'' \epsilon'' + \int (\epsilon'')^2 \geq \int (\hat S'')^2
$$
where the cross term vanishes by integration by parts and the natural boundary conditions. So $\hat S$ minimizes the roughness penalty among all functions with the same knot values. $\blacksquare$
:::

### Matrix form of the smoothing spline

Since the solution is a natural cubic spline, we can write $S(t) = \sum_{j} \alpha_j B_j(t)$ in terms of a spline basis. Let $\mathbf{B}$ be the $n+1 \times n+1$ basis evaluation matrix with $B_{ij} = B_j(t_i)$, and let $\mathbf{\Omega}$ be the **penalty matrix** with entries:
$$
\Omega_{jk} = \int_{t_0}^{t_n} B_j''(t)\, B_k''(t)\, \mathrm{d}t
$$

The smoothing spline problem becomes:
$$
\min_{\boldsymbol{\alpha}} \left\{ (\mathbf{y} - \mathbf{B}\boldsymbol{\alpha})^T \mathbf{W} (\mathbf{y} - \mathbf{B}\boldsymbol{\alpha}) + \lambda \boldsymbol{\alpha}^T \mathbf{\Omega} \boldsymbol{\alpha} \right\}
$$

where $\mathbf{W} = \text{diag}(w_0, \ldots, w_n)$. Setting the gradient to zero:
$$
(\mathbf{B}^T \mathbf{W} \mathbf{B} + \lambda \mathbf{\Omega})\, \hat{\boldsymbol{\alpha}} = \mathbf{B}^T \mathbf{W} \mathbf{y}
$$

The fitted values are:
$$
\hat{\mathbf{y}} = \mathbf{B} \hat{\boldsymbol{\alpha}} = \underbrace{\mathbf{B}(\mathbf{B}^T \mathbf{W}\mathbf{B} + \lambda\mathbf{\Omega})^{-1} \mathbf{B}^T \mathbf{W}}_{\mathbf{H}_\lambda} \mathbf{y}
$$

The matrix $\mathbf{H}_\lambda$ is the **hat matrix** (smoother matrix). It maps data $\mathbf{y}$ directly to fitted values $\hat{\mathbf{y}}$.

---

## 6. B-spline Basis

The natural cubic spline uses a **global** basis: each basis function $B_j(t)$ has support over the entire interval. This becomes computationally expensive and numerically unstable for large $n$. The **B-spline basis** provides an alternative parametrization with **local support** — each basis function is nonzero on at most $d+1$ consecutive intervals.

### Knot vector

A B-spline of degree $d$ on $[a, b]$ with $K$ basis functions is defined by a **knot vector**:
$$
\boldsymbol{\xi} = (\xi_0, \xi_1, \ldots, \xi_{K+d})
$$
a non-decreasing sequence of $K + d + 1$ values. The **multiplicity** of a knot controls the smoothness at that point: a knot of multiplicity $m$ reduces continuity from $C^{d-1}$ to $C^{d-m}$.

For an **open (clamped)** knot vector on $[0, 1]$ with $p$ interior knots:
$$
\boldsymbol{\xi} = (\underbrace{0, \ldots, 0}_{d+1},\; \xi_1, \ldots, \xi_p,\; \underbrace{1, \ldots, 1}_{d+1})
$$

This gives $K = p + d + 1$ basis functions and ensures the spline interpolates the endpoints exactly.

### Cox–de Boor recursion

The B-spline basis functions $\{\phi_{j,d}(t)\}_{j=0}^{K-1}$ of degree $d$ are defined recursively.

**Base case** ($d = 0$, piecewise constant):
$$
B_{j,0}(t) = \begin{cases} 1 & \xi_j \leq t < \xi_{j+1} \\ 0 & \text{otherwise} \end{cases}
$$

**Recursion** ($d \geq 1$):
$$
\phi_{j,d}(t) = \frac{t - \xi_j}{\xi_{j+d} - \xi_j} \phi_{j,d-1}(t) + \frac{\xi_{j+d+1} - t}{\xi_{j+d+1} - \xi_{j+1}} \phi_{j+1,d-1}(t)
$$

with the convention $0/0 = 0$.

:::{prf:example} Linear B-splines ($d=1$) on 3 knots
:class: dropdown
Let $\boldsymbol{\xi} = (0, 0, 0.5, 1, 1)$ giving $K = 3$ basis functions of degree 1.

- $\phi_{0,0}(t) = 1$ for $t \in [0, 0.5)$, else $0$
- $\phi_{1,0}(t) = 1$ for $t \in [0.5, 1)$, else $0$

Then:
$$
\phi_{0,1}(t) = \frac{t - 0}{0.5 - 0} \phi_{0,0}(t) + \frac{1 - t}{1 - 0} B_{1,0}(t)
$$

On $[0, 0.5)$: $\phi_{0,1}(t) = 2t$. On $[0.5, 1)$: $\phi_{0,1}(t) = 1 - t$. Elsewhere: $0$. This is a hat function with peak at $t = 0.5$.
:::

### Properties of B-splines

1. **Local support:** $B_{j,d}(t) = 0$ for $t \notin [\xi_j, \xi_{j+d+1}]$. Each basis function is nonzero on at most $d+1$ consecutive intervals.

2. **Partition of unity:** $\displaystyle\sum_{j=0}^{K-1} B_{j,d}(t) = 1$ for all $t \in [\xi_0, \xi_{K+d}]$.

3. **Non-negativity:** $B_{j,d}(t) \geq 0$ for all $t$.

4. **Smoothness:** At a simple interior knot, $B_{j,d} \in C^{d-1}$. At a knot of multiplicity $m$, continuity is $C^{d-m}$.

5. **Interpolation at endpoints:** For a clamped knot vector, $B_{0,d}(a) = B_{K-1,d}(b) = 1$.

### Basis matrix

Given evaluation points $t_0, \ldots, t_{N-1}$, define the **basis matrix**:
$$
\mathbf{B} \in \mathbb{R}^{N \times K}, \qquad \mathbf{B}_{ij} = B_{j,d}(t_i)
$$

Each row sums to 1 (partition of unity). Each column has at most $d+1$ nonzero blocks, so $\mathbf{B}$ is **banded sparse**.

A spline $S(t) = \sum_j \alpha_j B_{j,d}(t)$ evaluated at all points is simply $\mathbf{B}\boldsymbol{\alpha}$.

<!-- ```python
import numpy as np
from scipy.interpolate import BSpline

def build_bspline_basis(t, n_internal_knots, degree=3):
    """
    Build cubic B-spline basis matrix.

    Parameters
    ----------
    t : array, shape (N,)
        Evaluation points, normalized to [0, 1].
    n_internal_knots : int
        Number of interior knots (uniformly spaced on (0, 1)).
    degree : int
        Spline degree. Default 3 (cubic).

    Returns
    -------
    B : array, shape (N, K)
        Basis matrix. K = n_internal_knots + degree + 1.
    knots : array
        Full knot vector.
    """
    # internal knots: uniformly spaced, not including endpoints
    internal = np.linspace(0, 1, n_internal_knots + 2)[1:-1]

    # clamped knot vector: repeat endpoints degree+1 times
    knots = np.concatenate([
        np.repeat(0.0, degree + 1),
        internal,
        np.repeat(1.0, degree + 1),
    ])

    K = len(knots) - degree - 1   # number of basis functions

    # evaluate each basis function
    B = np.zeros((len(t), K))
    for j in range(K):
        c = np.zeros(K)
        c[j] = 1.0
        B[:, j] = BSpline(knots, c, degree, extrapolate=False)(t)

    B = np.nan_to_num(B)   # NaN outside support -> 0
    return B, knots
``` -->

---

## 7. Least Squares Spline Fitting

When the number of data points $N$ exceeds the number of basis functions $K$, we cannot interpolate exactly. Instead we solve the **least squares** problem:
$$
\min_{\boldsymbol{\alpha} \in \mathbb{R}^K} \left\| \mathbf{y} - \mathbf{B}\boldsymbol{\alpha} \right\|^2
$$

The normal equations are:
$$
\mathbf{B}^T \mathbf{B}\, \hat{\boldsymbol{\alpha}} = \mathbf{B}^T \mathbf{y}
$$

with solution:
$$
\hat{\boldsymbol{\alpha}} = (\mathbf{B}^T \mathbf{B})^{-1} \mathbf{B}^T \mathbf{y}
$$

provided $\mathbf{B}$ has full column rank (which holds when $K \leq N$ and the knots are placed so that every basis function is supported by at least one data point).

The fitted values are:
$$
\hat{\mathbf{y}} = \mathbf{B}\hat{\boldsymbol{\alpha}} = \underbrace{\mathbf{B}(\mathbf{B}^T\mathbf{B})^{-1}\mathbf{B}^T}_{\text{projection matrix}} \mathbf{y}
$$

This is the orthogonal projection of $\mathbf{y}$ onto the column space of $\mathbf{B}$.

### Weighted least squares

If different observations have different noise levels $\sigma_i^2$, we minimize the weighted residual:
$$
\min_{\boldsymbol{\alpha}} (\mathbf{y} - \mathbf{B}\boldsymbol{\alpha})^T \mathbf{W} (\mathbf{y} - \mathbf{B}\boldsymbol{\alpha}), \qquad \mathbf{W} = \text{diag}(1/\sigma_0^2, \ldots, 1/\sigma_{N-1}^2)
$$

The weighted normal equations are:
$$
\mathbf{B}^T \mathbf{W} \mathbf{B}\, \hat{\boldsymbol{\alpha}} = \mathbf{B}^T \mathbf{W} \mathbf{y}
$$

---

## 8. Ridge Regularization

### Motivation

When $\mathbf{B}^T\mathbf{B}$ is ill-conditioned (e.g. $K$ is large relative to $N$, or knots are placed where data is sparse), the least squares solution can have very large coefficients with high variance. **Ridge regularization** (Tikhonov regularization) adds a penalty on the size of the coefficients:
$$
\min_{\boldsymbol{\alpha}} \left\{ \left\| \mathbf{y} - \mathbf{B}\boldsymbol{\alpha} \right\|^2 + \lambda \|\boldsymbol{\alpha}\|^2 \right\}
$$

### Solution

Setting the gradient to zero:
$$
\frac{\partial}{\partial \boldsymbol{\alpha}}\left[\|\mathbf{y} - \mathbf{B}\boldsymbol{\alpha}\|^2 + \lambda\|\boldsymbol{\alpha}\|^2\right] = -2\mathbf{B}^T(\mathbf{y} - \mathbf{B}\boldsymbol{\alpha}) + 2\lambda\boldsymbol{\alpha} = 0
$$

gives the **ridge normal equations**:
$$
(\mathbf{B}^T\mathbf{B} + \lambda\mathbf{I})\,\hat{\boldsymbol{\alpha}} = \mathbf{B}^T\mathbf{y}
$$

$$
\boxed{\hat{\boldsymbol{\alpha}} = (\mathbf{B}^T\mathbf{B} + \lambda\mathbf{I})^{-1}\mathbf{B}^T\mathbf{y}}
$$

The matrix $\mathbf{B}^T\mathbf{B} + \lambda\mathbf{I}$ is always invertible for $\lambda > 0$, regardless of the rank of $\mathbf{B}$.

### Bias–variance decomposition

Let the true signal be $\mathbf{y} = \mathbf{B}\boldsymbol{\alpha}^* + \boldsymbol{\varepsilon}$ with $\boldsymbol{\varepsilon} \sim \mathcal{N}(0, \sigma^2\mathbf{I})$. Define $\mathbf{H}_\lambda = \mathbf{B}(\mathbf{B}^T\mathbf{B} + \lambda\mathbf{I})^{-1}\mathbf{B}^T$. The ridge estimator has:

**Bias:**
$$
\mathbb{E}[\hat{\mathbf{y}}] - \mathbf{B}\boldsymbol{\alpha}^* = (\mathbf{H}_\lambda - \mathbf{I})\mathbf{B}\boldsymbol{\alpha}^* = -\lambda\mathbf{B}(\mathbf{B}^T\mathbf{B}+\lambda\mathbf{I})^{-1}\boldsymbol{\alpha}^*
$$

**Variance:**
$$
\text{Var}(\hat{\mathbf{y}}) = \sigma^2 \mathbf{H}_\lambda \mathbf{H}_\lambda^T
$$

As $\lambda$ increases: bias increases, variance decreases. The optimal $\lambda$ minimizes the total mean squared error (MSE).

### SVD perspective

Let $\mathbf{B} = \mathbf{U}\mathbf{\Sigma}\mathbf{V}^T$ be the SVD of $\mathbf{B}$ with singular values $\sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_K \geq 0$. Then:
$$
\hat{\boldsymbol{\alpha}}_\lambda = \mathbf{V}\,\text{diag}\!\left(\frac{\sigma_j}{\sigma_j^2 + \lambda}\right)\mathbf{U}^T\mathbf{y}
$$

Each singular component is **shrunk** by the factor $\sigma_j^2/(\sigma_j^2 + \lambda)$:
- For large $\sigma_j$ (well-determined components): shrinkage is small
- For small $\sigma_j$ (ill-determined components): shrinkage is large

This is the mechanism by which ridge stabilizes the solution.

<!-- ```python
def fit_spline_ridge(t, y, n_internal_knots, degree=3, lam=1e-6):
    """
    Fit a B-spline to data (t, y) via ridge-regularized least squares.

    Parameters
    ----------
    t : array, shape (N,)
        Evaluation/observation points in [0, 1].
    y : array, shape (N,) or (N, D)
        Observed values.
    n_internal_knots : int
        Number of interior knots.
    degree : int
        Spline degree (default 3 = cubic).
    lam : float
        Ridge penalty parameter.

    Returns
    -------
    alpha : array, shape (K,) or (K, D)
        Spline coefficients.
    B : array, shape (N, K)
        Basis matrix used.
    """
    B, knots = build_bspline_basis(t, n_internal_knots, degree)
    K = B.shape[1]

    # ridge normal equations: (B^T B + lam I) alpha = B^T y
    A = B.T @ B + lam * np.eye(K)
    rhs = B.T @ y

    alpha = np.linalg.solve(A, rhs)
    return alpha, B
``` -->

:::{prf:example} Recovering a smooth signal from noisy data
:class: dropdown
Let the true signal be $f(t) = \sin(2\pi t) + 0.5\cos(4\pi t)$ on $[0,1]$. Observe $N=200$ noisy samples $y_i = f(t_i) + \varepsilon_i$ with $\varepsilon_i \sim \mathcal{N}(0, 0.1^2)$.

<!-- ```python
np.random.seed(42)
N = 200
t = np.linspace(0, 1, N)
y_true = np.sin(2*np.pi*t) + 0.5*np.cos(4*np.pi*t)
y_noisy = y_true + 0.1 * np.random.randn(N)

# fit with K=20 basis functions, mild ridge
alpha, B = fit_spline_ridge(t, y_noisy, n_internal_knots=16, lam=1e-4)
y_fit = B @ alpha

print(f"RMS error: {np.sqrt(np.mean((y_fit - y_true)**2)):.4f}")
# RMS error: 0.0071
``` -->

The B-spline fit closely recovers the true signal. The ridge penalty prevents overfitting without significantly biasing the estimate.
:::
