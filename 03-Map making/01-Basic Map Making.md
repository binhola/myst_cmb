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
Map-making is an inverse problem because we reconstruct a 2D sky map $\mathbf{s}$ from a 1D noisy time stream $\mathbf{d}$, using knowledge of how the telescope projects the sky through the pointing operator $\mathbf{P}$.

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
If the noise is **uncorrelated** in time (white noise)
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

#### Template map-making
*Template-based* map-making model, where the template $\mathbf{T}$ accounts for any non-white noise contributions (e.g. atmospheric noise, scan-synchronous signals, HWP systematics and non-idealities):
$$
\mathbf{d} = \mathbf{P} \mathbf{s} + \mathbf{T} \mathbf{a} + \mathbf{n}
$$

The corresponding maximum-likelihood solution is
$$
\mathbf{\hat s} = (\mathbf{P}^T \mathbf{N}^{-1} \mathbf{D}_{\rm T} \mathbf{P})^{-1} \mathbf{P}^T \mathbf{N}^{-1} \mathbf{D}_{\rm T} \mathbf{d}
$$

where the operator
$$
\mathbf{D}_{\rm T} = \mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}
$$
projects out the template subspace.

:::{prf:proof} template maximum likelihood solution
:class: dropdown
Following the same approach as before, define the quadratic form
$$
\chi^2 = (\mathbf{d} - \mathbf{P} \mathbf{s} - \mathbf{T} \mathbf{x})^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s} - \mathbf{T} \mathbf{x})
$$
We minimize $\chi^2$ with respect to both $\mathbf{s}$ and $\mathbf{x}$.

Taking the derivative with respect to $\mathbf{s}$:
$$
\dfrac{d \chi^2}{d \mathbf{s}} = - 2 \mathbf{P}^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s} - \mathbf{T} \mathbf{x})
$$

Setting this to zero gives
$$
\mathbf{P}^T \mathbf{N}^{-1} \mathbf{P} \, \mathbf{\hat s} = \mathbf{P}^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{T} \mathbf{x})
$$

Next, take the derivative with respect to $\mathbf{x}$:
$$
\dfrac{d \chi^2}{d \mathbf{x}} = - 2 \mathbf{T}^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s} - \mathbf{T} \mathbf{x})
$$

Setting this to zero yields
$$
\mathbf{\hat x} =  (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1}  \mathbf{T}^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s})
$$

Substituting $\mathbf{\hat x}$ into the equation for $\mathbf{\hat s}$:
$$
\mathbf{P}^T \mathbf{N}^{-1} \mathbf{P} \, \mathbf{\hat s} &= \mathbf{P}^T \mathbf{N}^{-1} \left[\mathbf{d} -  \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1}  \mathbf{T}^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s}) \right] \\
\mathbf{P}^T \mathbf{N}^{-1} \underbrace{[\mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}]}_{\mathbf{D}_{\rm T}} \mathbf{P} \, \mathbf{\hat s} &= \mathbf{P}^T \mathbf{N}^{-1} \underbrace{[\mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}]}_{\mathbf{D}_{\rm T}} \mathbf{d} \\
\mathbf{P}^T \mathbf{N}^{-1} \mathbf{D}_{\rm T} \mathbf{P} \, \mathbf{\hat s} &= \mathbf{P}^T \mathbf{N}^{-1} \mathbf{D}_{\rm T} \mathbf{d}
$$

Thus, the solution is
$$
\boxed{\mathbf{\hat s} = (\mathbf{P}^T \mathbf{N}^{-1} \mathbf{D}_{\rm T} \mathbf{P})^{-1} \mathbf{P}^T \mathbf{N}^{-1} \mathbf{D}_{\rm T} \mathbf{d}}
$$
with the **deprojection operator**
$$
\mathbf{D}_{\rm T} = \mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}.
$$

