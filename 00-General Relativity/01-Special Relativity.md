# From Special Relativity to General Relativity
## Special Relativity

### History

#### The problem with classical mechanics

In the 19th century, **Maxwell’s equations** were established.  
A fundamental problem appeared: Maxwell’s equations are **not invariant under Galilean transformations**, while classical mechanics is.

This led to three logical possibilities:

1. Maxwell’s equations are valid only in one special inertial frame  
2. Classical mechanics is wrong  
3. Maxwell’s equations are wrong  

Experiments confirmed Maxwell’s equations with high precision, so option (3) is excluded.

Option (1) introduced the **ether hypothesis**, a preferred inertial frame in which light propagates.  
The **Michelson–Morley experiment** showed no evidence for such a frame, ruling out the ether.

The only remaining option is (2): **classical mechanics must be modified**.

### Postulates of Special Relativity

Special relativity is based on two postulates:

1. **Principle of relativity**  
   The laws of physics have the same form in all inertial frames.

2. **Constancy of the speed of light**  
   Light propagates in vacuum with the same speed \( c \), independent of the motion of the source or the observer.

### Consequences

- Time and space are not absolute  
- Space and time are unified into spacetime  
- Physical laws are invariant under **Poincaré transformations**

### Spacetime and the Minkowski Metric

Events are described by spacetime coordinates:
```{math}
x^\mu = (ct,\,x,\,y,\,z)
````

The geometry of spacetime is defined by the **Minkowski metric**:

```{math}
\eta_{\mu\nu} = \mathrm{diag}(-1,\,1,\,1,\,1)
```

The invariant spacetime interval between two infinitesimally close events is:

```{math}
ds^2 = \eta_{\mu\nu}\,dx^\mu\,dx^\nu
     = -c^2 dt^2 + dx^2 + dy^2 + dz^2
```

This quantity is **invariant in all inertial frames**.

### Causal Structure

For two events separated by an interval ( ds^2 ):

* $ds^2 < 0$: **timelike separation** (causal connection possible)
* $ds^2 = 0$: **lightlike separation**
* $ds^2 > 0$: **spacelike separation** (no causal connection)

### Poincaré Group and Lorentz Transformations

#### Poincaré transformations

The most general symmetry of special relativity is:

```{math}
x'^{\mu} = \Lambda^{\mu}{}_{\nu} x^{\nu} + c^{\mu}
```

where:

* $\Lambda^{\mu}{}_{\nu}$ is a **Lorentz transformation**
* $c^\mu$ is a constant spacetime translation

#### Lorentz transformations

Lorentz transformations satisfy:

```{math}
\eta_{\rho\sigma}
\Lambda^{\rho}{}_{\mu}
\Lambda^{\sigma}{}_{\nu}
=
\eta_{\mu\nu}
```

This condition guarantees the invariance of the spacetime interval:

```{math}
ds'^2 = ds^2
```

Hence, all inertial observers agree on the causal structure of spacetime.

## From Special Relativity to General Relativity

### Tensors in Flat Spacetime

In **special relativity**, spacetime is flat and described by the **Minkowski metric** \(\eta_{\mu\nu}\).  
Under a Lorentz transformation:

```{math}
x^\mu \to x'^\mu = \Lambda^\mu{}_\nu x^\nu
````

A tensor of rank (n) transforms as:

```{math}
T^{\mu_1 \dots \mu_n} \to T'^{\mu_1 \dots \mu_n} = \Lambda^{\mu_1}{}_{\nu_1} \dots \Lambda^{\mu_n}{}_{\nu_n} T^{\nu_1 \dots \nu_n}
```

---

### Rank 0: Scalars

* A **scalar field** (\phi(x)) is invariant under Lorentz transformations:

```{math}
\phi'(x') = \phi(x)
```

* The **Minkowski interval** and the **proper time** of a particle are scalars:

```{math}
ds^2 = \eta_{\mu\nu} dx^\mu dx^\nu = -c^2 d\tau^2
```

---

### Rank 1: 4-Vectors

* **4-position:** $x^\mu = (ct, \vec{x})$
* **4-velocity:**

```{math}
u^\mu = \frac{dx^\mu}{d\tau} = \gamma (c, \vec{v})
```

with $\gamma = \frac{dt}{d\tau} = \frac{1}{\sqrt{1-v^2/c^2}}$

* **4-acceleration:** $a^\mu = \frac{du^\mu}{d\tau}$

---

### Derivative Operators

* Covariant derivative in flat spacetime:

```{math}
\partial_\mu = \frac{\partial}{\partial x^\mu}, \quad \partial^\mu = \eta^{\mu\nu} \partial_\nu
```

* Components:

```{math}
\partial_\mu = \left(\frac{\partial}{\partial ct}, \nabla \right), \quad
\partial^\mu = \left(-\frac{\partial}{\partial ct}, \nabla \right)
```

* **D’Alembertian (wave) operator:**

```{math}
\square = \partial_\mu \partial^\mu = -\frac{\partial^2}{\partial t^2} + \nabla^2
```

This operator is **Lorentz invariant**.

---

### Rank 2: Tensors

* Covariant equations are built using tensors to ensure **laws are the same in all inertial frames**.

* Example: **Klein-Gordon equation** for a scalar field (\phi):

```{math}
\square \phi - m^2 \phi = 0
```

---

### Maxwell Equations as Covariant Tensor Equations

* Electromagnetic fields are described by the **field strength tensor** (F_{\mu\nu}):

```{math}
F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu
```

* Maxwell's equations in vacuum:

```{math}
\partial_\mu F^{\mu\nu} = \mu_0 J^\nu, \quad
\partial_\alpha F_{\beta\gamma} + \partial_\beta F_{\gamma\alpha} + \partial_\gamma F_{\alpha\beta} = 0
```

These are **manifestly covariant** under Lorentz transformations.

---

### Why Covariance Matters

Equations that transform like tensors under Lorentz transformations are **covariant**, meaning all inertial observers see the same physics. This is crucial for building **relativistic laws of nature**.

---

### Lagrangian and Action Principle

#### Classical Mechanics

For a particle with coordinate (q(t)):

```{math}
L(q, \dot{q}) = T - V = \frac{1}{2} m \dot{q}^2 - V(q)
```

Action:

```{math}
S[q] = \int dt\, L(q, \dot{q})
```

Euler-Lagrange equation:

```{math}
\frac{d}{dt} \frac{\partial L}{\partial \dot{q}} - \frac{\partial L}{\partial q} = 0
```

---

#### Action in Special Relativity

* The **Lagrangian must be a scalar** to produce covariant equations of motion.
* **Free particle:**

```{math}
S = -m c \int d\tau = -m c \int \sqrt{-\eta_{\mu\nu} dx^\mu dx^\nu}
```

* **Free scalar field:**

```{math}
\mathcal{L} = \frac{1}{2} \partial_\mu \phi \partial^\mu \phi - \frac{1}{2} m^2 \phi^2
```

* **Electromagnetic field (Maxwell):**

```{math}
\mathcal{L} = -\frac{1}{4} F_{\mu\nu} F^{\mu\nu} - J_\mu A^\mu
```

These **Lagrangians are scalars**, ensuring **covariant equations** under Lorentz transformations.

---

### Summary

* Scalars, vectors, and tensors provide a **language for relativistic physics**.
* Proper choice of Lagrangian guarantees **covariant laws of motion**.
* Maxwell equations, Klein-Gordon equations, and free particles are **tensor equations**, valid in all inertial frames.
