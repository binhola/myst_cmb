---
bibliography:
  - references.bib
---

# Instrumental Models

## Jones Vector and Polarization States

Starting with the Maxwell's equation of electromagnetism in the vacuum without any charges or currents:

```{math}
:label: eq:maxwell1
\nabla \cdot \mathbf{E} &= 0
```

```{math}
:label: eq:maxwell2
\nabla \cdot \mathbf{B} &= 0
```

```{math}
:label: eq:maxwell3
\nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t}
```

```{math}
:label: eq:maxwell4
\nabla \times \mathbf{B} &= \frac{1}{c^2} \frac{\partial \mathbf{E}}{\partial t}
```

These four equations can be reduced into the wave equation for $\mathbf{E}$ and $\mathbf{B}$:

```{math}
:label: eq:waveE
\nabla^2 \mathbf{E} = \frac{1}{c^2} \frac{\partial^2 \mathbf{E}}{\partial t^2} \quad \quad
\nabla^2 \mathbf{B} = \frac{1}{c^2} \frac{\partial^2 \mathbf{B}}{\partial t^2}
```

This means that each component ($x , y, z$) of $\mathbf{E}$ and $\mathbf{B}$ also satisfies the scalar wave equation, for example, $E_x(\mathbf{r},t)$ can be expressed as:

```{math}
:label: eq:scalarWave
\nabla^2 E_x(x,y,z,t) - \frac{1}{c^2} \frac{\partial E_x(x,y,z,t)}{\partial t^2} = 0
```

The separation solution for each component can be represented in a plane wave expression:

```{math}
:label: eq:planeWave
E_x(\mathbf{r}) = A_x e^{i(\mathbf{k \cdot r} - \omega t)}
```

We note that similar equations hold for $E_y$, $E_z$, $B_x$, $B_y$, $B_z$.

Assuming that an electromagnetic field propagates in the $z$-direction, which means $A_z = 0$ and the field oscillates in the $xy$-plane. Polarization is the direction of oscillation, which can be characterized by a two-dimensional **Jones vector**:

```{math}
:label: eq:jonesVector
J = \begin{bmatrix}
A_x \\
A_y
\end{bmatrix}
```

where $A_x$ and $A_y$ are independent complex-valued amplitudes, defining the state of polarization.  
We can present some simple polarization states, for instance: horizontal linear polarization $J = \begin{bmatrix} 1 \\ 0 \end{bmatrix}$, vertical linear polarization $J = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$, left circular polarization $J = \begin{bmatrix} 1 \\ i \end{bmatrix}$.

## Jones matrices and Manipulating polarization states

How can we manipulate the polarization state of a light beam? In reality, we will use optical elements:

- **Polarizer**: setting the amplitude of one component to 0.
- **Wave plate**: introducing a phase shift between two components by birefringence.

Mathematically, we can describe the changing of $2 \times 1$ Jones vector by $2 \times 2$ Jones matrices.

### Polarizers

A horizontal or vertical polarizer transmits the corresponding field component and blocks the other. The Jones matrices can be described as:

```{math}
:label: eq:horizPolarizer
\text{Horizontal polarizer:} \quad
\begin{bmatrix}
1 & 0 \\
0 & 0
\end{bmatrix} \begin{bmatrix}
A_x \\ A_y
\end{bmatrix} = \begin{bmatrix}
A_x \\ 0
\end{bmatrix}
```

```{math}
:label: eq:vertPolarizer
\text{Vertical polarizer:} \quad
\begin{bmatrix}
0 & 0 \\
0 & 1
\end{bmatrix} \begin{bmatrix}
A_x \\ A_y
\end{bmatrix} = \begin{bmatrix}
0 \\ A_y
\end{bmatrix}
```

In general, a linear polarized field with field amplitude $E_0$ can be represented as:

```{math}
:label: eq:linearPol
\begin{bmatrix}
A_x \\ A_y
\end{bmatrix}
= E_0 \begin{bmatrix}
\cos(\theta) \\
\sin(\theta)
\end{bmatrix}
```