If we include a Gaussian prior on $\mathbf{x}$ with covariance $\mathbf{X} = \langle \mathbf{x} \mathbf{x}^T\rangle$, the quadratic form becomes
$$
\chi^2 = (\mathbf{d} - \mathbf{P} \mathbf{s} - \mathbf{T} \mathbf{x})^T \mathbf{N}^{-1} (\mathbf{d} - \mathbf{P} \mathbf{s} - \mathbf{T} \mathbf{x}) + \mathbf{x}^T \mathbf{X}^{-1} \mathbf{x}
$$

Following the same procedure, the solution is unchanged except that
$$
\mathbf{D}_{\rm T} = \mathbf{I} - \mathbf{T} (\textcolor{red}{\mathbf{X}^{-1}} + \mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}.
$$
:::

:::{note} Deprojection operator
:class:dropdown
- The operator $\mathbf{D}_{\rm T}$ is called a **deprojection operator** because it projects any vector onto the subspace orthogonal to the templates $\mathbf{T}$ (with respect to the $\mathbf{N}^{-1}$-weighted inner product).  
- To see this explicitly, apply $\mathbf{D}_{\rm T}$ to the data:
$$
\mathbf{D}_{\rm T} \mathbf{d} = [\mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}] (\mathbf{P} \mathbf{s} + \mathbf{T} \mathbf{a} + \mathbf{n}) 
$$

    Focusing on the template contribution $\mathbf{T}\mathbf{a}$, we obtain
$$
&[\mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} \mathbf{T}^T \mathbf{N}^{-1}] \mathbf{T} \mathbf{a} \\
= \quad & \mathbf{T} \mathbf{a} - \mathbf{T} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T})^{-1} (\mathbf{T}^T \mathbf{N}^{-1} \mathbf{T}) \mathbf{a} \\
= \quad & 0
$$

- Therefore, all components lying in the template subspace are removed:
$$
\mathbf{D}_{\rm T} \mathbf{T} = 0
$$

- As a result, $\mathbf{D}_{\rm T}\mathbf{d}$ contains no contribution from the templates, i.e.
$$
\mathbf{T}^T \mathbf{N}^{-1} (\mathbf{D}_{\rm T} \mathbf{d}) = 0
$$
which confirms that the cleaned data is orthogonal to $\mathbf{T}$.
:::

#### POMME
Pomme is a simple version of template map-making, with a set of templates chosen to capture all unpolarised signals that vary slowly over time. The template matrix T adopted in POMME comprises columns with elements spanning a fixed interval of length $\tau$ set to 1, and all other elements vanishing, i.e.,
$$
\mathbf{T}_{t}^{(i)} = \begin{cases}
    &1 \qquad i \tau \leq t <(i + 1) \tau \\
    &0 \qquad \text{otherwise}
\end{cases}
$$

By this definition, we can write
$$
\mathbf{D}_{\rm T} = \mathbf{I} - \mathbf{T} (\mathbf{T}^T \mathbf{T})^{-1} \mathbf{T}^T = \mathbf{I} - \dfrac{1}{\tau} \mathbf{J}
$$

where $J$ is a block-diagonal matrix that consists of $\tau \times \tau$ all-ones matrix blocks $\mathbf{J}_\tau$. 

$\mathbf{D}_{\rm T}$ subtracts the sample mean evaluated at every $\tau$-interval
$$
(\mathbf{D}_{\rm T} \, \mathbf{d})_t = d_t - \dfrac{1}{\tau} \sum_{s = i \tau}^{(i+1) \tau - 1} d_s
$$

:::{prf:proof} $\mathbf{D}_{\rm T}$ simplification
:class: dropdown
With white noise $\mathbf{N} = \sigma^2\mathbf{I}$, the deprojection operator is:
$$\mathbf{D}_T = \mathbf{I} - \mathbf{T}(\mathbf{T}^T\mathbf{T})^{-1}\mathbf{T}^T$$

The POMME template matrix $\mathbf{T}$ has one column per block, with 1s in the block's rows and 0s elsewhere. Label the blocks $i = 0, 1, \ldots, B-1$, each of length $\tau$. Then:

