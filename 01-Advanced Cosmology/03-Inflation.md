# Inflation

## Inflation and Slow-roll Model
:::{seealso} Inflation lecture
See the [Inflation](../02-Astro%20Cosmo%20Additional%20topics/05-Inflation.md) lecture by **Daniel Steer**
:::

## Quantum initial condition
Inflation provides a natural mechanism for producing initial conditions: the evolution of the inflaton field $\phi(t)$ governs the energy density of the early universe $\rho(t)$. The field $\phi$ plays the role of local "clock" reading off the amount of inflationary expansion to occur. By uncertainty principle, precise timing is not possible in quantum mechanics, so there is some variance in form of spatially varying fluctuations $\delta \phi(t, \mathbf{x})$. Therefore, there will be local differences in time when inflation ends, $\delta t(\mathbf{x})$, leading to different local densities after inflation, $\delta \rho(t,\mathbf{x})$, and to the curvature perturbation in comoving gauge $\mathcal{R}(\mathbf{x})$. 

### Inflaton fluctuations: Classical
Inflaton action
$$
S = \int d\eta d^3 x \sqrt{-g} \left[ \dfrac{1}{2} g^{\mu \nu} \partial_\mu \phi \partial_\nu \phi - V(\phi) \right]
$$
where $g \equiv \det g_{\mu \nu}$. 

For linearised dynamics, we need the action at quadratic order in fluctuations. For simplicity, we work in *spatially flat gauge*, in which we use the freedom of choice for coordinates to set the spatial metric to unperturbed $g_{ij} = - a^2 \delta_{ij}$. In this gauge, the information of perturbation is carried by the inflaton perturbation $\delta \phi$ and the metric $\delta g_{0 \mu}$ (related by Einstein equations). 

Evaluating the *unperturbed FRW metric*, we find
$$
S = \int d \eta d^3 x \left[ \dfrac{1}{2} a^2 (\dot{\phi}^2 - (\nabla \phi)^2) - a^4 V(\phi) \right]
$$

We write the perturbed inflaton field as
$$
\phi(\eta, \mathbf{x}) = \bar \phi(\eta) + \dfrac{f(\eta, \mathbf{x})}{a(\eta)}
$$

To get the linearised motion for $f(\eta, \mathbf{x})$, we need to expand the action to second order in the fluctuations: 
$$
S_{(2)} = \int d\eta d^3 x \dfrac{1}{2} \left[ \dot{f}^2 - (\nabla f)^2 + \dfrac{\ddot{a}}{a} f^2 \right]
$$

:::{prf:proof}

:::