The intensity of an electric field is given by the square of its magnitude:

```{math}
:label: eq:intensity
I = |\mathbf{E}^2| = |E_x^2| + |E_y^2| + |E_z^2|
```

Before a linear polarized field goes through a polarizer, the intensity can be expressed as:

```{math}
:label: eq:Iin
I_{\rm in} = |\mathbf{E}^2| = E_0^2
```

If we send a linear polarized field through a horizontal polarizer, the amplitude of the $y$-component becomes 0, so the intensity will become:

```{math}
:label: eq:malus
I_{\rm out} = E_0^2 \cos^2(\theta) = I_0 \cos^2(\theta)
```

This is **Malus's law**.

### Wave plates

Wave plates contain birefringent materials that introduce different refractive indices on each component of the electromagnetic field, meaning that when light propagates through such a medium with the same thickness $d$, the two field components $E_x$ and $E_y$ see different phase shifts $e^{ikn d}$ described by the Jones matrix:

```{math}
:label: eq:waveplateMatrix
\begin{bmatrix}
e^{ikn_x d} & 0 \\
0 & e^{ikn_y d}
\end{bmatrix}
\begin{bmatrix}
A_x \\ A_y
\end{bmatrix}
```

What we care about is the phase difference between $A_x$ and $A_y$, so we can ignore the global phase factoring out from the Jones matrix as it is irrelevant:

```{math}
:label: eq:phaseDiff
e^{ikn_x d} \begin{bmatrix}
1 & 0 \\
0 & e^{ik(n_x - n_y)d}
\end{bmatrix}
\longrightarrow
\begin{bmatrix}
1 & 0 \\
0 & e^{ik\Delta n d}
\end{bmatrix}
```

Setting values for $k$, $\Delta n$ and $d$ can be done by changing the birefringent materials or the thickness $d$. For example, to convert a linearly polarized light to circularly polarized light, we can use this Jones matrix:

```{math}
:label: eq:quarterWave
\text{Quarter wave plate:} \quad
\begin{bmatrix}
1 & 0 \\
0 & i
\end{bmatrix}
\begin{bmatrix}
1 \\ 1
\end{bmatrix}
= \begin{bmatrix}
1 \\ i
\end{bmatrix}
```

We call such a wave plate the **quarter wave plate** because $i = e^{i\frac{\pi}{2}}$ where $\frac{\pi}{2}$ is a quarter of $2\pi$, analogous to rotating a quarter of a circle or shifting a quarter of one full wave oscillation. Similarly, a **half-wave plate** introduces a phase of $\pi$, which has been used in the new generation of CMB experiments as a polarization modulator:

```{math}
:label: eq:halfWave
\text{Half wave plate:} \quad
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\begin{bmatrix}
1 \\ 1
\end{bmatrix}
= \begin{bmatrix}
1 \\ -1
\end{bmatrix}
```

So the half-wave plate mirrors the polarization vector about the $x$-axis. By rotating the wave plate, the polarization vector can be mirrored around any axis, so a half-wave plate can be used to arbitrarily rotate the direction of linearly polarized light without loss of intensity.

## Stokes parameters

### Coherency

In a very famous Young's double-slit experiment which shows the wave nature of light, people usually use a laser beam which is monochromatic light instead of using ordinary sunlight or a normal flashlight. Why? Because those light sources do not generate any interference fringes (or not as clearly as the case of the laser beam). This fact leads us to the conclusion that not all light reveals its polarized nature, for some types of light, no matter which wave plate or polarizer you use, in all cases 50% of all light will be transmitted.

The polarization depends on the degree of coherence: the more coherent (like a laser beam) the more possibility that interference can happen. This could be explained by phase fluctuation and because the phase difference varies rapidly with time, we can only observe the time-average. Mathematically, we describe the degree of coherence using time-average correlation between two field components:

```{math}
:label: eq:coherence
\langle E_x(t)^* E_y(t) \rangle
```

By taking the complex conjugate of $E_x$, we are looking at the phase difference between $E_x$ and $E_y$:

```{math}
:label: eq:phaseDiffCorr
E_x(t)^* E_y(t) = |E_x(t)||E_y(t)|e^{i(\phi_x(t)-\phi_y(t))} = |E_x(t)||E_y(t)|e^{i(\Delta \phi)}
```

If the phase difference $\Delta \phi$ fluctuates randomly, the time average of the correlation converges to 0, so this quantity can be used to measure the degree of polarization. If one of the components equals 0 the time-average also returns to 0, but this is simply a linearly polarized state. To keep track of all the correlations of the field, we define a **coherency matrix $G$**:

```{math}
:label: eq:coherencyMatrix
G = \left \langle
\begin{bmatrix}
E_x(t) \\ E_y(t)
\end{bmatrix}
\begin{bmatrix}
E_x^*(t) & E_y^*(t)
\end{bmatrix}
\right \rangle = \begin{bmatrix}
\langle E_x^2(t) \rangle & \langle E_x(t) E_y^*(t) \rangle \\
\langle E_x^*(t) E_y(t) \rangle & \langle E_y^2(t) \rangle
\end{bmatrix}
```

Note that the field components matrix can be related to the Jones matrix:

```{math}
:label: eq:jonesRelation
\begin{bmatrix}
E_x(t) \\ E_y(t)
\end{bmatrix} =
\begin{bmatrix}
A_x \\ A_y
\end{bmatrix} e^{-i \omega t} = \mathbf{J} e^{-i \omega t}
```

Therefore, the coherency matrix $G$ can be described as:

```{math}
:label: eq:GfromJ
G = \mathbf{J} \mathbf{J^\dagger}
```

:::{prf:example} Jones to coherency matrix
- Horizontally linearly polarized light: $\mathbf{J} = \begin{bmatrix} 1 \\ 0 \end{bmatrix} \longrightarrow G_{\rm horizontal} = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}$
- Diagonally linearly polarized light: $\mathbf{J} = \frac{1}{\sqrt{2}}\begin{bmatrix} 1 \\ 1 \end{bmatrix} \longrightarrow G_{\rm diagonal} = \frac{1}{2}\begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix}$
- Right circularly polarized light: $\mathbf{J} = \frac{1}{\sqrt{2}}\begin{bmatrix} 1 \\ -i \end{bmatrix} \longrightarrow G_{\rm circular} = \frac{1}{2}\begin{bmatrix} 1 & i \\ -i & 1 \end{bmatrix}$
- Unpolarized light: $G_{\rm unpolarized} = \frac{1}{2}\begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$
:::
### Stokes parameters

From those examples, we can see that in general the diagonal elements are positive, real-valued and the sum of them is the total average intensity. The off-diagonal elements are complex-valued and are each other's complex conjugates. Therefore, with the average intensity $I$, we can write an arbitrary coherency matrix as:

```{math}
:label: eq:stokesExpansion
G = \frac{1}{2} \begin{bmatrix}
I + Q & U + iV \\
U - iV & I - Q
\end{bmatrix} = \frac{1}{2} \Bigg(
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix} I +
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix} Q +
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix} U +
\begin{bmatrix}
0 & i \\
-i & 0
\end{bmatrix} V
\Bigg)
```

Those four matrices are called **Pauli matrices**; the coefficients $I, Q, U, V$ are known as **Stokes parameters** which describe the polarization state of light. They can be put into a **Stokes vector** $S$:

```{math}
:label: eq:stokesVector
S = \begin{bmatrix}
I \\ Q \\ U \\ V
\end{bmatrix}
```

We can rewrite the transformation of the Stokes vectors by expanding the Pauli matrices as:

```{math}
:label: eq:stokesTransform
\begin{bmatrix}
I \\ Q \\ U \\ V
\end{bmatrix}
=
\begin{bmatrix}
1 & 0 & 0 & 1 \\
1 & 0 & 0 & -1 \\
0 & 1 & 1 & 0 \\
0 & i & -i & 0
\end{bmatrix}
\begin{bmatrix}
\langle E_x^2(t) \rangle \\ \langle E_x(t) E_y^*(t) \rangle \\ \langle E_x^*(t) E_y(t) \rangle \\ \langle E_y^2(t) \rangle
\end{bmatrix} = \begin{bmatrix}
\langle E_x^2 \rangle + \langle E_y^2 \rangle \\
\langle E_x^2 \rangle - \langle E_y^2 \rangle \\
2 E_x E_y \cos(\phi) \\
2 E_x E_y \sin(\phi)
\end{bmatrix}
```

:::{prf:example} Polarization states with Stokes parameters:
```{math}
:label: eq:stokesExamples
G_{\rm horizontal} \longrightarrow S =
\begin{bmatrix}
1 \\ 1 \\ 0 \\ 0
\end{bmatrix} \\
```

```{math}
G_{\rm diagonal} \longrightarrow S =
\begin{bmatrix}
1 \\ 0 \\ 1 \\ 0
\end{bmatrix} \\
```

```{math}
G_{\rm circular} \longrightarrow S =
\begin{bmatrix}
1 \\ 0 \\ 0 \\ 1
\end{bmatrix} \\

```

```{math}
G_{\rm unpolarized} \longrightarrow S =
\begin{bmatrix}
1 \\ 0 \\ 0 \\ 0
\end{bmatrix}
```
:::

:::{note}
As you can see from the example:
- $Q \to $  a horizontal linearly polarized state
- $U \to$ a diagonal linearly polarized state
- $V \to$ a circularly polarized state.
:::
### Poincaré Sphere

In practice, we can measure the first component of the Stokes vector – the intensity $I$. The three other Stokes parameters $Q$, $U$ and $V$ can be interpreted geometrically as the coordinates of a point in the Poincaré sphere. If the light is fully polarized, then this point lies on the surface of the sphere with radius $I$. If the light is fully unpolarized, this point lies at the origin. The length of the vector $\begin{bmatrix} Q \\ U \\ V \end{bmatrix}$ is expressed as $\sqrt{Q^2 + U^2 + V^2}$ which is a measure of the degree of polarization.

[*Insert an image*]

## Jones and Muller formalism
Jones and Stokes/Mueller are the two most commonly used treatments for polarized signals. Jones formalism models the effects of instruments with matrix operations on electromagnetic field components or the so-called Jones vector $\mathbf{J} = \begin{bmatrix}
    A_x & A_y
\end{bmatrix}^\top$.
\begin{align}
    \mathbf{J}_{f} &= \mathcal{J} \mathbf{J}_{i}
\end{align}
where Jones matrix $\mathcal{J}$ which can be a general product of matrices describing different effects like optical elements on the initial field component.
\begin{align}
    \begin{bmatrix}
        A_x \\ A_y
    \end{bmatrix}_f &= \prod_k \begin{bmatrix}
        \mathcal{J}_{xx} & \mathcal{J}_{xy} \\
        \mathcal{J}_{yx} & \mathcal{J}_{yy}
    \end{bmatrix}_k \begin{bmatrix}
        A_x \\ A_y
    \end{bmatrix}_i
\end{align}
Similarly, Mueller formalism describes the instrument effects on the observable quantity Stokes parameters.
\begin{align}
    \mathbf{S}_{f} = \mathbf{M} \mathbf{S}_{i}
\end{align}
where the Mueller matrix $\mathbf{M}$, is the products of individual components on Stokes parameters.
\begin{equation}
    \begin{bmatrix}
        I \\ Q \\ U \\ V
    \end{bmatrix}_f = \prod_k \begin{bmatrix}
        M_{II} & M_{IQ} & M_{IU} & M_{IV} \\
        M_{QI} & M_{QQ} & M_{QU} & M_{QV} \\
        M_{UI} & M_{UQ} & M_{UU} & M_{UV} \\
        M_{VI} & M_{VQ} & M_{VU} & M_{VV} 
    \end{bmatrix}_k \begin{bmatrix}
        I \\ Q \\ U \\ V
    \end{bmatrix}_i
