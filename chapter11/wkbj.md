# The WKBJ method

The next "non-perturbative" method we will discuss is the Wentzel-Kramers-Brillouin-Jeffreys approximation (sometimes the "J" is not present). This is a technique for solving wave equations, focusing on the case that the relevant energies are "large" in a sense that we will discuss. 

This method is quite powerful and has uses well beyond quantum mechanics. It is the underlying scheme by which we justify ray-tracing methods for solving differential equations, such as geometric optics. For a good general discussion, I recommend {cite:p}`bender1999advanced`. (A wonderful book for many subjects). 

In the case of quantum mechanics, the other beautiful outcome of the WKB approximation is that we can begin to see the emergence of classical mechanics. We will discuss this fact once we have gone over the basics of the approximation.

While this is not a perturbative method, as it applies even when there is no "nearby" exactly solvable Hamiltonian, it is an *asymptotic* method. That is, there is a small parameter, and a systematic way of expanding the solution in that small parameter. The lowest-order solution is *singular*: in particular it is non-analytic in the small parameter. But there is an expression for it that can often be solved even when the underlying Schroedinger equation cannot be. 

## The short-wavelength limit

### Generalities

We are going to focus here on the one-dimensional time-independent Schroedinger equation:
```{math}
- \frac{\hbar^2}{2m} \frac{\del^2}{\del x^2} \psi(x) + V(x)\psi(x) = E\psi(x)
```
Crudely speaking, we are interested in highly excited states, in a way we will try to make precise. Consider in particular a bound state problem as illustrated below. 

Inside the potential well, at high eneough energy there will be many nodes and the wavfunction will oscillate rapidly. In this region, the approximation works when the number of nodes is $\gg 1$. If the potential is not varying too rapidly, it will be approximately constant over the scale of separation of the nodes. Locally near these nodes, the solution will then look like a plane wave (solution in a constant potential) with wavenumber 
```{math}
\hbar k(x) = p(x) = \sqrt{2 m (E - V(x))}
```
Similarly, if the energy is far enough below the potential, then the exponential falloff will be rapid compared to the rate of change of the potential and cam be characterized locally by a decay rate
```{math}
\hbar\kappa(x) = \sqrt{2m(V(x) - E)}
```
which we can think of as an imaginary wavenumber.

If this approximation is close to true, we can approximate the wavefunction well inside the potential well with
```{math}
:label: semiclassical_wavefunctions
\psi(x) \sim A_+ \exp\left(\frac{i}{\hbar}\int_{x_0}^x dx' p(x')\right) + A_- \exp\left(- \frac{i}{\hbar}\int_{x_0}^x dx' p(x')\right)
```
where $p(x) = \sqrt{2m(E - V(x))}$ is the classical momentum at fixed energy. Here $x_0$ is a choice, that can be absorbed into $A_{\pm}$. Well below the barrier, the solution is:
```{math}
:label: below_barrier
\psi(x) \sim B_+ \exp\left(\frac{1}{\hbar}\int_{x_0}^x dx' \rho(x')\right) + B_- \exp\left(- \frac{1}{\hbar}\int_{x_0}^x dx' \rho(x')\right)
```
where $\rho(x) = - i \sqrt{2m(E - V(x))} = \sqrt{2m(V(x) - E)}$ is a sort of imaginary momentum. 

The approximation can be expected to break down when the energy is roughly equal to the potential energy, so that the variation of the wavefunciton is not rapid. This is the region around the classical turning points. However, in this region, we can approximate the potential as a linear one, and the Schroedinger equation with a linear potential does have a solution in terms of Airy functions. If the WKB approximation starts to be good while the linear approximation is still valid, then we can use this fact to match the Airy functions to the WKB solutions and get a complete solution, including an approximation to the energy eigenvalues.

To get an estimate of when this approximation words, we can ask that the change in the wavelength $\lambda(x) = \hbar/p(x)$ over a distance of order the wavelength is small compared to the wavelength. This becomes
```{math}
:label: wkb_cond
\begin{align}
\Big| \frac{\Delta\lambda}{\lambda}\Big| & \sim \Big| \frac{\lambda\del_x \lambda}{\lambda}\Big| \\
& = |\del_x \lambda| = \Big|\frac{m\hbar V'}{(2m(E - V))^{3/2}}\Big| \\
& = \Big| \frac{m \hbar V'}{p^3}\Big| \\
& = \half \Big| \frac{2 m}{p^2} \frac{\hbar V'}{p}\Big|\\
& = \half \Big| \frac{\lambda \del_x V}{E_{kin}}\Big| \ll 1
\end{align}
```

So the change in the potential over a wavelength is small compared to the kinetix energy. We will see how this conditions emerges from a more systematic treatment.

### The semiclassical expansion

Let us begin with the ansatz
```{math}
\psi = e^{i S/\hbar}
```
So far this is just a rewriting, not an approximation. I am using the letter $S$ to foreshadow the relationship of the WKB approximation to the emergence of classical mechanics.

Putting this into the TISE, we get
```{math}
:label: se_wkb
(\del_x S)^2 = 2m(E - V(x)) + i\hbar \del_x^2 S
```
This is still an exact equation. But the approximation {eq}`semiclassical_wavefunctions` arises if we are allower to ignore the final term. Since this aproximation seems tied up in classical mechanics, and the last term is proportional to $\hbar$, one often says that we will perform a "small-$\hbar$" approximation. This is not quite correct. What we will be demanding is essentially that $S/\hbar \gg 1$.

