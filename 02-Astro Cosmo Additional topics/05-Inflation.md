---
title: Slow-roll inflation
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
date: 2026-02-17
---

# Motivation

The $\Lambda$CDM model is a perfectly satisfactory model of the universe for $t \gtrsim 10^{-3}$ s (scales at nuclear reactions), consistent with Big Bang nucleosynthesis, Hubble law, and growth of large-scale structure. However, the initial condition of the model (hot and dense in thermal equilibrium) is not explained.

Therefore, the model is not complete. $\Lambda$CDM has a number of structure problems/unanswered questions:
- **Flatness problem**: Why is the universe so flat today?
- **Horizon problem**: Why is the CMB so homogeneous on scales that were never in causal contact?
- **"Density fluctuation" problem**: What is the origin of the primordial seeds for structure formation?

These are **initial condition problems** — and these are what inflation addresses. 
(What is CDM or what is $\Lambda$ are questions inflation does **not** address.)

```{important}
**Inflation** is defined as a phase of accelerated expansion ($\ddot{a} > 0$) before the radiation-dominated era.
```

## Inflation condition

```{prf:observation} Inflation condition
Consider a power-law expansion $a \sim t^p$. Then
$$
\dot a \sim p \, t^{p - 1}, \qquad \ddot{a} \sim p(p-1) t^{p-2}.
$$
To have inflation ($\ddot{a} > 0$), we need $p > 1$.

For normal matter, we cannot have inflation because:
$$
p = \frac{2}{3} \quad \text{(matter-dominated)}, \qquad
p = \frac{1}{2} \quad \text{(radiation-dominated)}.
$$
```

If we take $\rho = \text{constant}$, then $a \sim e^{\text{const} \times t}$, so $\ddot{a} > 0$. But such accelerated expansion never ends, so it cannot be followed by radiation and matter eras. We need a mechanism to realize a **finite period of inflation**. This leads us to postulate a scalar field.

```{figure} #adot_sche
:width: 100%
:label: adot-sche

A schematic for $\dot a$. We can see that $\dot a$ increases during inflation, then decreases rapidly in the radiation era, decreases more slowly in the matter era, and increases again in the dark energy era.
```

> Are we simply pushing the problem of initial conditions back to $t_{inf}$?

The answer is **no**, because slow-roll inflation is an **attractor solution**.

:::{prf:example} Attractor solution
:label: attractor-example
Consider the differential equation
$$
\frac{dy}{dt} = -(y-1).
$$
The solution is
$$
y = 1 + A e^{-t}.
$$

```{figure} #attractor_example
:width: 80%
:label: attractor-example-fig

Example of an attractor. No matter what the initial condition, as time goes on the function always converges to a certain value.
```
:::

# Aspects of inflation

## Homogeneous and isotropic cosmology with inflation

> Why does inflation solve the flatness and horizon problems? 
> What do you have to do to get a period of primordial inflation? 
> Why is slow roll an attractor solution?

### Basic equations

For a Friedmann-Lemaître-Robertson-Walker (FLRW) universe, we have:

$$
\begin{cases}
    H^2 = \dfrac{\rho}{3 M_{pl}^2} - \dfrac{k}{a^2}, \qquad M_{pl}^2 = \dfrac{1}{8\pi G}, \qquad k = \begin{cases}
        1 \quad \text{closed} \\
        0 \quad \text{flat} \\
        -1 \quad \text{open}
    \end{cases} \\[6pt]
    \dfrac{\ddot{a}}{a} = -\dfrac{4\pi G}{3} (\rho + 3P) \\[6pt]
    \dot \rho = -3 H (\rho + P)
\end{cases}
$$

### The comoving Hubble radius

Define the **comoving Hubble radius** as $(aH)^{-1}$. If $a \sim t^p$, then

$$
(aH)^{-1} \sim \frac{1}{p} t^{1-p}.
$$

- **Radiation/matter domination** ($p < 1$): $(aH)^{-1}$ **increases** with time.
- **Inflation** ($p > 1$): $(aH)^{-1}$ **decreases** with time.

```{note}
The shrinking Hubble radius during inflation is the key to solving the horizon and flatness problems.
```

### The flatness problem

Define $\Omega(t) = \dfrac{\rho(t)}{\rho_c}$, where $\rho_c = \dfrac{3 H^2}{8\pi G}$. Then

$$
\Omega(t) - 1 = \Omega_k = \dfrac{k}{(aH)^2}.
$$