\end{equation}
The transformation from the Jones matrix $\mathcal{J}$ to the Mueller matrix $\mathbf{M}$:
\begin{equation}
    \mathbf{M} = \mathbf{U}(\mathcal{J} \otimes \mathcal{J^*}) \mathbf{U}^{-1}
\end{equation}
where $\otimes$ is the Kronecker product operator, $\mathbf{U} = \dfrac{1}{\sqrt{2}} \begin{bmatrix}
    1 & 0 & 0 & 1 \\
    1 & 0 & 0 & -1 \\
    0 & 1 & 1 & 0 \\
    0 & -i & i & 0
\end{bmatrix}$.

### Optical elements
#### Polarizer 
Changing the orthogonal amplitudes unequally. For example, a linear polarizer can be described by a Jones matrix:
$$
    \begin{align}
        \mathcal{J} = \begin{bmatrix}
        g_1 & 0 \\ 0 & g_2
    \end{bmatrix} \longrightarrow \mathbf{M}_{\text{polarizer}}=
    \begin{bmatrix}
        \dfrac{g_1^2 + g_2^2}{2} & \dfrac{g_1^2 - g_2^2}{2} & 0 & 0 \\
        \dfrac{g_1^2 - g_2^2}{2} & \dfrac{g_1^2 + g_2^2}{2} & 0 & 0 \\
        0 & 0 & g_1 g_2 & 0 \\
        0 & 0 & 0 & g_1 g_2 
    \end{bmatrix}
    \end{align}
$$

:::{note} Linear polarizer as detector in CMB experiments
The detector used in CMB experiments can be modeled as an ideal linear polarizer. In the Jones formalism, it is described by

$$
\mathcal{J} =
\begin{bmatrix}
1 & 0 \\
0 & 0
\end{bmatrix}.
$$

The corresponding Mueller matrix is then given by

$$
\mathbf{M}_{\rm det} = \frac{1}{2}
\begin{bmatrix}
1 & 1 & 0 & 0 \\
1 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}.
$$
:::
#### Wave plate (Retarder)
Introducing a phase shift between orthogonal components. For example, when the x component gets a $\delta/2$ phase shift (fast axis), and the y component gets a $-\delta/2$ phase shift (slow axis). The phase shift between x and y is $\delta$.

$$
    \begin{align}
        \mathcal{J} = \begin{bmatrix}
        e^{i \delta/2} & 0 \\ 0 &  e^{-i \delta/2} 
    \end{bmatrix} \longrightarrow \mathbf{M}_{\text{waveplate}} =
    \begin{bmatrix}
        1 & 0 & 0 & 0 \\
        0 & 1 & 0 & 0 \\
        0 & 0 & \cos\delta & \sin\delta \\
        0 & 0 & -\sin\delta & \cos\delta
    \end{bmatrix}  
    \end{align}
$$
:::{note} Half-wave plate for CMB experiments
One of the main goals of the next generation of CMB experiments is the detection of primordial B-mode polarization. Achieving this objective requires an extremely precise control of systematic effects. In particular, the mitigation of $1/f$ noise, which dominates at low frequencies, is crucial.

A half-wave plate (HWP) is especially useful in this context, as it modulates the polarized signal to higher frequencies, around $4 f_{\rm HWP}$, thereby reducing the impact of low-frequency noise.

An ideal monochromatic HWP corresponds to a retardance $\delta = \pi$ (i.e. half of a full wave $2\pi$), and its Mueller matrix is given by:

$$
\mathbf{H}_{\text{mono}} =
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & -1
\end{bmatrix}.
$$
:::
#### Rotator
Rotating the orthogonal components by an angle $\theta$. 
$$
    \begin{align}
    \mathcal{J} = \begin{bmatrix}
    \cos(\theta) & \sin(\theta) \\
    \rm -sin(\theta) & \cos(\theta)
\end{bmatrix} \longrightarrow \mathbf{R}(2\theta) = \begin{bmatrix}
        1 & 0 & 0 & 0 \\
        0 & \cos(2 \theta) & \sin(2 \theta) & 0 \\
        0 & \rm -sin(2 \theta) & \cos(2 \theta) & 0 \\
        0 & 0 & 0 & 1  
    \end{bmatrix}
    \end{align}
