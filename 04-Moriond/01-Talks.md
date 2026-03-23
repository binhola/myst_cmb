# Moriond Talks

## CMB Blind component separation - Alessandro
- ILC component separation $\to$ remove foreground
- Problems:
  - Complex spatial structure
  - Complex spectral structure

- Need a component separation with **minimal assumptions**.
  - ILC: minimize the *variance*, need the *covariance* of the data $$\mathbf{w} = [A_{CMB}^T C^{-1}A_{CMB}]^{-1} A_{CMB}^T C^{-1}$$
  - MultiClustering-ILC (MC-ILC) $\to$ improve the fit on the large scales.
  - Generalized-ILC $\to$ improve on the noise, fit for $F$ instead of A $$A = F + N $$

- Check the biases on different $r$ values and foreground models
- Include the template of foregrounds into likelihood.

- Broom packages 

- Blind detection of systematic residuals after component separation.

- Frontier?
  - Apply to SO data $\to$ transfer function. (some preliminary results)
  - Apply Broom to Planck data.

### Questions
- Why using templates ? Can not model statistically ? 
  - Alessandro: even using the templates it wouldn't leak into the variance ? 