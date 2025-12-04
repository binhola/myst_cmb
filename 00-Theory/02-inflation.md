# Inflation

## Horizon Problem

### Review of cosmological framework
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
where 
- $H = \partial_t \ln a$ is the Hubble parameter
- $\rho$ and $p$ are the energy density and pressure of background stress-tensor of a perfect fluid.

To study the causal structure of FLRW metric, we need to understand the light propagation, so we will define the *conformal time* for convenient:
$$
d\eta = \dfrac{dt}{a(t)}
$$

We can rewrite the FLRW metric as:
$$
ds^2 = a^2(\tau)[-d\eta^2 + dr^2 + r^2 d\Omega^2] = a^2(\tau) \eta_{\mu \nu} dx^\mu dx^\nu
$$

where $\eta_{\mu \nu}$ is the static Minkowski metric.

### Causal structure
The radial propagation of light is characterized by the following two-dimensional line element
$$
ds^2 = a^2(\tau) [-d\eta^2 + dr^2] = 0
$$

We get the solution for the null geodesic as
$$
r(\tau) = \pm \tau + \text{const}
$$

The maximal distance a photon can travel between an initial time $t_i$ and late time $t > t_i$ is also the ellapsed conformal time between 2 events:
$$
\Delta r = \Delta \tau = \tau - \tau_i = \int_{t_i}^{t} \dfrac{t'}{a(t')}
$$ 

Taken the initial time to be the "origin of the universe": $t_i = 0$ defined by the Big Bang singularity $a_i \equiv a(t_i = 0) \equiv 0$, we define the **comoving (particle) horizon** as:
$$
\Delta r_{\rm max} = \int_0^t \dfrac{dt'}{a(t')} = \tau (t) - \tau(0)
$$

Conformal time can also be rewrited as
$$
\tau = \int d \ln a (aH)^{-1} 
$$

The ellapsed conformal time depends on the evolution of the *comoving Hubble radius* $(aH)^{-1}$.

:::{dropdown} Derivation of $\tau = \int d \ln a (aH)^{-1}$
:class: dropdown

$$\tau \equiv \int \dfrac{dt}{a(t)} = \int \dfrac{da}{a} \left( a \dfrac{da}{dt} \dfrac{1}{a} \right)^{-1} = \int d\ln a (aH)^{-1}$$
:::

Consider a universe dominated by a fluid with an equation of state:

$$
\omega = \frac{p}{\rho}
$$

The comoving Hubble radius reads:
$$
(aH)^{-1} \propto a^{\frac{1}{2} (1+3\omega)}
$$


```{dropdown} Comoving Hubble radius
:class: dropdown

Using the **continuity equation**:

$$
\dot \rho + 3 H (\rho + p) = 0
$$

and substituting the equation of state $p = \omega \rho$, we obtain

$$
\dot \rho + 3 H \, \rho (1 + \omega) = 0
$$

Rewriting in terms of the scale factor $a(t)$, we have

$$
\frac{d\rho}{\rho} = -3(1+\omega) \frac{da}{a}
$$

Integrating this equation gives the evolution of the energy density:

$$
\rho \propto a^{-3(1+\omega)}
$$

Putting into the first Friedmann equation:

$$
H = H_0 a^{\frac{3}{2}(1+\omega)}
$$

We finally obtain
$$
(aH)^{-1} \propto a^{\frac{1}{2} (1+3\omega)}
$$
```

The comoving Hubble radius increases as the universe expands for all the farmiliar matter sources because they satisfied the *strong energy condition* (SEC):
$$
1 + 3\omega > 0
$$

The conformal time now reads:
$$
\tau = \dfrac{2}{3\omega+1} a^{\frac{1}{2} (1+3\omega)}
$$

For normal matter with $\omega > -\frac{1}{3}$ the initial time:
$$
t_i \propto a_i^{\frac{1}{2}(1+3\omega)} = 0, \quad \omega > -\frac{1}{3}
$$
and the comoving horizon is finite:
$$
\Delta r_{\rm max} \propto a(t)^{\frac{1}{2} (1+3\omega)}
$$

