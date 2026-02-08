# Non-Euclidean Geometry and General Relativity

## Part I: Manifolds and Coordinate Systems

### 1.1 Curved Spacetime as a Manifold
In General Relativity, spacetime is modeled as a **manifold** $\mathcal{M}$.

**Key Properties:**
- $\mathcal{M}$ is **not** a vector space  
- There is **no global Cartesian coordinate system** covering the entire manifold

**Important Insight:** At each point $p \in \mathcal{M}$, we can define a **tangent space** $T_p\mathcal{M}$ that *is* a vector space.

---

### 1.2 General Coordinate Systems
The manifold $\mathcal{M}$ is covered by arbitrary coordinates:
$$
x^\mu = (x^0, x^1, x^2, x^3)
\tag{1.1}
$$

**Crucial Note:** These coordinates have **no intrinsic physical meaning**; only tensorial quantities constructed from them are physically meaningful.

---

## Part II: Tangent and Cotangent Spaces

### 2.1 Tangent Space $T_p\mathcal{M}$
At each point $p \in \mathcal{M}$, the **tangent space** $T_p\mathcal{M}$ is defined as:

- A vector space with dimension equal to $\dim(\mathcal{M})$
- Spanned by the coordinate derivatives

**Natural Basis:**
$$
e_\mu \equiv \frac{\partial}{\partial x^\mu} \equiv \partial_\mu
\tag{2.1}
$$

**Vector Expansion:**
Any vector $v \in T_p\mathcal{M}$ can be expanded as:
$$
v = v^\mu e_\mu = v^\mu \partial_\mu
\tag{2.2}
$$

The components $v^\mu$ are called **contravariant components**.

---

### 2.2 Coordinate Transformations for Vectors
Consider a coordinate transformation:
$$
x^\mu \to x'^\mu(x)
\tag{2.3}
$$

**Basis Transformation:**
$$
\partial_\mu = \frac{\partial x'^\nu}{\partial x^\mu} \partial'_\nu
\tag{2.4}
$$

**Component Transformation** (to keep $v$ invariant):
$$
v'^\mu = \frac{\partial x'^\mu}{\partial x^\nu} v^\nu
\tag{2.5}
$$

---

### 2.3 Cotangent Space $T_p^*\mathcal{M}$
The **cotangent space** $T_p^*\mathcal{M}$ is the dual space of the tangent space.

**Basis One-Forms:** $dx^\mu$

**Duality Pairing:**
$$
dx^\mu(\partial_\nu) = \delta^\mu_\nu
\tag{2.6}
$$

**Covector Expansion:**
Any covector (1-form) $\lambda \in T_p^*\mathcal{M}$ can be written as:
$$
\lambda = \lambda_\mu dx^\mu
\tag{2.7}
$$

The components $\lambda_\mu$ are called **covariant components**.

---

### 2.4 Transformation of Covectors
Since the scalar product $\lambda(v)$ must be invariant:
$$
\lambda'_\mu = \frac{\partial x^\nu}{\partial x'^\mu} \lambda_\nu
\tag{2.8}
$$

Note the inverse Jacobian, opposite to vector transformation.

---

## Part III: Tensors and the Metric

### 3.1 General Tensors
A tensor of type $(p,q)$ has components:
$$
T^{\mu_1 \dots \mu_p}{}_{\nu_1 \dots \nu_q}
\tag{3.1}
$$

**Examples:**
- Scalar: type $(0,0)$
- Vector: type $(1,0)$
- Covector: type $(0,1)$
- Metric: type $(0,2)$

**Transformation Rule:**