With this in mind, we can still write a formal expansion
```{math}
:label: hbar_expansion
S = S_{cl} + \hbar S_1 + \hbar^2 S_2 + \ldots
```
and solve the Schroedinger equation order by order in $\hbar$. We will still need to check that $\hbar S_k \ll S_{k-1}$. Note that in terms of the wavefunction $\psi$ this is a *singular* expansion; the lowest-order piece is nonanalytic in $\hbar$. 

Plugging {eq}`hbar_expansion` into {eq}`se_wkb` and keeping only the $\hbar$-independent term, we get
```{math}
(\del_x S_{cl})^2 = 2m(E - V(x)) \Rightarrow 
\frac{(\del_x S_{cl})^2}{2m} + V(x) = E
```
Those who have had a good classical mechanics course will recognize this as the *Hamilton-Jacobi equation*, where $S$ is the classical action. We will return to this interpretation below, which is central to ray tracing/geometric optics/the method of characteristics. The solution is
```{math}
S_{cl}(x) = \pm \int_{x_0}^x dx' \sqrt{2m(E - V(x'))} \equiv \pm \int_{x_0}^x dx' p(x')
```
where again, $x_0$ is an integration constant. We have two solutions to $S$ and therefore for $\psi$. At this level of approximation we can consider linear combinations of these two solutions. Note that what we have done is true formally whether $E - V$ is positive or negative. In the former case, we recover {eq}`semiclassical_wavefunctions`. In the latter case, $S$ becomes imaginary, and we recover {eq}`below_barrier`. 

Our next step is to find $S_1$. The $\cO(\hbar)$ terms in {eq}`se_wkb` are:
```{math}
2 \del_x S_{cl} \del_x S_1 = i \del_x^2 S_{cl} 
\Rightarrow \del_x S_1 = \frac{i}{2} \frac{\del_x^2 S_0}{\del_x S_0} = \frac{i}{2} \del_x \ln \del_x S_0
```
Thus, keeping only terms that are nonvanishing as $\hbar \to 0$, we have
```{math}
\begin{align}
\psi(x) & = e^{i S/\hbar} \\
& = e^{\frac{i S_{cl}}{\hbar} + i S_1}\\
& = \frac{1}{\sqrt{\del_x S}} e^{i \frac{S_{cl}}{\hbar}}\\
& = \frac{1}{\sqrt{p(x)}}  e^{i \frac{S_{cl}}{\hbar}}
\end{align}
```
where $p(x) = \sqrt{2m(E - V(x))}$. This prefactor has a nice semiclassical interpretation, especially for bound states. We know $\psi(x)|^2 \propto \frac{1}{p(x)}$ is the probability density for the particle at position $x$. If the particle is in a potential well it will oscillate with period $T$. The fraction of time the particle will spend in a region $dx$ is the time spent in that region, which is
```{math}
P(x)dx = \frac{dx}{v(x)} = \frac{m dx}{p(x)} \propto |\psi(x)|^2 dx
```

Finally, we need to check on our approximation. Thius should be done at every order but we will here simply ask that in {eq}`se_wkb` the last term is small compared to the rest: that is, that
```{math}
(\del_x S_{cl})^2 \gg \hbar (\del_x^2 S_{cl})
```
This means
```{math}
p(x)^2 \gg 2\hbar| p'(x) p(x)|  = \Big| \frac{- 2 m V'(x)}{p}\Big|
\Rightarrow \Big| \frac{\lambda(x) V'}{E_{kin}} \ll 1
```
which is essentially the condition we already derived from a more hand-waving argument.

## Bound state problems

We now consider particles in some potential well, such that $\lim_{x\to\infty} V(x) > E$. In the figure below, we have broken up the $x$ axis into three regions. In regions I, II, III the WKB approximation is expected to hold. For large $|x|$ (in regions I and III), we assume the energy is far enough below the barrier that the length scale giverning the exponential falloff of the wavefunction is small compared to the length scale over which the potential varies. In region II we assume that the energy is large enough that the wavefunction rapidly oscillates, with a space between nodes so small that the potential does not vary appreciably in this range.

The WKB approximation is expected to break down at the classical turning points $A,B$> Here $p(x) \to 0$, $\lambda(x) \to \infty$, and we can see that the condition {eq}`wkb_cond` breaks down. Generally, however, the potential can be well-approximated by a linear potential; the resulting Schroedinger equation is exactly solvable. If we are fortunate, the regime in which the linear approximation holds will overlap with the regime in which the WKB approximation holds, as illustrated below. In this case we can match our WKB functions to the solutions near the turning points. 

Let us first turn to the solutions in the WKB regions. In region I, the solution is
```{nath}
\psi_I = \frac{C_I}{\sqrt{2m(V(x) - E)}} e^{\frac{1}{\hbar} \int^x_{x_I} dx'\sqrt{2m(V(x') - E)}}
```
Here $x_I$ is arbitrary. This solution will be exponentially decaying as $x \to - \infty$: we have set to zero an exponentially growing component.

In region II the solution looks like
```{math}
\psi_{II}(x) = \frac{1}{\sqrt{2m(E - V(x))}} \left(A_{II} e^{\frac{i}{\hbar}\int_{x_{II}}^x dx'\sqrt{2m(V(x') - E)}} + B_{II}  e^{- \frac{i}{\hbar}\int_{x_{II}}^x dx'\sqrt{2m(V(x') - E)}}\right)
```


