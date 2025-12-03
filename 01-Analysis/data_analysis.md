# Parametric Component Separation

## Baye's theorem
Our objective is to determine the parameter set $\hat{\xi}$ for the Mueller matrix $\mathbf{A}(\hat{\xi})$ that maximises the probability of observing the data given a sky signal:

```{math}
:label: data_model
\mathbf{d} = \mathbf{A}(\hat{\xi}) \mathbf{s} + \mathbf{n}
```

From Bayes' theorem:

```{math}
:label: bayes_theorem
P(\mathbf{s}|\mathbf{d}) = \frac{P(\mathbf{d}|\mathbf{s}) P(\mathbf{s})}{P(\mathbf{d})}
```

where:
- $P(\mathbf{s}|\mathbf{d})$ denotes the posterior probability of recovering the original sky signal given the observable data
- $P(\mathbf{d}|\mathbf{s})$ represents the likelihood of obtaining the data given a sky signal
- $P(\mathbf{s})$ constitutes the prior probability of the sky signal
- $P(\mathbf{d})$ is the marginal likelihood or evidence

```{note} Bayesian Interpretation
:open:
Maximising the posterior probability addresses the question: "Given the observations, what is the most plausible model?" We seek $\hat{\xi}$ that maximises $\frac{P(\mathbf{d}|\mathbf{s}) P(\mathbf{s})}{P(\mathbf{d})}$. The term $P(\mathbf{d})$ may be neglected as it is independent of $\hat{\xi}$. Assuming a uniform prior for $P(\mathbf{s})$, the optimisation reduces to maximising the likelihood $P(\mathbf{d}|\mathbf{s})$.
```

## Maximum Likelihood Formalism
In our formulation, $\mathbf{A} \mathbf{s}$ is well-characterised, hence the likelihood probability depends solely on the noise probability $\mathcal{L}(\mathbf{n})$. Assuming the noise $\mathbf{n}$ added to the input maps follows a multivariate Gaussian distribution with zero mean and covariance $\mathbf{N} \equiv \langle \mathbf{n} \mathbf{n}^\top \rangle$:

```{math}
:label: gaussian_likelihood
\mathcal{L}(\mathbf{n}) = \mathcal{N}(0, \mathbf{N}) = \frac{1}{\sqrt{(2\pi)^k |\mathbf{N}|}} \exp\left(-\frac{1}{2}\mathbf{n}^\top\mathbf{N}^{-1}\mathbf{n}\right)
```

Taking the natural logarithm of both sides:

```{math}
:label: log_likelihood
\log \mathcal{L}(\mathbf{n}) = -\frac{1}{2}\mathbf{n}^\top\mathbf{N}^{-1}\mathbf{n} + \mathrm{const}
```

```{important} Likelihood Maximization
Maximising $\log \mathcal{L}(\mathbf{n})$ is equivalent to minimising:

```{math}
:label: negative_log_likelihood
-2\log \mathcal{L}(\mathbf{n}) = \mathbf{n}^\top\mathbf{N}^{-1}\mathbf{n} = (\mathbf{d}-\mathbf{A} \mathbf{s})^\top \mathbf{N}^{-1} (\mathbf{d}-\mathbf{A}\mathbf{s})
```

The optimal estimate of the sky signal, $\hat{\mathbf{s}}$, is obtained by minimising the log-likelihood function in Equation {eq}`negative_log_likelihood`, yielding the closed-form solution:

```{math}
:label: signal_solution
\hat{\mathbf{s}} = (\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A})^{-1} \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d}
```

```{note} Derivation of Optimal Signal Estimate
:open:
The solution is derived by minimising the negative log-likelihood:

\begin{equation}
\begin{aligned}
\hat{\mathbf{s}} &= \arg \min_{\mathbf{s}} -2 \log \mathcal{L} (\mathbf{n}) = \arg \min_{\mathbf{s}} (\mathbf{d}-\mathbf{A} \mathbf{s})^\top \mathbf{N}^{-1} (\mathbf{d}-\mathbf{A}\mathbf{s}) \\
&= \arg \min_\mathbf{s} 
\Big[
\mathbf{d}^\top\mathbf{N}^{-1}\mathbf{d} + \mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}\mathbf{s} - \mathbf{d}^\top\mathbf{N}^{-1}\mathbf{A}\mathbf{s} - \mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d} 
\Big]
\end{aligned}
\end{equation}

Assuming the noise $\mathbf{N} = \langle \mathbf{n} \mathbf{n}^\top \rangle$ is zero-mean and uncorrelated (white noise), $\mathbf{N}$ is symmetric. For a symmetric matrix $\mathbf{O}$ and arbitrary vector $\mathbf{m}$, $\mathbf{m}^\top \mathbf{O} = \mathbf{O} \mathbf{m}$, and the inverse of a symmetric matrix remains symmetric. Thus:

\begin{equation}
\hat{\mathbf{s}} = \arg \min_\mathbf{s} 
\Big[
\mathbf{d}^\top\mathbf{N}^{-1}\mathbf{d} + \mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}\mathbf{s} - 2\mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d} 
\Big]
\end{equation}

The minimum $\hat{\mathbf{s}}$ is found by setting the derivative of the log-likelihood to zero:

\begin{equation}
\begin{aligned}
&\frac{\partial}{\partial \mathbf{s}}
\Big[
\mathbf{d}^\top\mathbf{N}^{-1}\mathbf{d} + \mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}\mathbf{s} - 2\mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d} 
\Big] = 0 \\
&\Rightarrow \quad 2\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}\hat{\mathbf{s}} - 2 \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d} = 0 \\
&\Rightarrow \quad \hat{\mathbf{s}} = (\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A})^{-1} \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d}
\end{aligned}
\end{equation}
```

```{caution} Matrix Invertibility Condition
:open:
This solution requires that all columns of $\mathbf{A}$ are linearly independent, meaning $\mathbf{A}$ has full column rank. Consequently, $\mathrm{rank}(\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}) = \mathrm{rank}(\mathbf{A})
$, ensuring the invertibility of $\mathbf{A}^\top \mathbf{N}^{-1} \mathbf{A}$.
```

## Spectral Likelihood
Substituting $\hat{\mathbf{s}}$ into the second term of $-2\log\mathcal{L}(\mathbf{n})$:

```{math}
:label: substitution
\mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}\mathbf{s} = \mathbf{s}^\top (\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A}) (\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A})^{-1}\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{d} = \mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1} \mathbf{d}
```

Thus,

```{math}
:label: simplified_negative_log_likelihood
-2\log\mathcal{L}(\mathbf{n}) = \mathbf{d}^\top\mathbf{N}^{-1}\mathbf{d} - \mathbf{s}^\top \mathbf{A}^\top \mathbf{N}^{-1} \mathbf{d}
```

```{important} Spectral Likelihood
Since $\mathbf{d}^\top\mathbf{N}^{-1}\mathbf{d}$ is constant, it may be neglected in the likelihood minimisation:

```{math}
:label: spectral_likelihood
-2\log\mathcal{L}(\mathbf{n}) = -\mathbf{d}^\top \mathbf{N}^{-1} \mathbf{A} (\mathbf{A}^\top \mathbf{N}^{-1}\mathbf{A})^{-1} \mathbf{A}^\top \mathbf{N}^{-1} \mathbf{d}
```

This expression constitutes the *spectral likelihood*.

```{caution} Square Matrix Limitation
:open:
Note that if $\mathbf{A}$ possesses full column rank and is additionally a square matrix, then $\mathbf{A}$ becomes invertible. In such cases, the spectral likelihood approach would not be advantageous.
```