$$

:::{note} Rotation representation of spin-2 object
We can describe the rotation of optical elements by 
1. Transforming to a basis where the Jones/Muller matrix is diagonal to describe the Jones/Muller vector in a coordinate system whose axes align with the axes of the optical elements
2. Applying the Jones/Muller matrix
3. Transforming back to the original basis. 
$$
    \mathbf{M}(2\theta) = \mathbf{R}(2\theta)^{\top} \mathbf{M} \mathbf{R}(2\theta)
$$
:::

### Optical chain
**Model:**

- A half-wave plate (HWP) $\mathbf{H}$ rotating at an angle $\varphi_t$ with frequency $f_{\rm HWP} = 2\,\mathrm{Hz}$. Additional parameters can be included in $\gamma$ to describe non-ideal or more complex HWP configurations.  
- A detector modeled as an ideal linear polarizer, with an orientation angle $\alpha_t$ that varies with time due to the scanning strategy.

The total optical chain is described by @ema_2026:

$$
\mathbf{M}(t) = \mathbf{M}_{\rm det} \, \mathbf{R}(-2\varphi_t)\, \mathbf{H}(\gamma)\, \mathbf{R}(2\varphi_t)\, \mathbf{R}(2\alpha_t).
$$

:::{note} What actually happens ?
:class: dropdown
The order matters (right $\rightarrow$ left action):
- $\mathbf{R}(2\alpha_t)$: sky rotation into detector frame  
- $\mathbf{R}(2\varphi_t)$ and $\mathbf{R}(-2\varphi_t)$: change of basis for the HWP  
- $\mathbf{H}(\gamma)$: HWP action  
- $\mathbf{M}_{\rm det}$: projection by the detector  
:::

:::{prf:example} Monochromatic HWP chain
$$
\mathbf{M}^{\text{mono}}(t) &= \underbrace{\frac{1}{2}
\begin{bmatrix}
1 & 1 & 0 & 0 \\
1 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}}_{\mathbf{M}_{\text{det}}} \, \underbrace{\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos(4 \varphi_t) & \sin(4 \varphi_t) & 0 \\
0 & -\sin(4 \varphi_t) & \cos(4 \varphi_t) & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}}_{\mathbf{R}(-2\varphi_t)\, \mathbf{H}_{\text{mono}}\, \mathbf{R}(2\varphi_t)}\, \underbrace{\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos(2 \alpha_t) & \sin(2 \alpha_t) & 0 \\
0 & -\sin(2 \alpha_t) & \cos(2 \alpha_t) & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}}_{\mathbf{R}(2\alpha_t)} \\
&= \dfrac{1}{2} \begin{bmatrix}
1 & \cos(2 \alpha_t + 4 \varphi_t) & \sin(2 \alpha_t + 4 \varphi_t) & 0 \\
1 & \cos(2 \alpha_t + 4 \varphi_t) & \sin(2 \alpha_t + 4 \varphi_t) & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
$$
:::

### Time-order data (TOD)
In CMB experiments, the detector is intensity-sensitive, measuring the polarization by projecting the full Stokes vector onto the detector's sensitivity axis. This measurement is captured by the first row of the optical chain's Muller matrix product, yielding the observed time-ordered data (TOD) as a linear combination of the Stokes parameters:
$$
\mathbf{d}_t = \mathbf{M}_{00}(t) {\rm I}_t + \mathbf{M}_{01}(t) {\rm Q}_t + \mathbf{M}_{02}(t) {\rm U}_t
$$

:::{prf:example} Monochromatic HWP optical chain
The TOD can be written as
$$
\mathbf{d}_t = {\rm I}_t + \cos(2 \alpha_t + 4 \varphi_t) {\rm Q}_t + \sin(2 \alpha_t + 4 \varphi_t) {\rm U}_t
$$
:::

## More advanced models
[*Insert Ema's model*]