### Problems with CMB
:::{figure} ../images/cmb_horizon_problem.png
:width: 100%
:label: fig-cmb-horizon

This figure shows the CMB horizon problem: regions that are causally disconnected appear to have the same temperature.
:::

The angle subtended by comoving horizon at recombination reads
$$
\theta_{\rm hor} = \dfrac{d_{\rm hor}}{d_A}
$$
where
- $d_{\rm hor}$ is the comoving horizon.
- $d_{A}$ is the comoving angular diameter distance from today to the recombination.

We define
$$
\tau_2 - \tau_1 = \int_{z_1}^{z_2} \dfrac{dz}{H(z)} = \mathcal{I}(z_1, z_2)
$$
In flat universe, we have
$$
\begin{aligned}
    d_{\rm hor} &= \tau_{\rm rec} - \tau_i \approx \mathcal{I}(z_{\rm rec}, \infty) \\
    d_A &= \tau_0 - \tau_{\rm rec} = \mathcal{I}(0, z_{\rm rec})
\end{aligned}
$$

From numerical calculation, we get
$$
\theta_{\rm hor} = \dfrac{\mathcal{I}(z_{\rm rec}, \infty)}{\mathcal{I}(0, z_{\rm rec})} = 1.15^\circ
$$

:::{figure} #I_evo 
:width: 100%
:label: fig-I-evo

Evolution of the cummulative $\mathcal{I}(0, z)$
:::

With the conventional Big Bang cosmology, the causal connection should vanish and sends the correlation function to zero for
$$
\theta > 2 \theta_{\rm hor} = 2.3^\circ
$$

However, observations of CMB show that the CMB temperature is extraordinary uniform:
$$
\dfrac{\delta T}{T} \sim 10^{-5} 
$$

## The shrinking Hubble sphere
The problem of the standard Big Bang cosmology lies in the growing of Hubble sphere, so a simple solution to the horizon problem is to conjecture a phase of decreasing Hubble radius in the early universe. 
$$
\dfrac{d}{dt} (aH)^{-1} < 0
$$
This period should last long enough to stretch a tiny correlated patch to a size close to the observable universe today.

### Solution to Horizon problem
A decreasing Hubble radius requires a violation of the SEC:
$$
\omega < -\frac{1}{3}
$$
The Big Bang singularity is pushed to negative conformal time:
$$
t_i \propto a_i^{\frac{1}{2}(1+3\omega)} = -\infty, \quad \omega < -\frac{1}{3}
$$

:::{figure} ../images/CMB_horizon_solu.png
:width: 70%
:label: cmb_horizon_solu

Solution for horizon problem
:::
This suggests that there is more conformal time between singularity and recombination than standard Big Bang cosmology scenario. $\tau = 0$ is no longer the singularity but the time of reheating. A decreasing comoving horizon means that large scales were inside the horizon before inflation, so the universe had time to establish spatial homogeneity.

### Solution to the Flatness problem
The shrinking Hubble sphere can also solve the flatness problem.

Consider spatial curvature in the first Friedmann equation:
$$
H^2 = \dfrac{\rho}{3 M_{pl}^2} - \dfrac{k}{a^2}
$$
Divide both side by $H$, we get
$$
1 - \Omega(a) = -\dfrac{k}{(aH)^2}
$$
where $\Omega(a) \equiv \dfrac{\rho(a)}{\rho_{\rm crit}(a)}$ and $\rho_{\rm crit} = 3 M_{pl}^2 H^2$.

Define the curvature density parameter:
$$
\Omega_k(a) \equiv -\dfrac{k}{(aH)^2}
$$
so that
$$
\Omega(a) + \Omega_k(a) = 1
$$

the curvature of the universe can be quantified as

$$
\begin{cases}
    \Omega (a) &= 1 \to k = 0 \text{(flat)}\\
    \Omega (a) &> 1 \to k = -1 \text{(negatively curved)}\\
    \Omega (a) &< 1 \to k = +1 \text{(positively curved)}
\end{cases}
$$