# Introduction to quantum mechanics

I will start with a quasi-historical, phenomenological discussion of some basic aspects of quantum mechanics:

1. The need for a new dimensionful quantity $\hbar$ with units [Energy $\times$ time].
2. The quantization of the energy of light with frequency $\omega$ into parcels ("photons") with energy $\hbar \omega$,
3. The fact that quantum states can be written as complex vectors, and that the sum of two such vectors is another legitimate quantum state.
4. The probabilistic nature of the outcome of quantum measurements.

These are all important; point (3) motivates a serious survey/review of linear algebra, which is also needed to discuss (4) more precisely.

## Blackbody radiation

Consider a cavity with walls at some temperature $T$, such that the electromagnetic field inside of the cavity is at equilibrium with the walls

![black body model](blackbody.jpeg)

 What is the expected energy density inside the cavity? We could (following many textbooks) try to comute this from classical electromagnetism, but we will appeal to dimensional analysis. 
 
 The total energy denisty should be an integral over all allowed frequencies:
 
 ```{math}
 :label: energy_density
 E(T) = \int_0^{\infty} E(T,\omega)
 ```
 
 Assuming that the box is very large compared to the wavelengt of the light inside, and that we are asking aboput the energy density which should (for a large box) be independent ot the box size, We have the following dimensionful quantities:
 
 1. The frequency $\omega$.
 2. The temperature writen as a thermal energy $k_B T$.
 3. The speed of light $c$.
 
 To get an energy density we can make an energy from $k_B T$ and a length scale $c/\omega$ (proportional to the wavelenngth). $E(T,\omega)$ should have units of energy denisty per frequency. The only combination of the above yielding a quantity with the rigt dimensions is:
 
 ```{math}
 :label: en_dens_dimanalysis
 E(T, omega) = A k_B T \left(\frac{\omega}{c}\right)^3 \frac{1}{\omega}
 ```
 
 where $A$ is a dimensionless constant that requires a first-principles calculation to obtain.
 
 The total energy is thus
 
 ```{math}
 :label: total_energy_divergent
 E(T) = \left(\frac{A k_B T}{c^3}\right) \int_0^{\infty} d\omega \omega^2 = \infty
 ```
 
This is sometimes termed the "ultraviolet catastrophe". Possible outs are (a) there is a maximum possible frequency for the electromagnetic field, or (b) we need to introduce some other dimensionful constant so that $E(T,omega)$ becomes a function that falls off rapidly at large $\omega$. Note that either requires some new dimensionful constant; the former requires at least a maximum frequency $\Omega$. 
 
We will describe a solution of the type (b), as this produces a spectrum which is in agreement with the data; this was Planck's original goal. Plank's guess ammounted to introducing a new fundamental constant $\hbar$ with units [Energy $\times$ time]. Thus, $\hbar \omega$ is now an energy scale intronsic to the system.

Now consider an electromagnetic field with a given polarization and wave vector ${\vec k}$, such that $\omega = 2\pi c |{\vec k}|$. 

## Photon polarization

### Classical description

Consider an electromagnetic field propagating in a vacuum along the $z$ direction. The most general solution to Maxwell's equations in this case is:

```{math}
:label: propagating_em
{\vec E} = \text{Re}\ \left\{ \left[ E_x {\hat x} + E_y {\hat y} \right]e^{i (kx - \omega t)}\right\} = \text{Re}\left\{ {\vec E}_c e^{i (kx - \omega t)} \right\}
```

where $E_{x,y} \in \mathbb{C}$ so that $E_i = |E_i| e^{i\delta_i}$, and $\omega = c k$. We can rewrite this as

```{math}
:label: real_propagating
{\vec E} = |E_x|\cos(kz - \omega t+ \delta_x) {\hat x} + |E_y| \cos(kx - \omega t + \delta_y)
```

The magnetic field ${\vec H}$ can be determined from the Maxwell equation

```{math}
:label: determine_H
\nabla \times {\vec E} + \frac{1}{c}\frac{\del}{\del t}\vec{H}
```

This supports various polarization states such as

1. Linear/plane polarization: ${\vec E}_x = E e^{i\delta} {\hat n}$ where $E$ is a positive real number and ${\hat n}$ a unit vector in the $x-y$ plane. In particular ${\hat n} = {\hat x}, {\hat y}$ correspond to plane polarization along the $x$- and $y$-axis respectively.

