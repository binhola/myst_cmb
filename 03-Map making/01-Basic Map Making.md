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

### Pomme map-making

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
**The broken symmetry.** Ordinary block-averaging is *not* time-translation invariant. If you shift the data by one sample, the block boundaries fall in different places, giving a different $\mathbf{D}_{\rm T}$​. In Fourier language this means $\mathbf{D}_{\rm T}$​ is not diagonal in the DFT basis — it couples nearby frequencies.
:::