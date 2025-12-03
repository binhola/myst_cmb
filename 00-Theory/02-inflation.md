# Inflation

## Horizon Problem
```{important} Pillars of cosmology
- **Cosmological Principle:** The universe is *homogeneous* and *isotropic* on the large scales.
- The observational fact that the universe is *expanding*.
```

The FLRW metric:
```{math}
:label: flrw
ds^2 = -dt^2 + a^2(t) \left[ \dfrac{dr^2}{1 - kr^2} + r^2 d \Omega^2 \right]
```
where 
$$
k =
\begin{cases} 
-1 & \text{Open universe (hyperbolic)} \\
0 & \text{Flat universe (Euclidean)} \\
+1 & \text{Closed universe (spherical)}
\end{cases}
$$

Observations indicate that the universe is nearly flat, so we consider the case $k=0$, the Friedmann equations read:
```{math}
:label: friedmann
\begin{aligned}
    H^2 &= \dfrac{1}{3 M_{pl}^2} \rho \\
    \dot H + H^2 &= - \dfrac{1}{6 M_{pl}^2} (\rho + 3p)
\end{aligned}
```
where $H = \partial_t \ln a$ is the Hubble parameter; $\rho$ and $p$ are the energy density and pressure of background stress-tensor of a perfect fluid.

To study the causal structure of FLRW metric, we need to understand the light propagation, so we will define the *conformal time* for convenient:
$$
d\tau = \dfrac{dt}{a(t)}
$$

We can rewrite the FLRW metric \@ref(eq:friedmann)

