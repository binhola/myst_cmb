# Map-making

## Data Model
Suppose that the measured time-ordered data (TOD) has $n$ points $d_1, d_2, ..., d_n$ and *linearly* depends on the true sky signal of $s$ points $s_1, s_2, ..., s_m$. 
$$
\mathbf{d} = \mathbf{P} \mathbf{s} + \mathbf{n}
$$

The noise $\mathbf{n}$ is gaussian, stochastic with zero mean $\langle \mathbf{n} \rangle = 0$:
$$
\mathbf{N} = \langle \mathbf{n} \mathbf{n}^T \rangle
$$

The sky signal is described in term of *Stokes Parameters* represents the polarization state of the light. We can describe the way signal is measured by optical elements with the detector orientation $\varphi$ and half-wave plate rotation angle $\psi$. The standard CMB TOD model with one pixel per observation is:

$$
\underbrace{\begin{pmatrix} d_1 \\ d_2 \\ \vdots \\ d_{N_t} \end{pmatrix}}_{N_t \times 1}
=
\underbrace{\begin{pmatrix}
\mathbf{0} & \cdots & \mathbf{r}_1 & \cdots & \mathbf{0} \\
\mathbf{0} & \cdots & \mathbf{r}_2 & \cdots & \mathbf{0} \\
\vdots & & \vdots & & \vdots \\
\mathbf{0} & \cdots & \mathbf{r}_{N_t} & \cdots & \mathbf{0}
\end{pmatrix}}_{N_t \times 3N_p}
\underbrace{\begin{pmatrix} I_1 \\ Q_1 \\ U_1 \\ \vdots \\ I_{N_p} \\ Q_{N_p} \\ U_{N_p} \end{pmatrix}}_{3N_p \times 1},
$$

where $\mathbf{r}_t = \bigl(1,\; \cos(-2\varphi_t+4\psi_t),\; \sin(-2\varphi_t+4\psi_t)\bigr)$ is placed in the three columns corresponding to the pixel $p(t)$ observed at time $t$.

:::{prf:example} A 2-pixel universe
Imagine you are living in a 2-pixel universe. Given $N_t=5$, $N_p=2$

$$
\begin{pmatrix} d_1 \\ d_2 \\ d_3 \\ d_4 \\ d_5 \end{pmatrix}
=
\begin{pmatrix}
1 & \cos\theta_1 & \sin\theta_1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & \cos\theta_2 & \sin\theta_2 \\
1 & \cos\theta_3 & \sin\theta_3 & 0 & 0 & 0 \\
1 & \cos\theta_4 & \sin\theta_4 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & \cos\theta_5 & \sin\theta_5 
\end{pmatrix}
\begin{pmatrix} I_1 \\ Q_1 \\ U_1 \\ I_2 \\ Q_2 \\ U_2 \end{pmatrix},
$$

with $\theta_t = -2\varphi_t + 4\psi_t$.

**Assumptions**:

- HWP rotation frequency: $f_{\text{HWP}} = 2\ \text{Hz}$  
  → HWP angle $\varphi_t = 2\pi f_{\text{HWP}} t = 4\pi t$ (radians)
- Detector orientation: $\psi_t = 0^\circ$ (constant)
- Modulation angle: $\theta_t = -2\varphi_t + 4\psi_t = -8\pi t$
- Sampling times: $t = 0.1,\ 0.2,\ 0.3,\ 0.1,\ 0.5\ \text{s}$ (10 Hz sampling, one repeated sample)
- Stokes parameters:

$$
\begin{aligned}
\text{Pixel 1:}&\quad I_1 = 1.0,\; Q_1 = 0.5,\; U_1 = 0.3\\
\text{Pixel 2:}&\quad I_2 = 0.8,\; Q_2 = -0.2,\; U_2 = 0.4
\end{aligned}
$$

**Compute $\cos\theta_t$ and $\sin\theta_t$**

| $t$ (s) | $\theta_t = -8\pi t$ (rad) | $\cos\theta_t$ | $\sin\theta_t$ |
|-----------|-------------------------------|------------------|------------------|
| 0.1       | $-0.8\pi$                    | $-0.809017$    | $-0.587785$    |
| 0.2       | $-1.6\pi$                    | $0.309017$     | $0.951057$     |
| 0.3       | $-2.4\pi$                    | $0.309017$     | $-0.951057$    |
| 0.5       | $-4\pi$                      | $1$            | $0$            |

**Pointing matrix $\mathbf{P}$**

$$
\mathbf{P} =
\begin{pmatrix}
1 & -0.809017 & -0.587785 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0.309017 & 0.951057 \\
1 & 0.309017 & -0.951057 & 0 & 0 & 0 \\
1 & -0.809017 & -0.587785 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 1 & 0
\end{pmatrix}
$$

