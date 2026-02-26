# Linear Perturbation Evolution in minimal model

## Equation of motions (DraftXXX)
The equations of motion for the matter perturbations come from conservation of the stress tensor
$$
\boxed{
\nabla^\mu T_{\mu \nu} = 0}
$$
Developing the covariant derivative
$$
\nabla^\mu T_{\mu \nu} = \partial_\mu T^\mu_\nu + \Gamma^\mu_{\mu \alpha} T^{\alpha}_\nu - \Gamma^\alpha_{\mu \nu} T^\mu_\alpha = 0
$$
For $\nu = 0$, we have the **conitinuity equation** (equation of density perturbation evolution):
```{math}
:label: continuity-eq

\boxed{
\partial_\eta \delta \rho = -3 \mathcal{H} (\delta \rho + \delta P) + 3 \dot \psi (\bar \rho + \bar P) - \partial_i q^i}
```

For $\nu = i$, we have the **Euler equation** (equation of momentum perturbation evolution):
```{math}
:label: euler-eq

\boxed{
\partial_\eta ((\bar{\rho} + \bar{P})v^i) = -4 \mathcal{H} q^i - (\bar \rho + \bar P ) \partial^i \phi - \partial^i \delta P - \partial_j \Pi^{ij}
}
```
:::{prf:proof} Equation of motion 
:class: dropdown

- Density perturbation evolution
:::

We evaluate equations {eq}`continuity-eq` and {eq}`euler-eq` in few cases:
1. **Matter**: non-relativistic fluid, $P_m = 0$ and $\Pi^{ij}_m = 0$
$$
\dot \delta_m &= - \nabla \cdot \mathbf{v}_m + 3 \dot \psi \\
\dot{\mathbf{v}}_m &= - \mathcal{H} \mathbf{v}_m - \nabla \phi
$$

1. **Radiation**: relativistic fluid, $P_r = \dfrac{1}{3} \rho_r$ and $\Pi^{ij}_r = 0$
$$
\dot \delta_r &= - \dfrac{4}{3} \nabla \cdot \mathbf{v}_r + 4 \dot \psi \\
\dot{\mathbf{v}}_r &= - \dfrac{1}{4} \nabla \delta_r - \nabla \phi
$$

## Initial conditions
### Adiabatic fluctuations
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

:::{important} Initial conditions
At early times, the universe is **radiation dominated**, so it natural to set the initial conditions for all **superhorizon** Fourier modes. 
- Equation {eq}`metric-potential` implies that $$\boxed{\phi = \text{const}}$$
on superhorizon scales.
- From equation {eq}`00-com`, we have
$$
\boxed{
\delta \approx \delta_r = -2 \phi
}
$$
on superhorizon scales.
- The velocity divergence $\theta$ is related to $\phi$ via the **0i** Einstein equation
$$ \dot \phi + \mathcal{H} \phi \propto (\bar \rho + \bar P) \theta $$
so $\theta$ is *negligible* (decaying mode) on superhorizon scales (with $\phi = \text{const}$).
- The pressure perturbation $\delta P$ is not independent but given by
$$
\delta P = c^2_s \delta \rho = c^2 s(-2 \bar \rho \phi)
$$

Thus, **all matter perturbation variables** ($\delta$, $\delta P$, $\theta$, $\sigma$ if present) can be expressed in terms of **single constant** $\phi$ on superhorizon scales. 
:::

:::{prf:proof} Initial conditions
:class: dropdown

From equation {eq}`00-com`, on the superhorizon scales ($k \ll \mathcal{H}$), the term $\nabla^2 \phi$ is negligible, leaving
$$
-3 \mathcal{H}(\dot \phi + \mathcal{H} \phi) = 4 \pi G a^2 \delta \rho
$$

Since $\phi = \text{const}$, $\dot \phi = 0$
$$
-3 \mathcal{H}^2 \phi = 4 \pi G a^2 \delta \rho
$$
Using Friedmann equation
$$
3 \mathcal{H}^2 = 8 \pi G a^2 \bar \rho
$$
we have

$$
- 8 \pi G a^2 \bar \rho \phi &= 4 \pi G a^2 \delta \rho \\
$$
Therefore,
$$
\delta &= -2 \phi = \text{const}
$$
:::