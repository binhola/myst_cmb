---
title: "Inflation in Cosmology"
short_title: "Inflation"
abstract: I dunno know
numbering: true
exports:
  - format: pdf
    template: arxiv_two_column
    article_type: Report
---

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
\begin{align}
    H^2 &= \dfrac{1}{3 M_{pl}^2} \rho \\
    \dot H + H^2 &= - \dfrac{1}{6 M_{pl}^2} (\rho + 3p)
\end{align}
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

:::{prf:proof} Conformal time
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


```{prf:proof} Comoving Hubble radius
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
```{math}
\begin{align}
    d_{\rm hor} &= \tau_{\rm rec} - \tau_i \approx \mathcal{I}(z_{\rm rec}, \infty) \\
    d_A &= \tau_0 - \tau_{\rm rec} = \mathcal{I}(0, z_{\rm rec})
\end{align}
```

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
```{math}
:label: curv_dens
\Omega_k(a) \equiv -\dfrac{k}{(aH)^2}
```
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

From equation {ref}`curv_dens`, we know that whenever the comoving Hubble radius $(aH)^{-1}$ grows, the curvature increases. From observations, we know that today $|1 - \Omega(a_0)| \lesssim 0.01$. In order to achieve this level of flatness of the universe today, we need to explain a much more extreme flatness at early times. In contrast, during inflation, when $(aH)^{-1}$ decreases, the universe is driven towards flatness. 

:::{figure} ../images/inflation_horizon.png
:width: 100%
:label: inflation_horizon

In the early universe and late time, the scales of cosmological interest are susceptible to microphyiscal processes, because they are smaller than the horizon (subhorizon). When they are larger than the horizon (superhorizon), the physics froze.
:::
:::{note} Evolution of $\Omega$
:class: dropdown
We have the relation
$$
\dfrac{d \Omega}{d\ln a} = (1 + 3\omega) \Omega (\Omega - 1)
$$
It is clear the $\Omega = 1$ is an unstable fixed point if the strong energy condition is satisfied, but becomes an attractor during inflation.

**Proof:**
From continuity equation and $p = \omega \rho$, we have
$$
\rho \propto a^{-3(1 + \omega)}
$$
So
$$
\dfrac{d \ln \rho}{d \ln a} = -3 (1+\omega)
$$
From the first Friedmann equation
$$
H^2 = \dfrac{8\pi G}{3} \rho - \dfrac{k}{a^2}
$$
We have the definition of density parameter as
$$
\Omega = \dfrac{8 \pi G}{3H^2} \rho
$$
So
$$
\dfrac{k}{a^2} = H^2 (\Omega - 1)
$$
Also, using continuity equation $\dot \rho = -3 H (1 + \omega) \rho$, we have
$$
2 \dot H H = \dfrac{8\pi G}{3} \dot \rho + 2 \dfrac{k}{a^3} \dot a = -H^2 \Omega \times 3 H (1+ \omega) \rho + 2 H^2 (\Omega - 1) H
$$
So
$$
2 \dfrac{\dot H}{H^2} = - 3 \Omega (1 + \omega) + 2(\Omega - 1)
$$
We have

```{math}
\begin{align}
\dfrac{d \ln \Omega}{d \ln a} &= \dfrac{d \ln \rho}{d \ln a} - 2 \dfrac{d \ln H}{d \ln a} \\
&= \dfrac{d \ln \rho}{d \ln a} - 2 \dfrac{\dot H}{H^2} \\
&= -3(1+\omega) + 3 \Omega (1+\omega) - 2(\Omega - 1) \\
&= [3(1+\omega) - 2 ](\Omega - 1) \\
&= (1 + 3 \omega) (\Omega - 1)
\end{align}
```

So
$$
\dfrac{d\Omega}{d \ln a} = (1 + 3\omega) \Omega (\Omega - 1)
$$
:::

:::{important} Duration of inflation
:open:

How much inflation do we need to solve the horizon problem? We require that the observable universe today fits in the comoving Hubble radius at the beginning of the inflation
$$
(a_0 H_0)^{-1} < (a_I H_I)^{-1}
$$

Assume that the universe was radiation dominated since the end of inflation and ignore the recent dark matter and dark energy dominated-epochs. We have $H \propto a^{-2}$ during radiation domination, then
$$
\dfrac{a_0 H_0}{a_E H_E} \sim \dfrac{a_0}{a_E} \dfrac{a_E^2}{a_0^2} \sim \dfrac{a_E}{a_0} \sim \dfrac{T_0}{T_E} \sim 10^{-28}
$$
where $T_E \sim 10^{15}$ GeV and $T_0 = 10^{-3}$ eV ($\sim 2.7$ K)  

Therefore,
$$
(a_I H_I)^{-1} > (a_0 H_0)^{-1} \sim  10^{28} (a_E H_E)^{-1}
$$

Inflation can solve the horizon problem if $(a H)^{-1}$ shrinks by the factor of $10^{28}$. The most common way to approach this is to assume $H \approx \text{const}$ during inflation. We have $H_I = H_E$ and
$$
\dfrac{a_E}{a_I} > 10^{28} \quad \text{or} \quad \ln \left( \dfrac{a_E}{a_I} \right) > 64
$$

The solution of horizon problem requires about 60 $e$-folds of inflation.

**Remark**: $0$ denotes today, $I$ is the beginning of inflation, $E$ is the end of inflation (reheating).

:::
### Condition for inflation

The key condition is the shrinking of comoving Hubble radius:
$$
\dfrac{d}{dt} (aH)^{-1} < 0
$$

1. **Accelerated expansion**:
$$
\dfrac{d}{dt} (aH)^{-1} = \dfrac{d}{dt} (\dot a)-1 = -\dfrac{\ddot a}{ \dot a^2} < 0
$$
Therefore, during inflation
$$
\ddot a > 0
$$

2. **Slow-varying Hubble parameter**:
We can also write
$$
\dfrac{d}{dt} (aH)^{-1} = - \dfrac{\dot a H + a \dot H}{(aH)^2} = -\dfrac{1}{a} (1 - \epsilon)
$$
where $\epsilon \equiv - \dfrac{\dot H}{H^2}$.
The shrinking Hubble sphere requires
$$
\epsilon = - \dfrac{\dot H}{H^2} < 1
$$
3. **Quasi de-Sitter expansion**: 
For perfect inflation, $\epsilon = 0$, the spacetime becomes de Sitter space
$$
ds^2 = dt^2 - e^{2Ht} dx^2
$$
where $H = \partial_t \ln a = \text{const}$. Inflation has to end, so it can not be perfect. However for small and finite $\epsilon$, this approximation is still valid for the inflationary background. This is why we refer to inflation as a quasi-de Sitter period.
4. **Negative pressure**:
From second Friedmann equation, we have
$$
\omega < -\dfrac{1}{3}
$$
Inflation requires negative pressure or a violation of SEC.
5. **Constant density**:
From continuity equation, we have
$$
\left| \dfrac{d \ln \rho}{d \ln a} \right| = 2\epsilon < 1
$$
For small $\epsilon$ condition, the energy density should be nearly constant. Conventional matter sources all dilute with expansion, so we need to look for something more unusual.

## The physics of inflation
The shrinking Hubble sphere requires
$$
\epsilon = - \dfrac{\dot H}{H^2} = - \dfrac{d \ln H}{d N} < 1
$$
where $d N = H dt = d \ln a$ measures the number of $e$-folds $N$ of inflationary expansion. Small $\epsilon$ means that the fractional change of $H$ per $e$-fold is small. We define
$$
\eta \equiv \dfrac{d \ln \epsilon}{d N} = \dfrac{\dot \epsilon}{\epsilon H}
$$
For inflation to last sufficiently long ($N \sim 60$), $\epsilon$ has to remain small for a sufficiently large number of Hubble parameters. This requirement is fulfilled if $|\eta| < 1$.