**Sky signal $\mathbf{s}$**

$$
\mathbf{s} = \begin{pmatrix} 1.0 \\ 0.5 \\ 0.3 \\ 0.8 \\ -0.2 \\ 0.4 \end{pmatrix}
$$

**Time-ordered data**

$$
d_1 &= 1\cdot1.0 + (-0.809017)\cdot0.5 + (-0.587785)\cdot0.3 \\
    &= 1.0 - 0.4045085 - 0.1763355 = 0.419156 \\
d_2 &= 1\cdot0.8 + 0.309017\cdot(-0.2) + 0.951057\cdot0.4 \\
    &= 0.8 - 0.0618034 + 0.3804228 = 1.1186194 \\
d_3 &= 1\cdot1.0 + 0.309017\cdot0.5 + (-0.951057)\cdot0.3 \\
    &= 1.0 + 0.1545085 - 0.2853171 = 0.8691914  \\
d_4 &= d_1 = 0.419156 \\
d_5 &= 1\cdot0.8 + 1\cdot(-0.2) + 0\cdot0.4 = 0.8 - 0.2 = 0.6.
$$

Thus the TOD vector is:

$$
\mathbf{d} = \begin{pmatrix} 0.4192 \\ 1.1186 \\ 0.8692 \\ 0.4192 \\ 0.6 \end{pmatrix}.
$$
:::

## Map-making
### Maximum Likelihood
If the noise is Gaussian with covariance $\mathbf{N}$, the maximum likelihood estimate of $\mathbf{s}$ is:

$$
\mathbf{\hat s} = (\mathbf{P}^T \mathbf{N}^{-1} \mathbf{P})^{-1} \mathbf{P}^T \mathbf{N}^{-1} \mathbf{d}
$$
:::{prf:proof} Maximum likelihood solution
:class: dropdown
The probability $p$ to find the sky signal $\mathbf{s}$ given data $\mathbf{d}$ under Bayes's theorem:
$$
p(\mathbf{s} \, | \, \mathbf{d}) = \dfrac{p(\mathbf{d} \, | \, \mathbf{s}) \, p(\mathbf{s})}{p\mathbf{(\mathbf{d})}}
$$

Assume that the prior on the sky signal $p(\mathbf{s})$ is uniform. The sky signal $\mathbf{s}$ and measured data $\mathbf{d}$ are deterministic so the probability depends on how we define the noise model. Let's assume it is gaussian noise.
$$
\chi^2 = -2 \ln p(\mathbf{s} \, | \, \mathbf{d}) = (\mathbf{d} - \mathbf{P} \mathbf{s})^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s})
$$

We want to maximize $p(\mathbf{s} \, | \, \mathbf{d})$ that means minimize $\chi^2$ with respect to $\mathbf{s}$:
$$
\dfrac{d \chi^2}{d \mathbf{s}} = -2 \mathbf{P}^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s})
$$

The optimal $\mathbf{\hat s}$ is at $\dfrac{d \chi^2}{d \mathbf{s}} = 0$:
$$
\mathbf{P}^T \mathbf{N}^{-1} \mathbf{P} \mathbf{\hat s} = \mathbf{P}^T \mathbf{N}^{-1} \mathbf{d} \\
\Rightarrow \qquad \boxed{\mathbf{\hat s} = (\mathbf{P}^T \mathbf{N}^{-1} \mathbf{P})^{-1}\mathbf{P}^T \mathbf{N}^{-1} \mathbf{d}}
$$
:::
:::{note}
- The maximum likelihood estimator is **unbiased** under correct model assumptions and provides an optimal (lossless in Fisher information) compression from TOD to map.
- However, computing the matrix inverse $(\mathbf{P}^T \mathbf{N}^{-1} \mathbf{P})^{-1}$ directly is *computationally infeasible* for realistic data sizes. In practice, the system is solved iteratively using methods like **conjugate gradient** without ever forming or inverting the matrix explicitly.
:::
### Binned map-making
In many CMB experiments, the noise is **uncorrelated** in time (white noise), so
$$
\mathbf{N} = \sigma^2 \mathbf{I}
$$
Then
$$
\mathbf{\hat s} = (\mathbf{P}^T \mathbf{P})^{-1} \mathbf{P}^T \mathbf{d}
$$

:::{note} Why "Binned" ?
:class: dropdown
If each time sample observes **only one pixel**, $\mathbf{P}^T \mathbf{P}$ is a block diagonal. Each $3 \times 3$ block for pixel $p$ is:
$$
\mathbf{A_p} = \sum_{t \, \in \, \text{hits of p}} \mathbf{r}_t^T \mathbf{r}_t
$$
where $r_t = \begin{pmatrix} 1 & \cos \theta_t & \sin \theta_t \end{pmatrix}$. And $\mathbf{P}^T \mathbf{d}$ gives a $3 \times 1$ vector for each pixel:
$$
\mathbf{b}_p = \sum_{t \, \in \, \text{hits of p}} \mathbf{r}^T_t \mathbf{d}_t
$$