$$
T'^{\mu_1 \dots \mu_p}{}_{\nu_1 \dots \nu_q}
=
\frac{\partial x'^{\mu_1}}{\partial x^{\alpha_1}}
\dots
\frac{\partial x'^{\mu_p}}{\partial x^{\alpha_p}}
\frac{\partial x^{\beta_1}}{\partial x'^{\nu_1}}
\dots
\frac{\partial x^{\beta_q}}{\partial x'^{\nu_q}}
T^{\alpha_1 \dots \alpha_p}{}_{\beta_1 \dots \beta_q}
\tag{3.2}
$$

---

### 3.2 Tensor Contraction
**Partial Contraction** (yields new tensor):
$$
U^\mu{}_\rho = T^{\mu\nu} S_{\nu\rho}
\tag{3.3}
$$

**Full Contraction** (yields scalar):
$$
\phi = T^{\mu\nu} S_{\mu\nu}
\tag{3.4}
$$

---

### 3.3 Metric Tensor and Distances
The **metric tensor** $g_{\mu\nu}$ is a symmetric $(0,2)$ tensor:
$$
g = g_{\mu\nu} dx^\mu \otimes dx^\nu
\tag{3.5}
$$

**Spacetime Interval:**
$$
ds^2 = g_{\mu\nu} dx^\mu dx^\nu
\tag{3.6}
$$

---

### 3.4 Raising and Lowering Indices
**Lowering Indices:**
$$
v_\mu = g_{\mu\nu} v^\nu
\tag{3.7}
$$

**Raising Indices:**
$$
v^\mu = g^{\mu\nu} v_\nu
\tag{3.8}
$$

where $g^{\mu\nu}$ is the inverse metric:
$$
g^{\mu\alpha} g_{\alpha\nu} = \delta^\mu_\nu
\tag{3.9}
$$

---

### 3.5 Determinant of the Metric
Under coordinate transformation:

$$
g'_{\mu\nu}
=
\frac{\partial x^\alpha}{\partial x'^\mu}
\frac{\partial x^\beta}{\partial x'^\nu}
g_{\alpha\beta}
\tag{3.10}
$$

**Determinant Transformation:**
$$
\det g' = (\det J)^{-2} \det g
\tag{3.11}
$$

where $J$ is the Jacobian matrix $\partial x'^\mu/\partial x^\nu$.

**Important:** $\det g$ is **not a scalar**.

---

## Part IV: Covariance and Local Frames

### 4.1 Covariance of Physical Laws
Physical laws must be expressed as **tensor equations** to ensure coordinate independence.

If a tensor equation holds in one coordinate system:
$$
\xi^\rho{}_{\mu\nu} = 0
\tag{4.1}
$$

then in any other coordinates:
$$
\xi'^\rho{}_{\mu\nu} = 0
\tag{4.2}
$$

---

### 4.2 Local Free-Falling Frames (LFFF)
At any point $p \in \mathcal{M}$, we can choose coordinates (Riemann normal coordinates) such that:
$$
g_{\mu\nu}(p) = \eta_{\mu\nu}, \quad
\partial_\alpha g_{\mu\nu}(p) = 0
\tag{4.3}
$$

**Implications:**
- Locally, physics reduces to Special Relativity
- Globally, curvature cannot be removed

---

## Part V: Covariant Derivative

### 5.1 The Problem with Partial Derivatives

**For Scalars** (works fine):

$$
\partial_\mu f \quad \text{is a tensor}
\tag{5.1}
$$

**For Vectors** (problematic):

$$
\partial_\alpha v^\mu \quad \text{is NOT a tensor}
\tag{5.2}
$$

Extra terms appear due to derivatives of the Jacobian.

---

### 5.2 Defining the Covariant Derivative

**For a Vector $v^\mu$:**

$$
\nabla_\alpha v^\mu
=
\partial_\alpha v^\mu
+
\Gamma^\mu_{\alpha\beta} v^\beta
\tag{5.3}
$$

The $\Gamma^\mu_{\alpha\beta}$ are **connection coefficients**.

**For a Covector $\lambda_\mu$:**

$$
\nabla_\alpha \lambda_\mu
=
\partial_\alpha \lambda_\mu
-
\Gamma^\beta_{\alpha\mu} \lambda_\beta
\tag{5.4}
$$

---

### 5.3 Properties of Covariant Derivative

1. **Linearity:**
   For tensors $T$, $S$ and scalars $a$, $b$:
   $$
   \nabla_\mu (a\,T + b\,S) = a\,\nabla_\mu T + b\,\nabla_\mu S
   \tag{5.5}
   $$

2. **Leibniz Rule:**
   For tensors $T$ and $S$:

   $$
   \nabla_\mu (T \otimes S)
   =
   (\nabla_\mu T) \otimes S
   +
   T \otimes (\nabla_\mu S)
   \tag{5.6}
   $$

3. **Action on Scalars:**
   For scalar field $f$:
   $$
   \nabla_\mu f = \partial_\mu f
   \tag{5.7}
   $$

These properties uniquely determine $\nabla$ on all tensors.

---

## Part VI: Levi-Civita Connection

### 6.1 Determining the Connection
The connection is fixed by imposing:

1. **Symmetry (Torsion-Free):**
   $$
   \Gamma^\alpha_{\mu\nu} = \Gamma^\alpha_{\nu\mu}
   \tag{6.1}
   $$

2. **Metric Compatibility:**
   $$
   \nabla_\alpha g_{\mu\nu} = 0
   \tag{6.2}
   $$

---

### 6.2 Christoffel Symbols
These conditions yield the unique **Levi-Civita connection**:

$$
\Gamma^\alpha_{\mu\nu}
=
\frac{1}{2} g^{\alpha\beta}
\left(
\partial_\mu g_{\nu\beta}
+
\partial_\nu g_{\mu\beta}
-
\partial_\beta g_{\mu\nu}
\right)
\tag{6.3}
$$

**Important:** $\Gamma^\alpha_{\mu\nu}$ is **not a tensor**.

---

### 6.3 Useful Identities

**Divergence of a Vector:**

$$
\nabla_\mu v^\mu
=
\frac{1}{\sqrt{-g}}
\partial_\mu\!\left(\sqrt{-g}\, v^\mu\right)
\tag{6.4}
$$

**Scalar Wave Operator (d'Alembertian):**

$$
\square \phi
=
\nabla_\mu \nabla^\mu \phi
=
\frac{1}{\sqrt{-g}}
\partial_\mu\!\left(\sqrt{-g}\, g^{\mu\nu} \partial_\nu \phi\right)
\tag{6.5}
$$

where $g = \det(g_{\mu\nu})$.

---

## Part VII: Particle Motion in Curved Spacetime

### 7.1 Basic Setup
We study a **free particle** as a **test body**:

- The particle does **not** back-react on the geometry
- Spacetime geometry is fixed by $g_{\mu\nu}$

---

### 7.2 Worldline Parameterization
The particle follows a **worldline** $C(\lambda)$:
$$
x^\mu = x^\mu(\lambda), \quad \lambda \in \mathbb{R}
\tag{7.1}
$$

---

### 7.3 Proper Time
For **timelike trajectories**, define **proper time** $\tau$:
$$
d\tau^2 = - ds^2 = - g_{\mu\nu} dx^\mu dx^\nu > 0
\tag{7.2}
$$

For massive particles, we often use:
$$
\lambda = \tau
\tag{7.3}
$$

---

### 7.4 4-Velocity
**Definition:**
$$
U^\mu = \frac{dx^\mu}{d\tau}
\tag{7.4}
$$

**Normalization:**
$$
U^\mu U_\mu = g_{\mu\nu} U^\mu U^\nu = -1
\tag{7.5}
$$

---

### 7.5 Tangent Vector
For general parameter $\lambda$:
$$
t^\mu = \frac{dx^\mu}{d\lambda}
\tag{7.6}
$$

**Relation to 4-velocity:**
$$
t^\mu = \left(\frac{d\tau}{d\lambda}\right) U^\mu
\tag{7.7}
$$

---

## Part VIII: Geodesic Equation

### 8.1 Variation Along Curves

**For a Scalar Field $\phi$:**
$$
\frac{d\phi}{d\lambda} = t^\mu \nabla_\mu \phi
\tag{8.1}
$$

**For General Tensors $T$:**
$$
\frac{dT}{d\lambda} = t^\mu \nabla_\mu T
\tag{8.2}
$$

---

### 8.2 4-Acceleration
**Definition:**
$$
a^\nu = \frac{dU^\nu}{d\lambda} = t^\mu \nabla_\mu U^\nu
\tag{8.3}
$$

For $\lambda = \tau$:
$$
a^\nu = U^\mu \nabla_\mu U^\nu
\tag{8.4}
$$

---

### 8.3 Free Particle Condition
A particle is **free** if:
$$
a^\nu = 0 \quad \Rightarrow \quad U^\mu \nabla_\mu U^\nu = 0
\tag{8.5}
$$

---

### 8.4 Deriving the Geodesic Equation
Using the covariant derivative expression:
$$
\nabla_\mu U^\nu = \partial_\mu U^\nu + \Gamma^\nu_{\mu\alpha} U^\alpha
\tag{8.6}
$$

We obtain:
$$
U^\mu \partial_\mu U^\nu + \Gamma^\nu_{\mu\alpha} U^\mu U^\alpha = 0
\tag{8.7}
$$

Since $U^\mu \partial_\mu = \frac{d}{d\tau}$:
$$
\frac{dU^\nu}{d\tau} + \Gamma^\nu_{\mu\alpha} \frac{dx^\mu}{d\tau} \frac{dx^\alpha}{d\tau} = 0
\tag{8.8}
$$

Finally, with $U^\nu = \frac{dx^\nu}{d\tau}$:

$$
\boxed{
\frac{d^2 x^\nu}{d\tau^2}
+
\Gamma^\nu_{\mu\alpha}
\frac{dx^\mu}{d\tau}
\frac{dx^\alpha}{d\tau}
=
0
}
\tag{8.9}
$$

---

## Part IX: Interpretation and Remarks

### 9.1 Physical Interpretation

**Key Results:**
1. Free particles follow **geodesics** of spacetime
2. Gravity is encoded in the **connection** $\Gamma^\nu_{\mu\alpha}$
3. In local free-falling frames ($\Gamma^\nu_{\mu\alpha}(p) = 0$), motion reduces to Special Relativity

---

### 9.2 Important Remarks

**For Massless Particles:**
- Proper time $\tau$ is not defined
- The geodesic equation still holds using an **affine parameter** $\lambda$

**General Principle:**
The geodesic equation (8.9) represents the generalization of Newton's first law to curved spacetime.