- **Radiation/matter domination**: $\Omega_k$ **increases** with time. CMB observations constrain $|\Omega_k| \lesssim 0.0007$ today. This requires extreme fine-tuning of $\Omega_k$ at the beginning of the radiation era.
- **Inflation**: $\Omega_k$ **decreases** during inflation, solving the fine-tuning problem. To satisfy the observational constraint, we need
  $$
  |\Omega_k(t_{pl})| \sim 10^{-60}.
  $$

### Number of e-folds

Define the number of **e-folds** as

$$
N \equiv \ln\left( \frac{a_{end}}{a} \right).
$$

If $a = a_{ini}$, we have

$$
N_\star \equiv \ln\left( \frac{a_{end}}{a_{ini}} \right).
$$

To solve the flatness problem, we need $N_\star \gtrsim 50$.

```{prf:example} Evolution of the Hubble radius
:label: hubble-radius-example

- In a **radiation-dominated** universe, $a \sim t^{1/2}$, so
  $$
  \frac{1}{aH} \sim t^{1/2} \sim a, \qquad \ln\left( \frac{1}{aH} \right) \sim \ln a.
  $$

- In a **matter-dominated** universe, $a \sim t^{2/3}$, so
  $$
  \frac{1}{aH} \sim t^{1/3} \sim a^{1/2}, \qquad \ln\left( \frac{1}{aH} \right) \sim \frac{1}{2} \ln a.
  $$

- For a **de Sitter** inflation ($H = \text{const}$),
  $$
  \frac{1}{aH} \sim \frac{1}{a}, \qquad \ln\left( \frac{1}{aH} \right) \sim -\ln a.
  $$
```

## Quantum fluctuations around the background inflationary solution

> How do these become the initial conditions for the $\Lambda$CDM model?

```{figure} #inflation_example
:width: 100%
:label: inflation-example

Hubble horizon evolution. Scales inside the horizon evolve; scales outside the horizon freeze.
```

## Realizing inflation with a scalar field

Inflation requires $\ddot{a} > 0$, which from the second Friedmann equation implies

$$
\rho + 3P < 0 \quad \Rightarrow \quad P < -\frac{\rho}{3}.
$$

This requires **negative pressure**. A cosmological constant gives accelerated expansion but never stops. We introduce a scalar field $\phi$ with a potential $V(\phi)$ to achieve a finite period of inflation.

If $\phi = \text{const}$, this is equivalent to a cosmological constant since $\rho_\phi = \text{const}$.

**Slow-roll inflation**: We consider a potential $V(\phi)$ such that $\phi$ moves very slowly down the potential.

### Scalar field action and equations

The action for a scalar field is

$$
S_\phi = \int d^4 x \sqrt{-g} \left( -\frac{1}{2} \partial_\mu \phi \partial_\nu \phi \, g^{\mu \nu} - V(\phi) \right).
$$

The stress-energy tensor is

$$
T_{\mu \nu} = -\frac{2}{\sqrt{-g}} \frac{\delta S_\phi}{\delta g^{\mu \nu}} = \partial_\mu \phi \partial_\nu \phi - g_{\mu \nu} \left( \frac{1}{2} \partial_\alpha \phi \partial^\alpha \phi + V(\phi) \right).
$$

Varying the action with respect to $\phi$ gives the Klein-Gordon equation

$$
\nabla_\mu \nabla^\mu \phi = \frac{\partial V}{\partial \phi}.
$$

For a flat FLRW metric $g_{\mu\nu} = \text{diag}(-1, a^2(t)\delta_{ij})$, this becomes

```{math}
:label: kg-equation
\boxed{\ddot{\phi} + 3H\dot{\phi} + \frac{dV}{d\phi} = 0}.
```

From $T^0_0$ and $T^i_j$, we obtain the energy density and pressure:

$$
\rho = \frac{1}{2} \dot{\phi}^2 + V(\phi), \qquad
P = \frac{1}{2} \dot{\phi}^2 - V(\phi).
$$

### Slow-roll conditions

Inflation requires $P/\rho \ll -1/3$, i.e., $\dot{\phi}^2 \ll V$. This is the **first slow-roll condition**:

```{important}
:label: slow-roll-conditions
**Slow-roll conditions**

1. $\dfrac{1}{2} \dot{\phi}^2 \ll V$ (kinetic energy much smaller than potential)
2. $|\ddot{\phi}| \ll |3H\dot{\phi}|, |V'|$ (acceleration negligible)
```

Under these conditions, the equations simplify dramatically:

$$
H^2 \approx \frac{1}{3M_{pl}^2} V(\phi), \qquad
3H\dot{\phi} \approx -V'(\phi).
$$

### Slow-roll parameters

It is convenient to define dimensionless **slow-roll parameters** in terms of the potential.

```{prf:definition} Slow-roll parameters
The **potential slow-roll parameters** are defined as

$$
\epsilon_V \equiv \frac{M_{pl}^2}{2} \left( \frac{V'}{V} \right)^2, \qquad
\eta_V \equiv M_{pl}^2 \left( \frac{V''}{V} \right).
$$

Slow-roll inflation requires $\epsilon_V \ll 1$ and $|\eta_V| \ll 1$.
```

```{prf:proof} Relation to dynamics
:class: dropdown
From the slow-roll equations, we have $\dot{\phi} = -V'/(3H)$. Substituting into the definition of $\epsilon_V$:

$$
\epsilon_V = \frac{M_{pl}^2}{2} \left( \frac{V'}{V} \right)^2 = \frac{M_{pl}^2}{2} \left( \frac{3H\dot{\phi}}{V} \right)^2.
$$

Using $H^2 \approx V/(3M_{pl}^2)$, we get $V \approx 3M_{pl}^2 H^2$, so

$$
\epsilon_V \approx \frac{M_{pl}^2}{2} \left( \frac{3H\dot{\phi}}{3M_{pl}^2 H^2} \right)^2 = \frac{1}{2M_{pl}^2} \left( \frac{\dot{\phi}}{H} \right)^2.
$$

This shows $\epsilon_V$ measures the kinetic energy relative to the potential.

Similarly, one can show that $\eta_V$ measures the acceleration term $\ddot{\phi}/(H\dot{\phi})$.
```

One can also show that

$$
\frac{\ddot{a}}{a} \approx H^2 (1 - \epsilon_V).
$$

Inflation ends when either $\epsilon_V$ or $|\eta_V|$ becomes of order 1.

### Number of e-folds in terms of the potential

The number of e-folds can be expressed as an integral over the field.

```{prf:proof} Number of e-folds
:class: dropdown
We have $dN = d\ln a = H dt$. Using $dt = d\phi/\dot{\phi}$ and the slow-roll relation $\dot{\phi} \approx -V'/(3H)$,

$$
dN = H \frac{d\phi}{\dot{\phi}} = H \left( -\frac{3H}{V'} \right) d\phi = -\frac{3H^2}{V'} d\phi.
$$

Using $H^2 \approx V/(3M_{pl}^2)$,

$$
dN = -\frac{V}{M_{pl}^2 V'} d\phi.
$$

Thus the number of e-folds between a field value $\phi$ and the end of inflation $\phi_{end}$ is

:::{math}
:label: efolds-integral
\boxed{N(\phi) = \int_{\phi_{end}}^{\phi} \frac{V}{M_{pl}^2 V'} \, d\phi'}.
:::
```

```{prf:example} Quadratic potential
:label: quadratic-example
Consider $V(\phi) = \frac{1}{2} m^2 \phi^2$.

- **Slow-roll parameters**:
  $$
  \epsilon_V = \frac{M_{pl}^2}{2} \left( \frac{2}{\phi} \right)^2 = 2 \left( \frac{M_{pl}}{\phi} \right)^2, \qquad
  \eta_V = 2 \left( \frac{M_{pl}}{\phi} \right)^2.
  $$
  Both are small when $\phi \gg M_{pl}$.

- **Number of e-folds**:
  Using $V/V' = \phi/2$,
  $$
  N = \int_{\phi_{end}}^{\phi} \frac{\phi}{2M_{pl}^2} d\phi = \frac{\phi^2 - \phi_{end}^2}{4M_{pl}^2}.
  $$
  Inflation ends when $\epsilon_V \approx 1$, i.e., $\phi_{end} \approx \sqrt{2} M_{pl}$. For $N \approx 60$, we need $\phi \approx \sqrt{4N} M_{pl} \approx 15 M_{pl}$.
```

# Slow-roll inflation is an attractor solution

One of the key features of slow-roll inflation is that it is an **attractor**: independent of the initial conditions $(\phi_i, \dot{\phi}_i)$, the solution $\phi(t)$ converges to the slow-roll trajectory.

We demonstrate this for the quadratic potential $V(\phi) = \frac{1}{2} m^2 \phi^2$.

## a. The slow-roll solution

From the slow-roll equation $3H\dot{\phi} = -V'$, with $H^2 \approx V/(3M_{pl}^2)$:

```{math}
:label: sr-solution-quadratic
\dot{\phi}_{SR} = -\frac{V'}{3H} = -\frac{m^2 \phi}{3\sqrt{\frac{V}{3M_{pl}^2}}} = -\frac{m^2 \phi}{3\sqrt{\frac{m^2 \phi^2}{6M_{pl}^2}}} = -\frac{m M_{pl}}{\sqrt{3/2}} \frac{\phi}{|\phi|}.
```

For $\phi > 0$, $\dot{\phi}_{SR} = -\sqrt{\frac{2}{3}} m M_{pl}$ — a **constant** (negative) velocity.

## b. Convergence to the slow-roll solution

We want to show that any trajectory approaches this solution.

:::{math}
:label: phase-flow
\frac{d\dot{\phi}}{d\phi} = -\frac{\sqrt{3}}{M_{pl}} \sqrt{\frac{1}{2}\dot{\phi}^2 + \frac{1}{2}m^2\phi^2} - \frac{m^2\phi}{\dot{\phi}}.
:::

:::{figure} #phase-space-family
:label: phasespace

The attractor of inflation: family of phase-space trajectories showing convergence to the slow-roll solution.

:::

```{prf:proof} Attractor behavior for quadratic potential
:class: dropdown

Start from the full Friedmann and Klein-Gordon equations:

$$
H^2 = \frac{1}{3M_{pl}^2} \left( \frac{1}{2} \dot{\phi}^2 + \frac{1}{2} m^2 \phi^2 \right), \qquad
\ddot{\phi} + 3H\dot{\phi} + m^2 \phi = 0.
$$

We can study the phase space $(\phi, \dot{\phi})$. Define dimensionless variables:

$$
x = \frac{\phi}{M_{pl}}, \qquad y = \frac{\dot{\phi}}{m M_{pl}}, \qquad \tau = m t.
$$

Then the equations become:

$$
\frac{dx}{d\tau} = y, \qquad
\frac{dy}{d\tau} = -3\tilde{H} y - x,
$$

where $\tilde{H} = H/m = \sqrt{\frac{1}{6}(y^2 + x^2)}$.

The slow-roll solution corresponds to $y = -\sqrt{2/3}$ (for $x>0$). To study convergence, consider a small deviation: $y = -\sqrt{2/3} + \delta y$, $x = x_{SR} + \delta x$. Linearizing the equations around the slow-roll trajectory shows that perturbations decay exponentially in time, demonstrating that the slow-roll solution is an attractor.

Alternatively, we can derive a first-order equation for $\dot{\phi}(\phi)$. From

$$
\frac{d\dot{\phi}}{d\phi} = \frac{\ddot{\phi}}{\dot{\phi}} = -\frac{3H\dot{\phi} + m^2\phi}{\dot{\phi}} = -3H - \frac{m^2\phi}{\dot{\phi}}.
$$

Substituting $H = \sqrt{\frac{1}{3M_{pl}^2}\left( \frac{1}{2}\dot{\phi}^2 + \frac{1}{2}m^2\phi^2 \right)}$, we get

:::{math}
:label: phase-flow
\frac{d\dot{\phi}}{d\phi} = -\frac{\sqrt{3}}{M_{pl}} \sqrt{\frac{1}{2}\dot{\phi}^2 + \frac{1}{2}m^2\phi^2} - \frac{m^2\phi}{\dot{\phi}}.
:::

This is a first-order ODE for $\dot{\phi}(\phi)$. The slow-roll solution is a particular solution. One can show numerically (or analytically by linearizing around it) that all trajectories in the phase plane flow toward this solution as $\phi$ decreases.
```

Thus, slow-roll inflation is indeed an attractor: regardless of the initial field velocity, the system quickly converges to the slow-roll trajectory, making the predictions of inflation insensitive to initial conditions. This is why inflation solves the fine-tuning problems of the standard Big Bang model.

```{important} Summary
- Inflation requires $\ddot{a} > 0$, achieved by a scalar field with potential $V(\phi)$.
- Slow-roll conditions: $\dot{\phi}^2 \ll V$, $|\ddot{\phi}| \ll |3H\dot{\phi}|, |V'|$.
- Slow-roll parameters $\epsilon_V, \eta_V \ll 1$ ensure inflation lasts long enough.
- The number of e-folds $N \gtrsim 50$ solves the flatness and horizon problems.
- Slow-roll inflation is an **attractor** — initial conditions are quickly forgotten.
- Quantum fluctuations during inflation become the seeds for structure formation.
```