The binned map for pixel $p$ is then:
$$
\mathbf{\hat s}_p = \mathbf{A}_p^{-1} \mathbf{b}_p
$$

We have binned the data and the pointing information into per‑pixel $3 \times 3$ matrices and $3 \times 1$ vector.

In the simplest case, if we ignore polarization (only $I$), then $\mathbf{r}_t = 1$ and:
$$
\hat I_p = \dfrac{\sum_{t \in p} d_t}{\text{number of hits in $p$}}
$$
which is just the **average** of all measurements that fell into pixel $p$. 
:::

:::{prf:example} Binned map-making in the 2-pixel universe
We continue with the same example. The TOD vector computed earlier is:

$$
\mathbf{d} = \begin{pmatrix} 0.419156 \\ 1.118619 \\ 0.869191 \\ 0.419156 \\ 0.6 \end{pmatrix}.
$$

The true Stokes parameters for the two pixels are:

$$
\text{Pixel 1: } &(I_1,Q_1,U_1) = (1.0,\; 0.5,\; 0.3), \\
\text{Pixel 2: } &(I_2,Q_2,U_2) = (0.8,\; -0.2,\; 0.4).
$$

We now apply **binned map‑making** to recover these parameters from $\mathbf{d}$ and the pointing information.

**Per‑Pixel Accumulation**

For each pixel $p$, we form:

$$
\mathbf{A}_p = \sum_{t \in \text{hits of } p} \mathbf{r}_t^T \mathbf{r}_t, \qquad
\mathbf{b}_p = \sum_{t \in \text{hits of } p} \mathbf{r}_t^T d_t,
$$

where $\mathbf{r}_t = (1,\cos\theta_t,\sin\theta_t)$ and $\theta_t = -8\pi t$ (radians).

**Pixel 1** (hits at $t = 0.1, 0.3, 0.4$)

- $t = 0.1$: $\mathbf{r} = (1,\,-0.809017,\,-0.587785)$, $d = 0.419156$  
- $t = 0.3$: $\mathbf{r} = (1,\,0.309017,\,-0.951057)$, $d = 0.869191$
- $t = 0.4$: $\mathbf{r} = (1,\,-0.809017,\,-0.587785)$, $d = 0.419156$

The accumulated $3\times3$ matrix $\mathbf{A}_1$ and vector $\mathbf{b}_1$ are:

$$
\mathbf{A}_1 =
\begin{pmatrix}
3 & -1.309017 & -2.126627 \\
-1.309017 & 1.404508 & 0.657163 \\
-2.126627 & 0.657163 & 1.595492
\end{pmatrix},
\qquad
\mathbf{b}_1 =
\begin{pmatrix}
1.707503 \\ -0.409800 \\ -1.319300
\end{pmatrix}.
$$

Solving $\mathbf{A}_1 \hat{\mathbf{m}}_1 = \mathbf{b}_1$ yields:

$$
\hat{\mathbf{m}}_1 = \begin{pmatrix} 1.0 \\ 0.5 \\ 0.3 \end{pmatrix},
$$

which exactly matches the true input (no noise case).

**Pixel 2** (hits at $t = 0.2, 0.5$)

- $t = 0.2$: $\mathbf{r} = (1,\,0.309017,\,0.951057)$, $d = 1.118619$  
- $t = 0.5$: $\mathbf{r} = (1,\,1,\,0)$, $d = 0.6$

$$
\mathbf{A}_2 =
\begin{pmatrix}
2 & 1.309017 & 0.951057 \\
1.309017 & 1.095492 & 0.293893 \\
0.951057 & 0.293893 & 0.904508
\end{pmatrix},
\qquad
\mathbf{b}_2 =
\begin{pmatrix}
1.718619 \\ 0.945673 \\ 1.063870
\end{pmatrix}.
$$

Solving gives:

$$
\hat{\mathbf{m}}_2 = \begin{pmatrix} 0.8 \\ -0.2 \\ 0.4 \end{pmatrix},
$$

again recovering the true values exactly.

Binned map‑making reproduces the input Stokes parameters perfectly in this noise‑free test. The algorithm only requires per‑pixel sums, avoiding the construction of the full pointing matrix. For white noise, this is the optimal minimum‑variance map.
:::

### POMME map-making
*Template-based* map-making model, where the template $\mathbf{T}$ is included for any noise that is not white noise (atmospheric, scan-synchronous, HWP)
$$
\mathbf{d} = \mathbf{P} \mathbf{s} + \mathbf{T} \mathbf{a} + \mathbf{n}
$$