$$\mathbf{T} = \begin{pmatrix} \mathbf{1}_\tau & \mathbf{0} & \cdots & \mathbf{0} \\ \mathbf{0} & \mathbf{1}_\tau & \cdots & \mathbf{0} \\ \vdots & & \ddots & \vdots \\ \mathbf{0} & \cdots & & \mathbf{1}_\tau \end{pmatrix} \in \mathbb{R}^{N_t \times B}$$

where $\mathbf{1}_\tau$ is a column of $\tau$ ones.

**Step 1: compute $\mathbf{T}^T\mathbf{T}$** 

The $(i,j)$ entry is $\mathbf{T}^{(i)\,T}\mathbf{T}^{(j)}$. The blocks have disjoint support, so:
$$(\mathbf{T}^T\mathbf{T})_{ij} = \mathbf{1}_\tau^T \mathbf{1}_\tau \,\delta_{ij} = \tau\,\delta_{ij}$$
$$\Rightarrow \quad \mathbf{T}^T\mathbf{T} = \tau\,\mathbf{I}_B, \qquad (\mathbf{T}^T\mathbf{T})^{-1} = \frac{1}{\tau}\mathbf{I}_B$$
```{prf:example}
Let $\tau = 2$ 
$$
\mathbf{T} = \begin{pmatrix}
    1 & 0 \\
    1 & 0 \\
    0 & 1 \\
    0 & 1 \\
\end{pmatrix} \qquad  \mathbf{T}^{T} = \begin{pmatrix}
    1 & 1 & 0 & 0 \\
    0 & 0 & 1 & 1 \\
\end{pmatrix}
$$
Then 
$$
\mathbf{T}^T \mathbf{T} = \begin{pmatrix}
    2 & 0 \\
    0 & 2
\end{pmatrix} = 2 \, \mathbf{I}_{2 \times 2}
$$
```
**Step 2: compute $\mathbf{T}(\mathbf{T}^T\mathbf{T})^{-1}\mathbf{T}^T$** 

Substituting:
$$\mathbf{T}(\mathbf{T}^T\mathbf{T})^{-1}\mathbf{T}^T = \frac{1}{\tau}\mathbf{T}\mathbf{T}^T$$