2. Circular polarization:
- **Left circular polarization (LCP)**: $E_y = - i E_x = - i E e^{i\delta)$, or
equivalently ${\vec E}_c = E({\hat x} - i {\hat y})e^{i\delta}$. Thus:

```{math}
:label: lcp
{\vec E}_{LCP} = E\left(\cos(kz - \omega t + \delta){\hat x} + \sin (kz - \omega t + \delta) {\hat y}\right)
```

- **Right circular polarization (RCP)**: $E_y = i E_x = i e^{i\delta}$ or ${\vec E}_c = E({\hat x} + i {\hat y})e^{i\delta}$. Thus:

```{math}
:label: rcp
{\vec E}_{RCP} = E\left(\cos(kz - \omega t + \delta){\hat x} + \sin (kz - \omega t + \delta) {\hat y}\right)
```

Note that for any plane wave, ${\vec E}_c$ can be written as a linear combination of left- and right-circular polarizations, or as $x$- and $y$-plane polarizations. 

The energy density is 

```{math}
:label: maxwell_ed
\begin{align}
\cal{E} & = \frac{1}{8\pi}\left[ {\vec E}^2 + {\vec H}^2\right]\\
& = \frac{1}{4\pi} \left[|E_x|^2\cos^2(kz - \omega t + \delta_x) + |E_y|^2\cos^2(kz - \omega t + \delta_y)\right]
\end{align}
```

Assuming the field propagates in some volume $V$, the total energy is

```{math}
:label: total_energy
U = \int d^2 x z {\cal E} = \frac{V}{2\times 4\pi} \left[|E_x|^2 + |E_y|^2\right]
```

the factor of 2 in the denominator comes from integrating the $\cos^2$ factors over $z$.

Now let us pass our beam through a polarizer. We call an "x-polarizer" one which admits only light polarized along the ${\hat x}$ direction, so that $E_x$ remains unchanged by $E_y$ is set to zero. In general, we can consider a polarizer aligned along any complex unit vector ${\hat n}$ so that any initial light wave described by {eq}`propagating_em` becomes

```{math}
:label: polarized_em
{\vec E}_{after} = \text{Re}\left\{ {\vec E}_c \cdot {\hat n} {\hat n} e^{i(kz - \omega t)} \right\}
```

For a polarizer aligned along ${\hat x}$, ${\hat n} = {\hat x}$; for a polarizer admitting LCP, ${\hat n}_{LCP} = \frac{1}{\sqrt{2}} \left({\hat x} - i {\hat y}\right)$; for a polarizer admitting RCP, ${\hat n}_{RCP} = \frac{1}{\sqrt{2}}\left({\hat x} + i {\hat y}\right)$.

This generally reduces the energy of the beam of light. For example, we can show that if we consider light polarized along ${\hat n} = \frac{1}{\sqrt{2}} \left(\hat{x} + {\hat y}\right)$, that is at a $45^{\circ}$ angle fromthe $x$-axis, and pass it through a polatizer aligned along the $x$ axis,

```{math}
:label: field_reduction
{\vec E} = E\cos(kx - \omega t + \delta)\left({\hat x} + {\hat y}\right) \rightarrow E\cos(kx - \omega t + \delta){\hat x}
```

The energy is in this case cut in half:

```{math}
:label: energy_reduction
U_{init} = \frac{V}{8\pi}\times 2 \times |E|^2 \rightarrow U_{after} = \frac{V}{8\pi}|E|^2 = \half U_{init}
```

### Quantum description

If we apply Planck and Einstein's insights, the beam of light consists of photons with energy $U = N\hbar \omega$. Consider the case above of light polarized at $45^{\circ}$ from teh $x$-axis passing through a polarizer aligned along the $x$ axos. Then $U_{final} = \half N \hbar \omega$ and the number of photons is cut in half. But now we should be asking:

- *which* photons pass through the polarizer?
- also what if $N$ is odd?

Our best available interpretation is that *each* photon has a $50\%$ chance of passing through this polarizer. For typical classical beams one can see that $N \gg 1$, so that the law of large numbers/central limit theorem tells us

```{math}
:label: lln_polarizer
N \to N\left(\half + {\cal O}\left(\frac{1}{\sqrt{N}}\right)\right)
```

