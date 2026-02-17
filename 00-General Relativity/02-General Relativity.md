# Towards Curved Spacetime

## Equivalence Principle

### 1. Weak Equivalence Principle (WEP)

Experimental observation shows that **inertial mass** $m_i$ equals **gravitational mass** $m_g$.

- For a point particle in an **electric potential** $\phi_E$:

$$
m_i \, \vec{a} = -q_e \, \nabla \phi_E
$$

- For a point particle in a **gravitational potential** $\phi_g$:

$$
m_i \, \vec{a} = -m_g \, \nabla \phi_g
$$

Observation: $m_i = m_g \implies \vec{a} = -\nabla \phi_g$  

**Consequence:** The acceleration due to gravity is **universal**, independent of the particle’s mass or composition.

---

### 2. Free-Falling Frame (FFF)

- In a region with a **constant gravitational field**, one can define a frame where **gravity disappears locally**.  
- For **non-uniform gravity**, a **local FFF** can still be defined.  
- Gravity manifests as a **change of coordinates**, i.e., the metric encodes the gravitational field.

---

### 3. Einstein Equivalence Principle (EEP)

- **Locally**, physics in a free-falling frame is identical to physics in **Minkowski spacetime** (SR applies).  
- At any point in spacetime, one can choose coordinates such that the laws of physics take their SR form.

---

### 4. Strong Equivalence Principle (SEP)

- Extends EEP to **all laws of nature**, including gravitational interactions themselves.  

**Summary:**

| Principle | Scope |
|-----------|-------|
| WEP | Test bodies |
| EEP | Non-gravitational interactions |
| SEP | All laws including gravity |

---

## Non-Inertial Frames

### a. Lorentz Transformations

- In flat spacetime (SR), Lorentz transformations are **linear**:

$$
x^\mu \to y^\mu = \Lambda^\mu{}_\nu x^\nu
$$

- The **spacetime interval** is invariant:

$$
ds^2 = \eta_{\mu\nu} dx^\mu dx^\nu
$$

- In a new frame $y^\mu$:

$$
dx^\mu = \frac{\partial x^\mu}{\partial y^\alpha} dy^\alpha
$$

- Substituting:

$$
ds^2 = \eta_{\mu\nu} \frac{\partial x^\mu}{\partial y^\alpha} \frac{\partial x^\nu}{\partial y^\beta} dy^\alpha dy^\beta
$$

- For linear Lorentz transformations, this reduces to:

$$
\eta_{\mu\nu} \frac{\partial x^\mu}{\partial y^\alpha} \frac{\partial x^\nu}{\partial y^\beta} = \eta_{\alpha\beta}
$$

---

### b. General Curvilinear Transformations

- For a **general invertible transformation**:

$$
x^\mu \to y^\mu(x^\alpha)
$$

- Jacobian matrix:

$$
J^\mu{}_\nu = \frac{\partial y^\mu}{\partial x^\nu}
$$

- The metric in the new frame $R'$ is:

$$
g_{\alpha\beta}(y) = \eta_{\mu\nu} \frac{\partial x^\mu}{\partial y^\alpha} \frac{\partial x^\nu}{\partial y^\beta}
$$

- If $R'$ is a **FFF**, the metric encodes the **gravitational interaction**.

---

### c. Motion of a Particle in Non-Inertial Frame

- In an **inertial frame $R$** (or FFF in gravity):

$$
a^\mu = \frac{d^2 x^\mu}{d\tau^2} = 0
$$

- In a general frame $y^\mu$:

$$
\frac{d^2 y^\alpha}{d\tau^2} = \frac{\partial y^\alpha}{\partial x^\mu} \frac{d^2 x^\mu}{d\tau^2} + \frac{\partial^2 y^\alpha}{\partial x^\mu \partial x^\nu} \frac{dx^\mu}{d\tau} \frac{dx^\nu}{d\tau}
$$

- Since $d^2 x^\mu / d\tau^2 = 0$, we get:

$$
\frac{d^2 y^\alpha}{d\tau^2} + \underbrace{\frac{\partial^2 y^\alpha}{\partial x^\mu \partial x^\nu} \frac{\partial x^\mu}{\partial y^\beta} \frac{\partial x^\nu}{\partial y^\gamma}}_{\Gamma^\alpha_{\beta\gamma}} \frac{dy^\beta}{d\tau} \frac{dy^\gamma}{d\tau} = 0
$$

- This defines the **geodesic equation** in the new frame:

$$
\frac{d^2 y^\alpha}{d\tau^2} + \Gamma^\alpha_{\beta\gamma} \frac{dy^\beta}{d\tau} \frac{dy^\gamma}{d\tau} = 0
$$

where $\Gamma^\alpha_{\beta\gamma}$ are the **Christoffel symbols** (affine connection).  

- The parameter $\tau$ is the **affine parameter**, usually the **proper time** for massive particles.

---

### Summary

- Gravity can be interpreted as **curvature of spacetime**.  
- Free-fall corresponds to **geodesic motion**.  
- Christoffel symbols encode the effects of **non-inertial (curved) frames**.  
- This is the **geometric foundation of General Relativity**.