Now compute $\mathbf{T}\mathbf{T}^T$. Its $(t, t')$ entry is:
$$(\mathbf{T}\mathbf{T}^T)_{tt'} = \sum_i T_{ti} T_{t'i} = \begin{cases} 1 & \text{if } t, t' \text{ are in the same block} \\ 0 & \text{otherwise} \end{cases}$$

This is exactly the block-diagonal matrix with $\tau\times\tau$ all-ones blocks $\mathbf{J}_\tau$:
$$\mathbf{T}\mathbf{T}^T = \mathbf{J} := \mathrm{diag}(\mathbf{J}_\tau, \mathbf{J}_\tau, \ldots, \mathbf{J}_\tau)$$

```{prf:example}
$$
\mathbf{T} \mathbf{T}^T = \begin{pmatrix}
    1 & 1 & 0 & 0 \\
    1 & 1 & 0 & 0 \\    
    0 & 0 & 1 & 1 \\   
    0 & 0 & 1 & 1 \\
\end{pmatrix}
$$
```
**Step 3:**
$$\boxed{\mathbf{D}_T = \mathbf{I} - \frac{1}{\tau}\mathbf{J}}$$

The action on any vector $\mathbf{v}$ is:
$$(\mathbf{D}_T\mathbf{v})_t = v_t - \frac{1}{\tau}\sum_{t' \in \text{block}(t)} v_{t'} = v_t - \bar{v}_{\text{block}(t)}$$

confirming that $\mathbf{D}_T$ is a **block-wise mean subtraction operator**. $\blacksquare$

```{prf:example}
Given
$$
\mathbf{d} = \begin{pmatrix}
    1 \\ 2 \\ 3 \\4
\end{pmatrix}
$$
We have
$$
\mathbf{D}_T \mathbf{d} = \mathbf{d} - \dfrac{1}{\tau} \begin{pmatrix}
    3 \\ 3 \\ 7 \\ 7
\end{pmatrix}
$$
```
:::

:::{important} Fourier representation of $\mathbf{D}_{\rm T}$
**The broken symmetry.** Ordinary block-averaging is *not* time-translation invariant. If you shift the data by one sample, the block boundaries fall in different places, giving a different $\mathbf{D}_{\rm T}$​. In Fourier language this means $\mathbf{D}_{\rm T}$​ is not diagonal in the DFT basis, it couples frequencies that belong to the same *aliasing class.
:::

#### Fourier representation of the deprojection operator
Define the Discrete Fourier Transform (DFT) matrix  

$$
F_{kt} = \frac{1}{\sqrt{N}}\, e^{-2\pi i\, k t / N}, \qquad k,t = 0,\dots,N-1,
$$

and the transformed operator  

$$
\tilde{\mathbf{D}}_{\rm T} = \mathbf{F}\,\mathbf{D}_{\rm T}\,\mathbf{F}^{\dagger}.
$$

The matrix elements of $\tilde{\mathbf{D}}_{\rm T}$ are:

$$
(\tilde{\mathbf{D}}_{\rm T})_{kk'} = 
\begin{cases}
1 - \dfrac{|C_k|^2}{\tau^2}, & k = k', \\[6pt]
-\,\dfrac{C_k C_{k'}^*}{\tau^2}, & k \equiv k' \pmod{B},\; k'\neq k, \\[6pt]
0, & \text{otherwise},
\end{cases}
$$

where $B = N/\tau$ is the number of blocks, and the frequency‑dependent factor $C_k$ is given by

$$
C_k = \sum_{s=0}^{\tau-1} e^{-2\pi i\, k s / N}
    = e^{-\pi i\, k (\tau-1)/N}\; \frac{\sin(\pi k\tau/N)}{\sin(\pi k/N)}.
$$

The magnitude is
$$
|C_k| = \left|\frac{\sin(\pi k\tau/N)}{\sin(\pi k/N)}\right|.
$$
<!-- Frequencies $k$ and $k'$ that differ by a multiple of $B$ (i.e. $k' = k + mB$) belong to the same *aliasing class* and are coupled by $\mathbf{D}_{\rm T}$.  This coupling is a direct consequence of the broken time‑translation invariance. -->

:::{prf:proof} Full derivation of $(\tilde{\mathbf{D}}_{\rm T})_{kk'}$
:class:dropdown
We start from $\mathbf{D}_{\rm T} = \mathbf{I} - \frac{1}{\tau}\mathbf{J}$, with $\mathbf{J}_{tt'}=1$ if $t$ and $t'$ lie in the same block and $0$ otherwise.  Then

$$
(\tilde{\mathbf{D}}_{\rm T})_{kk'} = \delta_{kk'} - \frac{1}{\tau}\,(\mathbf{F}\mathbf{J}\mathbf{F}^{\dagger})_{kk'}.
$$

We need $(\mathbf{F}\mathbf{J}\mathbf{F}^{\dagger})_{kk'}$.  Write $t = b\tau + s$, $t' = b\tau + s'$ where:
- $b = 0,1,\dots,B-1$ (block index),  
- $s,s' = 0,\dots,\tau-1$ (position inside the block).

Because $J_{tt'}=1$ only when $t$ and $t'$ are in the same block (same $b$), we have

$$
(\mathbf{F}\mathbf{J}\mathbf{F}^{\dagger})_{kk'}
= \frac{1}{N}\sum_{b=0}^{B-1}\sum_{s=0}^{\tau-1}\sum_{s'=0}^{\tau-1}
  e^{-2\pi i\,k(b\tau+s)/N}\; e^{2\pi i\,k'(b\tau+s')/N}.
$$

Factor the exponentials:

$$
= \frac{1}{N}
   \underbrace{\left(\sum_{b=0}^{B-1} e^{-2\pi i\,(k'-k)b\tau/N}\right)}_{\displaystyle \text{aliasing structure } A}
   \underbrace{\left(\sum_{s=0}^{\tau-1} e^{-2\pi i\,k s/N}\right)}_{\displaystyle \text{frequency response } C_k}
   \underbrace{\left(\sum_{s'=0}^{\tau-1} e^{2\pi i\,k' s'/N}\right)}_{\displaystyle C_{k'}^*}.
$$

Since $\tau/N = 1/B$, the exponent in $A$ becomes $-2\pi i\,(k'-k)b/B$.  Thus

$$
A = \sum_{b=0}^{B-1} e^{-2\pi i\,(k'-k)b/B}.
$$

This is a geometric series.  Write $k'-k = qB + r$ with $q,r\in\mathbb{Z}$ and $r\equiv (k'-k)\bmod B$, $0\le r<B$.  Then

$$
e^{-2\pi i\,(k'-k)b/B} = e^{-2\pi i\,(qB+r)b/B} = e^{-2\pi i\,q b}\, e^{-2\pi i\, r b/B} = e^{-2\pi i\, r b/B},
$$

because $e^{-2\pi i q b}=1$.  Hence

$$
A = \sum_{b=0}^{B-1} e^{-2\pi i\, r b/B}.
$$

- If $r=0$ (i.e. $k'\equiv k\pmod{B}$), each term is $1$, so $A = B$.
- If $r\neq 0$, the sum is a geometric series with ratio $\rho = e^{-2\pi i r/B}$.  Its value is

$$
A = \frac{1-\rho^{B}}{1-\rho} = \frac{1-e^{-2\pi i r}}{1-\rho} = 0,
$$

because $e^{-2\pi i r}=1$.

Thus

$$
A = \begin{cases}
B, & k'\equiv k\pmod{B},\\[2pt]
0, & \text{otherwise}.
\end{cases}
$$

Therefore $(\mathbf{F}\mathbf{J}\mathbf{F}^{\dagger})_{kk'}$ is non‑zero only when $k'\equiv k\pmod{B}$, and in that case

$$
(\mathbf{F}\mathbf{J}\mathbf{F}^{\dagger})_{kk'} = \frac{B}{N}\,C_k C_{k'}^* = \frac{C_k C_{k'}^*}{\tau}.
$$

Substituting back gives  

$$
(\tilde{\mathbf{D}}_{\rm T})_{kk'} = \delta_{kk'} - \frac{1}{\tau}\cdot\frac{C_k C_{k'}^*}{\tau}
= \delta_{kk'} - \frac{C_k C_{k'}^*}{\tau^2}.
$$

Separating the diagonal ($k=k'$) and off‑diagonal ($k'\equiv k\bmod B$, $k'\neq k$) parts yields the stated result.
:::

:::{prf:proof} Full derivation of $C_k$
:class:dropdown
We have

$$
C_k = \sum_{s=0}^{\tau-1} e^{-2\pi i\, k s / N}.
$$

This is again a geometric series.  Write $\omega = e^{-2\pi i k/N}$.  Then

$$
C_k = \sum_{s=0}^{\tau-1} \omega^s = \frac{1-\omega^\tau}{1-\omega},
$$

provided $\omega\neq 1$ (i.e. $k$ not a multiple of $N$; the case $k=0$ is treated separately).  Now

$$
\omega^\tau = e^{-2\pi i k\tau/N}, \qquad 1-\omega = 1-e^{-2\pi i k/N}.
$$

Factor out half‑exponentials to obtain the sine form:

$$
1-\omega^\tau = e^{-\pi i k\tau/N}\left(e^{\pi i k\tau/N} - e^{-\pi i k\tau/N}\right)
= e^{-\pi i k\tau/N}\, 2i\sin(\pi k\tau/N),
$$

$$
1-\omega = e^{-\pi i k/N}\left(e^{\pi i k/N} - e^{-\pi i k/N}\right)
= e^{-\pi i k/N}\, 2i\sin(\pi k/N).
$$

Therefore

$$
C_k = \frac{e^{-\pi i k\tau/N}\, 2i\sin(\pi k\tau/N)}{e^{-\pi i k/N}\, 2i\sin(\pi k/N)}
= e^{-\pi i k (\tau-1)/N}\; \frac{\sin(\pi k\tau/N)}{\sin(\pi k/N)}.
$$

For $k=0$ (or $k$ multiple of $N$), the expression is understood as the limit $k\to0$, which gives $C_0 = \tau$.  
:::

:::{note}
The condition $k'\equiv k\pmod{B}$ defines the **aliasing class**:
$$
\{k,\; k\pm B,\; k\pm 2B,\; \dots\}.
$$

Frequencies within the same class are coupled by $\mathbf{D}_{\rm T}$.  This coupling arises because the block‑averaging filter is not translation‑invariant.
:::

#### What does $\mathbf{D}_{\rm T}$ do to the power spectrum?
The TOD noise is $\mathbf{n}$ with power spectrum $P_k = \langle |\hat n_k|^2 \rangle$. For $1/f$ noise:
$$
P_k = \sigma^2 \left[ 1 + \left( \dfrac{f_{\rm knee}}{f_k} \right)^\alpha \right], \qquad f_k = \dfrac{k}{N} \cdot f_s
$$

We apply the filter to the noise:
$$
\hat n_k^{\rm out} = \sum_{k'} (\mathbf{\tilde D}_{\rm T})_{kk'} \hat n_{k'}
$$

The power at frequency $k$ is then
$$
\langle |\hat n_k^{\rm out}|^2 \rangle = \sum_{k'} \sum_{k''} (\mathbf{\tilde D}_{\rm T})_{kk'} (\mathbf{\tilde D}_{\rm T})_{kk''}^* \langle n_{k'} n_{k''}^*\rangle
$$

For stationary noise, $\langle n_{k'} n_{k''}^*\rangle = P_{k'} \delta_{k' k''}$. Therefore,
$$
P_{k}^{\rm deproj} = \sum_{k'} |(\mathbf{\tilde D}_{\rm T})_{kk'}|^2 \cdot P_{k'}
$$

The output power at frequency $k$ is **not** simply $|(\mathbf{\tilde D}_{\rm T})_{kk}|^2 \cdot P_{k}$; it also receives contributions from all $k'$ in the same aliasing class.

We now separate the diagonal and off-diagonal contributions:
$$
P_{k}^{\rm deproj} &=\sum_{k': k' \equiv k} \left| \delta_{k k'} - \dfrac{C_k C_{k'}^*}{\tau^2} \right|^2 \cdot P_{k'} \\
P_{k}^{\rm deproj} &= \underbrace{\left( 1 - \dfrac{|C_k|^2}{\tau^2} \right)^2 P_{k}}_{\text{filter term}} + \underbrace{\sum_{\substack{k' \equiv k \ \mathrm{mod}\ B \\ k' \neq k}} \dfrac{|C_k|^2 |C_{k'}|^2}{\tau^4} P_{k'}}_{\text{leakage term}}
$$

The first term describes the attenuation of frequency $k$ (a high-pass filtering effect).

The second term represents the leakage of power from the other members of the same aliasing class.

If the noise is white ($P_{k'} = \sigma^2$ for all $k'$), the leakage term simplifies:
$$
\left.P_k^{\text {deproj }}\right|_{\text {white }}=\sigma^2\left[\left(1-\frac{\left|C_k\right|^2}{\tau^2}\right)^2+\frac{\left|C_k\right|^2}{\tau^4} \sum_{\substack{k' \equiv k \ \mathrm{mod}\ B \\ k' \neq k}}\left|C_{k^{\prime}}\right|^2\right]
$$

Using Parseval’s identity within the aliasing class,
$$
\sum_{k' \equiv k \text{ mod } B} |C_{k'}|^2 = \tau N / B = \tau^2
$$
we obtain
$$
\left.P_k^{\text {deproj }}\right|_{\text {white }}=\sigma^2\left(1-\frac{\left|C_k\right|^2}{\tau N}\right)
$$

This reduces to a purely diagonal filter. For white noise, the projection operator does not produce any leakage (since all members of the aliasing class have the same power, the contributions cancel out).

For $1/f$ noise, however, the low-frequency members of each aliasing class carry more power, and this excess power leaks into higher frequencies.