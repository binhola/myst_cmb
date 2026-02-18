---
title: Introduction to Gravitational Waves
author:
  - name: Binh Nguyen
    affiliations: Universite Paris Saclay
    email: yenbinhpy308@gmail.com
date: 2026-02-17
---

# Introduction

The merger of a binary system (e.g. two black holes) generates gravitational waves. A typical amplitude from detected signals is divided into three main phases, as shown in {numref}`fig-gw-amp`. This course will focus primarily on the first *inspiral* phase, where the two black holes are still well separated.

```{figure} ../images/astrocosmo/bh_merging.png
---
width: 70%
align: center
name: fig-gw-amp
---
A typical gravitational-wave signal produced by a pair of coalescing black holes. The inspiral phase can be described by post-Newtonian series expansion, while the late part of the ringdown phase can be described using linear perturbation theory (blue parts of the signal). The merger and early ringdown, however, exhibit nonlinear spacetime dynamics (orange part of the signal).
```

> How does one extract the properties of the binary black holes (e.g. the masses of the two BHs, their distance from us, etc.) from the data?

```{figure} ../images/astrocosmo/gw-first-detection.png
---
width: 70%
align: center
name: fig-gw-detection
---
LIGO measurement of gravitational waves at the Livingston (right) and Hanford (left) detectors, compared with theoretical predicted values.
```

To study the *inspiral phase*, we can use perturbation theory:

$$
g_{\mu \nu} = \bar{g}_{\mu \nu} + h_{\mu \nu}, \qquad \text{where} \quad |h_{\mu \nu}| \ll 1,
$$

where $\bar{g}_{\mu \nu}$ can be the Minkowski or FLRW metric, depending on whether we are studying binary systems on astrophysical or cosmological scales.

## Gravitational waves in cosmology

Gravitational waves play an increasingly important role in cosmology, with two main applications:

- **$H_0$ measurement**: by observing individual sources (e.g. binary black holes) on cosmological scales, we can independently measure the Hubble constant.
- **Stochastic Gravitational Wave Background (SGWB)**: analogous to the CMB for photons, this background carries information about the early universe. At high redshifts ($z \gg 5$), there are two main components:
    1. **Astrophysical components**: individual signals from many unresolved sources superpose to form a background.
    2. **Cosmological/primordial components**: originating from primordial sources in the early universe (e.g. inflation, phase transitions, cosmic strings).

```{important}
Due to the **weakness of gravitational interactions**, gravitons **decouple from the primordial plasma** from **$t_{\rm pl}$ onwards** — much earlier than photons (**$z \lesssim 1100$**).

Therefore, the **SGWB contains information about the primordial universe**, potentially revealing **physics at inaccessible energy scales**.
```

```{hint} Strong evidence for SGWB
:class: dropdown

In Summer 2023, pulsar timing array collaborations announced strong evidence for a stochastic gravitational wave background.

- Observation time: $T \sim 1$ yr
- Characteristic frequency: $f_{\mathrm{GW}} \sim 10^{-9}$ Hz
- Corresponding wavelength: $\lambda_{\mathrm{GW}} \sim \dfrac{c}{f_{\mathrm{GW}}} = \dfrac{3 \times 10^8 \,\mathrm{m/s}}{10^{-9}\,\mathrm{Hz}} \approx 10 \,\mathrm{pc}$

This opens a new window to test Grand Unified Theories (GUTs) and early universe physics.
```

# Order of magnitude estimates for black hole ringdown

During the ringdown phase, a perturbed black hole oscillates at characteristic complex frequencies (quasinormal modes):

$$
\omega = \omega_R + i \omega_I.
$$

- **Oscillation frequency**: for the fundamental mode ($l = 2, n = 0$):
  $$
  f = \frac{\omega_R}{2\pi} = \frac{c^3}{G_N M} \frac{1}{3\pi\sqrt{3}} \approx 12 \,\mathrm{kHz} \left( \frac{M_\odot}{M} \right).
  $$
  More generally, $f \propto 1/M$.

- **Decay time scale**: 
  $$
  \tau \sim \frac{1}{\omega_I} = 3\sqrt{3} \left( \frac{G_N M}{c^3} \right) \frac{1}{n + \frac{1}{2}},
  $$
  where $n$ is the overtone number. For the fundamental mode, $\tau \approx 0.55 \, \mathrm{ms} \, (M/M_\odot)$.


A summary of the key gravitational-wave observables for different detectors:

| Detector                   | $f_{\rm GW}$ (typical)      | $\tau$ (ringdown decay time) | Typical $M$                   |
| -------------------------- | --------------------------- | ---------------------------- | ----------------------------- |
| LVK (LIGO/Virgo/KAGRA)     | $\sim 10$–$10^3$ Hz         | $\sim 10^{-3}$–$10^{-2}$ s   | $\sim 10$–$100 M_\odot$       |
| LISA                       | $\sim 10^{-4}$–$10^{-1}$ Hz | $\sim 10^3$–$10^4$ s         | $\sim 10^6$–$10^9 M_\odot$    |
| PTA (Pulsar Timing Arrays) | $\sim 10^{-9}$–$10^{-7}$ Hz | $\sim 10^7$–$10^9$ s         | $\sim 10^9$–$10^{10} M_\odot$ |

:::{hint} First detection of a black hole ringdown
:class: dropdown

- By LVK (from GW150914) 
- Provided the first direct observation of the quasinormal modes predicted by general relativity. 
- Measuring the amplitudes and frequencies of these modes opens the possibility to test the Hawking area theorem: that the total horizon area after merger $A$ should satisfy $A \ge A_1 + A_2$. 
- While current LVK data are consistent with this bound, higher signal-to-noise detections of multiple ringdown modes in the future could provide a quantitative test of this fundamental prediction.
:::

## Detector types
- LVK and LISA are interferometers based on michael-son morley experiments. 
- Some explaination for michelson morley here. ....
$$
ds^2 = g_{\mu \nu}
$$