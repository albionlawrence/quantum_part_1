# The simple harmonic oscillator

The next potential we wish to consider is the *simple harmonic oscillator,
```{math}
:label: sho_ham
H = \frac{p^2}{2m} + \half m \omega^2 x^2
```
Tihs is exactly solvable in both classical and quantum mechanics. Why do we consider such a potential, besides this nice fact of classical solvablility? Because at low energies, it is often a good first approximation to a given potential.

Consider a more general 1d potential problem,
```{math}
H = \frac{p^2}{2m} + V(x)
```
We will consider energies so that the classically allowed region is near the absolute monimum of the potential. 

Now if we set $x = x_0$ as the location of this classical minimum, we can approximate $V(x)$ as:
```{math}
:label: approx_potential
V(x) = V(x_0) + (x - x_0) V'(x_0) + \half (x - x_0)^2 V''(x_0) + \frac{1}{3!} (x = x_0)^3 V'''(x_0) + \ldots
```
Since we are looking near a minimum, $V'(x_0) = 0$. We can also shift the total energy (since it is irrelevant in classical and qauntum mechanics in the absence of gravity). This expansion is a good one if the higher order terms in $(x - x_0)$ are smaller than the lower-order ones. In particular, we can approximate the potential by the quadratic term if
```{math}
:label: quadratic_condition
\half \big| V''(x_0) (x - x_0)^2\big| \gg \frac{1}{3!} \big|V'''(x_0)(x - x_0)^3\big| \Rightarrow |x - x_0| \ll \frac{3 V''(x_0)}{V'''(x_0)}
```
You might have been tempted to say "the third derivtive of $V$ at $x_0$ is smaller than the second derivative" but that makes no sense -- these quantities have different dimensions. In fact the viability of the approximation also depends on $|x - x_0|$ being small enough. This depends on the energy. We can see thius best classically: for larger energies, the particle has a larger range, and eventually the criterion {eq}`quadratic_condition` will break down.

This story is actually pretty general; for many problems, teh Lagrangian can be approximated at low energies by a Lagrangian which is quadratic in the phase space variables; if the system is stable, it can be reduced further to a collection of harmonic oscillators. This includes the electromagnetic field. Higher order or anharmonic terms (which in quantum field theory arises from particle interactions) can be treated in an approximation scheme known as *perturbation theory*.

Finally to get {eq}`sho_ham`, we set $V'(x_0) = m \omega^2$. We can define $\omega$ this way (given $m, V(x)$). The reason for doing so becomes clear when we examine the solutions to the classical and quantum problems.

## Classical solution

As a reminder, Hamilton's equations give us:
```{math}
\begin{align}
{\dot x} & = \frac{\del H}{\del p} = \frac{p}{m}\\
{\dot p} & = - \frac{\del H}{\del x} = - m \omega^2 x
\end{align}
```
Taking the deirvative of the first equation and using the second equation, we get the classical SHO equation
```{math}
{\ddot x} + \omega^2 x = -
```
which has as a general solution
```{math}
x(t) = X_{max} \cos(\omega t + \delta) \Rightarrow p = - X_{max} m\omega \sin(\omega t + \delta)
```
and $A,\delta$ are set by the initial conditions on $x(t_0), {\dot x}(t_0)$. The total energy of this solution is 
```{math}
E = \frac{p^2}{2m} + \half m \omega^2 x^2 = \half m \omega^2 X_{max}^2
```
Thus, more energetic states travel a wider range. The frequency of oscillation, and the period $T = 2\pi/\omega$, are fixed.




