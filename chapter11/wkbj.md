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
\Rightarrow \alpha \equiv \Big| \frac{\lambda(x) V'}{E_{kin}} \ll 1
```
which is essentially the condition we already derived from a more hand-waving argument. Here we introduce $\alpha$ for notational ease in the example below.

Just to get a sense of the nontriviality of these conditions, we can look at a 1d case with the potential $V = - c/x^n$ with $n > 0$. If we fix the total energy $E$, we find
```{math}
\alpha = \frac{2 m \hbar \frac{n c}{x^{n+1}}}{\left(E + \frac{c}{x^n}\right)^{3/2}}
```
For fixed $E$ this is always valid as $x \to \infty$ as the particle becomes the free particle for which WKB is exact. As $x to 0$, when the potential energy dominates is large compared to $|E|$, we have:
```{math}
	\alpha \sim \frac{2 m n \hbar}{\sqrt{c}} x^{\frac{n}{2} - 1}
```
Thus WKB works well when $n > 2$. For $n < 2$ WKB breaks down near the origin. (Note that for $n > 2$ the energy eigenstates are unbounded below, with $n = 2$ being an interesting marginal case, as we have seen in a prior problem set).

You might fairly ask why we chose the scaling we did. Why is the leading singular behavior $e^{i S/\hbar}$ and not $e^{i S/\hbar^2}$ or  $e^{i S/\hbar^{1/2}}$ or some such? Why do we expand $S$ in powers of $\hbar$ rather than $\hbar^2$, $\hbar^{1/2}$? This is determined by the power of $\hbar^2$ that sits in front of the kinetic term. If we demand that all of the terms in the Schroedinger equation appear at the same order, *including the energy*, you can convince yourself tha this is the right scaling. In general you have to deduce the correct scaling; and a given problem may support various scalings for different energies and momenta. The book {cite:p}`bender1999advanced` has a good discussion of these issues. [This paper](https://www.cambridge.org/core/journals/journal-of-fluid-mechanics/article/regimes-of-nearinertial-wave-dynamics/EF5D7BF32476D89A6582B8C3033252F9) of which I was a co-author encounters this issue in a situation where the resolution is nontrivial.

## Bound state problems

We now consider particles in some potential well, such that $\lim_{x\to\infty} V(x) > E$. In the figure below, we have broken up the $x$ axis into three regions. In regions I, II, III the WKB approximation is expected to hold. For large $|x|$ (in regions I and III), we assume the energy is far enough below the barrier that the length scale giverning the exponential falloff of the wavefunction is small compared to the length scale over which the potential varies. In region II we assume that the energy is large enough that the wavefunction rapidly oscillates, with a space between nodes so small that the potential does not vary appreciably in this range.

The WKB approximation is expected to break down at the classical turning points $A,B$> Here $p(x) \to 0$, $\lambda(x) \to \infty$, and we can see that the condition {eq}`wkb_cond` breaks down. Generally, however, the potential can be well-approximated by a linear potential; the resulting Schroedinger equation is exactly solvable. If we are fortunate, the regime in which the linear approximation holds will overlap with the regime in which the WKB approximation holds, as illustrated below. In this case we can match our WKB functions to the solutions near the turning points. 

Let us first turn to the solutions in the WKB regions. In region I, the solution is
```{math}
\psi_I = \frac{C_I}{\sqrt{2m(V(x) - E)}} e^{\frac{1}{\hbar} \int^x_{x_I} dx'\sqrt{2m(V(x') - E)}}
```
Here $x_I$ is arbitrary. This solution will be exponentially decaying as $x \to - \infty$: we have set to zero an exponentially growing component.

In region II the WKB solution looks like
```{math}
\psi_{II}(x) = \frac{1}{\sqrt{2m(E - V(x))}} \left(A_{II} e^{\frac{i}{\hbar}\int_{x_{II}}^x dx'\sqrt{2m(V(x') - E)}} + B_{II}  e^{- \frac{i}{\hbar}\int_{x_{II}}^x dx'\sqrt{2m(V(x') - E)}}\right)
```

While in Region III the WKB solution looks like 
```{math}
\psi_I = \frac{C_{III}}{\sqrt{2m(V(x) - E)}} e^{- \frac{1}{\hbar} \int^x_{x_{III}} dx'\sqrt{2m(V(x') - E)}}
```
which is exponentially decaying. 

As with the other bound state problems we have studied, we have 4 complex unknowns, with one complex constraint due to the combination of normalization and choice of overeall phase. We will find four constraints due to matching the WKB solutions to the equations near the turning points. 

Let us study the turning point $B$. Expanding in a Taylor series,
```{math}
\begin{align}
V(x) & = V(x_B) + (x - x_B) V'(x_B) + \half (x - x_B)^2 V''(x_B) + \ldots\\
&  = V(x_B) + \gamma (x = x_N) + \ldots
\end{align}
```
We assume that teh higher order terms are small in a region around $x_B$ that overlaps with the region of validity of the WKB approximation. In general, of course, this needs to be checked.

Now we examine the Schrodinger equation. By definition, $V(x_B) = E$, so these terms drop out. Furthermore, we define $y \equiv L (x - x_B)$, with $L$ to be determined. Nondimensionalizing our equations are almost always a good idea -- we will discover important characteristic scales, and we will reduce the equations to ones that we can look up or plug most easily into a computer. Further multiplyng the equation by $\frac{2 m L^2}{\hbar^2}$, the resulting equation is:
```{math}
- \del_y^2 \psi + \frac{2 m \gamma L^3}{\hbar^2} y = 0
```
We set $L = \left(\frac{2m\gamma}{\hbar^2}\right)^{1/3}$, to find
```{math}
- \del_y^2 \psi + y \psi = 0
```
This differential equation has known solutions in terms of *Airy functions*, whose properties you can look up in many places such as the [Digital Library of Mathematical Functions](https://dlmf.nist.gov/) (see Chapter 9). There are two independent solutions $Ai(y), Bi(y)$, and a general solution has the form
```{math}
\psi = a Ai(y) + b Bi(y)
```

At large $|y|$, the WKB approximation works well for these functions (you can and should deduce this from the conditions we have discussed). Their asymptotic properties are known:
```{math}
\begin{align}
Ai(y) \sim \begin{cases} \frac{1}{\sqrt{\pi} y^{1/4}} e^{-\frac{2}{3}y^{3/2}} & y \to \infty \\
 \frac{1}{\sqrt{\pi} |y|^{1/4}} \cos\left(\frac{2}{3}|y|^{3/2} - \frac{\pi}{4}\right) & y \to - \infty \end{cases}
Bi(y) \sim \begin{cases}  \frac{1}{\sqrt{\pi} y^{1/4}} e^{\frac{2}{3}y^{3/2}} & y \to \infty \\
 \frac{1}{\sqrt{\pi} |y|^{1/4}} \sin\left(\frac{2}{3}|y|^{3/2} - \frac{\pi}{4}\right) & y \to - \infty \end{cases}
\end{align}
```
You can check easily that these result from applying our WKB solutions to regions $II,III$ to the linear potential.

Normalizability then demands that we choose solution $Ai(y)$ about the turning point $x_B$. About $x_A$ we can map the problem to the one we solved by letting $y \to - y$, so that the proper solution is $Ai(-y)$. 

We then need to match the solutions in region II. Performing the expansion of $\int dx' p(x')$ near the turning point, 
```{math}
\frac{1}{\hbar} \int_{x_{II}}^x dx' \sqrt{2m(E - V(x'))} \sim - \frac{2}{3}(-y)^{3/2} + \frac{2}{3}(-y_{II})^{3/2}
```
where $y_{II} = L (x_{II} - x_B)$. The minus sign appears because we get $-y$ inside the square root; the upshot is an overall minus sign when we do the integral. We set $x_{II} = x_B$ to find that our solution in region II matches $Ai$ if we adjust $A_{II}, B_{II}$ such that
```{math}
\psi(x) \propto \frac{1}{\sqrt{2m(E - V(x))}} \cos\left(\frac{1}{\hbar} \int^{x_B}_x dx' \sqrt{2m(E - V(x'))} - \frac{\pi}{4}\right)
```
Note the integral is from $x$ to $x_B$; this takes care of the minus sign we introduced.

On the other hand, the same matching condition applied to the turning point $A$ gives us 
```{math}
\psi(x) \propto \frac{1}{\sqrt{2m(E - V(x))}} \cos\left(\frac{1}{\hbar} \int_{x_A}^x dx' \sqrt{2m(E - V(x'))} - \frac{\pi}{4}\right)
```
These two need to be equal, which means the cosine terms need to be equal. Since the cosine terms are odd, we can write
```{math}
 \cos\left(- \frac{1}{\hbar} \int^{x_B}_x dx' \sqrt{2m(E - V(x'))} + \frac{\pi}{4}\right) =  \cos\left(\frac{1}{\hbar} \int_{x_A}^x dx' \sqrt{2m(E - V(x'))} - \frac{\pi}{4}\right)
 ```
 The arguments now need to be equal up to a factor of $\pi n$ (the overall sign difference if $n$ is odd can be absorbed into the overall relative sign of $A_I, A_{III}$), so that
```{math}
 (- \frac{1}{\hbar} \int^{x_B}_x dx' \sqrt{2m(E - V(x'))} + \frac{\pi}{4} = 
\frac{1}{\hbar} \int_{x_A}^x dx' \sqrt{2m(E - V(x'))} - \frac{\pi}{4} - \pi n
```
which becomes
```{math}
\frac{1}{\hbar} \int_{x_A}^{x_B}dx' p(x') = \pi \hbar(n + \half) 
```
This is the *Bohr-Sommerfeld quantization condition*. It was generalized to higher-dimensional situations in various works by Einstein, Brillouin, and Keller (only applicable to energies for which classical trajectories live on tori in phase space; a story that will take us too far afield, however).


### Example 1: the Simple Harmonic Oscillator

In this case the turning points are at $x_B = - x_A = \sqrt{\frac{2E}{m\omega}}$. The quantization condition is
```{math}
\int_{-x_B}^{x_B} dx' \sqrt{2m(E - \half m \omega^2 (x')^2)} = \hbar \pi(n + \half)
```
Now we can substitute $x = y \sqrt{\frac{2E}{m\omega}}$ and set $y = \sin \theta$; we find
```{math}
\frac{\pi E}{\omega} = (n + \half) \pi \hbar
```
But this is the exact answer! This is a general feature of Hamiltonians quadratic in their arguments -- the WKB approximation gives exact expressions for the eigenvalues. It also, through the path integral, gives an exact expression for teh propagator, as we will discuss. It does not, however, give the right expressions for the energy eigenstates. This is a longer story; the chapters in Shankar on path integrals and their relation to WKB contains the required pieces of this puzzle.

### Example 2: the Linear potential

Consider instead $V = g |x|$. If we go through the same exercise, we find
```{math}
E = \half \left(\frac{3 g (n + \half) \pi \hbar}{2 m^{\half}}\right)^{2/3}
```
The wavefunctions, as it happens, are amenable to an exact solution using Airy functions, and the resulting eigenvalues can be computed. For the ground state $n = 0$, the WKB expression is too high by $10\%$. for the first excited state, the result is too high by $1\%$. For the second excited state, the result is low by $.5\%$. (It is worth thinking about why the $n = 0,1$ WKB answers will always be larger than the exact answer, but at higher $n$ there is no such restriction).

## The Hamilton-Jacobi equation and geometric optics

We found that at lowest order in the WKBJ approximation, 
```{math}
:label: ti_hj
\frac{1}{2m} ({\vec\nabla} S_{cl})^2 + V({\vec x}) = E
```
Here we have written down the equation for an $n$-dimensional nonrelativistic potential problem; the derivation is essentially the same. 

As it happens this is a well-known equation in classical mechanics, the *Hamilton-Jacobi* equation. Since this course teaches classical as well as quantum mechanics, I will break here and discuss the meaning of this equation in classical mechanics.

### Hamilton-Jacobi from least action

Let us return to the principle of least action and consider it in phase space form. Starting with $S = \int_{t_i}^{t_f} dt L(q,{\dot q})$, we recall that to first order in variations of $q$,
```{math}
\delta S = \left[ \frac{\del L}{\del {\dot q}^i} \delta q^i\right]\Big|^{t_f}_{t} + \int_{t_i}^{t} dt' \left(\frac{\del L}{\del q^i} - \frac{d}{dt} \frac{\del L}{\del {\dot q}^i}\right)\delta q^i
```
In the usual Euler-Lagrange equations we fix the initial and final positions. Here we want to understand $S$ evaluated on classical paths *as a function of* $q(t)$, given some fixed initial condition $q(t_i)$. Since we are evaluating $S$ along classical paths, the integral vanishes, the integrand just being the classical erquations of motion, and we are left with $\delta S = \frac{\del L}{\del {\dot q}^i}(t) \delta q^i(t)$, or
```{math}
:label: ds_dq
\frac{\del S}{\del q^i} = p_i
```
where $p_i$ is the conjugate momentum. Here since $q(t_i)$ is fixed and $q(t)$ given, $p_i$ is completely determined. 

Now by definition, $\frac{d S}{d t} = L$ by definition. On the other hand, using the chain rule,
```{math}
L = \frac{d S}{dt} = \frac{\del S}{\del t} + \frac{\del S}{\del q^i}{\dot q^i} =  \frac{\del S}{\del t} + p_i {\dot q^i}
```
Since $H =  p_i {\dot q^i} - L$, we have 
```{math}
:label: ds_dt
\frac{\del S}{\del t} = - H
```
Thus if we consider $S$ as a function of $q(t), t$, its variation $dS$ under infinitesimal variations $dq^i, dt$ of its arguments is
```{math}
dS = p_i dq^i - H dt
```
We have also shown that
```{math}
\frac{\del S}{\del t} + H(q^i, p_i = \frac{\del S}{\del q^i}) = 0
```
when evaluated along classical trajectories. This is the *Hamilton-Jacobi* equation; the function $S$ is called *Hamilton's principle function*.

We have shown that by knowing the classical trajectories $q^i(t), p_i(t)$ given fixed initial conditions, the equations {eq}`ds_dq` and {eq}`ds_dt` furnish a solution $S$ to the Hamilton-Jacobi equations. Furthermore, this solution is the classical action as a function of the endpoint $q(t)$ given $q(t_i)$. Returning to the quantum problem, if we consider the time-*dependent* Schroedinger equation
```{math}
i\hbar \del_t \psi = - \frac{\hbar^2}{2m} \nabla^2 \psi + V(q) \psi
```
and write $\psi = e^{i\frac{S(q,t)}{\hbar}$ with $S = S_{cl} + \hbar S_1 + \ldots$, then the leading order $\cO(\hbar^{0})$ equation is the full Hamilton-Jacobi equation. 

The equation {eq}`ti_hj` is consistent with the full Hamilton-Jacobi equations if we set
```{math}
S = W(q^i(t)) - E t
```
where $W$ is called *Hamilton's characteristic function*; here $p_i = \frac{\del W}{\del q^i}$, or $dW = p_i dq^i$. The solution is also consistent with the classical ewuations of motion for the family of trajectories with fixed energy. The functional form will be different from the solution with fixed initial conditions, as the corresponding trajectories will have varying energy (consider the 1d case of force-free motion where we fix $t$ and vary $q$ given an initial condition; this will be a family of trajectories with increasing velocity and thus energy).

What we are seeing is that different solutions to the H-J equations with different specified constants yield different families of trajectories. To understand this we consider a different perspective on these equations.

### Canonical transformations in phase space

Last semester we briefly touched on canonical transformations as transformations in phase space which preserve the Poisson brackets and the Hamiltonian structure of the problem. That is, start with some system for which the phase space variables are $q^i, p_i$, $i \in \{1,\ldots,n\}$, such that $\{q^i, q^j\} = \{p_i, p_j\} = 0$, and $\{q^i,p_j\} = \delta^i_j$. Assume further there is a Hamiltonian $H(q,p)$ such that the system satisfies Hamilton's equations. A canonical transformation is  coordinate transformation *in phase space* to new coordinates $Q^I(q,p), P_I(q,p)$, $I - \{1,\ldots,N\}$ such that
```{math}
\{Q^I, Q^J\} = \{P_I, P_J\} = 0\ ; \ \ \{Q^I, P_J\} = \delta^I_J
```
and such that there is function $K(Q,P)$ for which Hamilton's equations for $q,p,H$ become, under the coordinate transformation, Hamilton's equations for $Q,P,K$:
```{math}
\begin{align}
\frac{d Q^I}{d t} & = \frac{\del K}{\del P_I}\\
\frac{d P_I}{d t} & = - \frac{\del K}{\del Q^I}
\end{align}
```
Following the previous discussion, these are consistent with the trajectory being the minimum of the phase space action
```{math}
S' = \int_{t_i}^t dt' \left(P_I {\dot Q}^I - K\right)
```
or in differential form, $dS' = P_I dQ^I - K dt$.

The variation of $S,S'$ yields the same equations of motion if $dS = dS' + dF$ where $F$ is a function of coordinates, momenta, and time; integrating this along a trajectory, it will only contribute to the endpoints and thus not appear in the equations of motion. (Note that in principle stationarity works if $dS' + dF = \lambda dS$ for some constant $\lambda$. But we can scale $\lambda$ away, by rescaling $P,Q,K$ and rewriting the form of $K$, so we will ignore this. (See chapter 10 of {cite:p}`goldstein2002classical` for a discussion of this point). 

As it happens, however, $F$ determines the coordinate transformation. That is, if we write
```{math}
dF = p_i dq^i - P_I dQ^I - Hdt + Kdt
```
or equivalently
```{math}
\frac{dF}{dt} = p_i {\dot q}^i - P_I {\dot Q}^I + (K  - H)
```
The differential version treats $q, Q$ as the independent coordinates. Thus, we have
```{math}
\begin{align}
p_i & = \frac{\del F}{\del q^i}\\
P_I & = - \frac{\del F}{\del Q^I}\\
K & = H + \frac{\del F}{\del t}
\end{align}
```
If we specify $F(q, Q, t)$, then, the equations above give $p(q,Q,t)$, $P(q, Q, t)$, $K$. We can then solve for $Q, P$ in terms of $q, p$.

On the other hand, writing $P dQ = d(PQ) - Q d P$, we can instead consider the equation
```{math}
d(F + P_I Q^I) = p_i dq^i + Q^I dP_I - Hdt + Kdt
```
If we set $\Phi = F + P_I Q^I = \Phi(q_i, P^I)$ we get a different set of coordinate transformations determined by $\Phi$, with 
```{math}
\begin{align}
p_i & = \frac{\del \Phi}{\del q^i}\\
Q^I & = - \frac{\del \Phi}{\del P_I}\\
K & = H + \frac{\del \Phi}{\del t}
\end{align}
```
We can consider similar generating functions that are functions of $p, P$ or of $p, Q$. These are typically classified into four types, dependening on which pair of old and new variables they are explicitly functions of.

Let us therefore consider coordinates $Q^I, P_I$ that are constant in time along trajectories. These could be the initial conditions or any other set of $2n$ bits of data that label the trajectories. The corresponding Hamiltonian $K$ is therefore constant by Hamilton's equations and can be set to zero. Then we are left with 
```{math}
K = 0 = H + \del_t F_2(q,P,t)
```
where we have set $S = F_2$ to tie this to the discussion in Section 9.1 of {cite:p}`goldstein2002classical`. The variables $P_I$ appear as explicit constants of motion; we are guaranteed that $Q^I = - \frac{\del F_2}{\del P^I}$ is also constant. The equation above becomes the Hamilton-Jacobi equation
```{math}
H(q_i, p_i = \frac{\del F_2}{\del q^i}, t) + \frac{\del F_2}{\del t}
```
In the original derivation we specified $q^i(t_i)$. But as long as we have a *complete solution* with $n$ independent integration constants, then we can invert the coordinate transformations to find $q^i(Q^I, P_I, t)$, that is, we generate a trajectory.

### Canonical transformations and the HJ equation

In this context, if the Hamiltonian is time-independent, we can choose a solution of the form $F_2 = S = W(q,E) - Et$. $E$ now becomes one of the constants of motion: the resulting equation
```{math}
H(q^i, p_i = \frac{\del W}{\del q^i}) = E
```
A complete solution will require $n-1$ additional constants of motion.

The simplest interesting example is the 1d simple harmonic oscillator. Considering solutions of fixed energy, we have
```{math}
\frac{\del S}{\del x} = \sqrt{2m(E - \half m \omega^2 x^2)}
```
We can do an integral to find
```{math}
S = \int^x dx\sqrt{2m(E - \half \omega^2 x^2)} - E t
```
up to a constant of integration which we can absorb in to $S$ without changing the fact that $S$ solves the H-J equation.

By the above discussion, $\del_E S$ is a constant of motion, which we will call $\beta$, so that
```{math}
\beta = \int dx \sqrt{\frac{m}{2}}\frac{1}{\sqrt{2m(E - \half \omega^2 x^2)}} - t
```
is constant; again the constant of integraion unspecified by the indefinite integral can be absorbed into $\beta$. The result is
```{math}
t + \beta = \frac{1}{\omega}\sin^{-1} x \sqrt{\frac{m\omega^2}{2E}}
```
or
```{math}
x = \sqrt{\frac{2E}{m\omega^2}} \sin(\omega (t + \beta))
```
This is the general solution; the constants of motion are $E$ and the time $-\beta$ at which $x = 0$. The latter can be shifted away with a shift in time.

### The method of characteristics

The flip side of this, relevant for the quantum problem, is that if we have a family of solutions $q^i(t)$ to the equations of motion, we have a solution to the Hamilton-Jacobi equation. That is, let us assume we know $S(q^i(t_0),t_0)$ (the initial condition) at some time $t_0$. This yields $p_i(t_0) = \frac{\del S}{\del q^i}$. At each initial point we can thus generate a trajectory $q^i(t), p_i(t) = \frac{\del S}{\del q^i(t)}$. Along each trajectory, the partial derivative $\del_t S$ becomes a total derivative, so we have $d_t S + H(q^i(t), p_i(t)) = 0$. $H$ is a known function and the equations of motion yield known functions $q^i(t), p_i(t)$, so we have $d_t S + F(t) = 0$ which can be integrated, perhaps on a computer. We then know $S$ along the family of trajectories we have computed. This is a specific example of the *method of characteristics*. The process of turning the wave equation into an equation of Hamilton-Jacobi type, and then solving the katter via the method of characteristics, is a specific example of *ray tracing*. A similar procedure for exlectromagnetic waves, for example, moving through a medium with variable index of refraction, yields the geometric optics approximation, where the individual ``rays" are the characteristics of an associated Hamilton-Jacobi-like approximation to the full wave equation. 

A simple example is the case of the free particle, for which 
```{math}
\del_t S + \frac{1}{2m}(\del_x S)^2 = 0
```
The characteristic equations/Hamilton's equations are ${\dot x} = p$, {\dot p} = 0$, solved by $x(t) = x_0 + p_0 t/m$. Let us say we know that at $t = 0$, $S = \half \gamma x_0 ^2$. Then $p_0 = \gamma x_0$, and $x(t) = (1 + \gamma t/m) x_0$.

Now along this trajectory,
```{math}
\begin{align}
\del_t S + \frac{1}{2m} p(t) \del_x S & = \del_t S + \frac{1}{2} {\dot x} \del_x S \\
& = d_t S - \frac{1}{2m} p(t)^2 = 0
\end{align}
```
Now along the trajectory $x(t)$, $p(t) = p(0) = \gamma x_0$, so $d_t S = \frac{\gamma^2}{2m} x_0^2$ or
```{math}
\begin{align}
S & =  \half \gamma x_0^2 + \frac{\gamma^2}{2m} x_0^2 t \\
& = \half \gamma x_0^2\left(1 + \frac{\gamma}{m} t\right) \\
& = \half \gamma\frac{x(t)^2}{(1 + \gamma t/m)}
\end{align}
```
You can check that this solves the Hamilton-Jacobi equation.

## WKBJ as a semiclassical limit

The fact that the classical equations omf motion arise from the WKBJ approximation motivates the term *semiclassical limit*. You might think this is because it is an $\hbar \to 0$ limit; again, that is not quite right, since (as I keep ranting on and on about) $\hbar$ is a dimensionful parameter. 

I will sketch out a couple of ways to think about this limit. These are only sketches. Fleshing out the arguments in detail is non-trivial!

### Comment: large quantum numbers

In general the story is that $S_{cl}/\hbar \gg 1$. We can see what this means in terms of the simple harmonic ocillator. If $L \sim T - V \sim n \hbar\omega$, wheer $n$ is the excitation level of a state, we can guess that $S \sim n \hbar$. So $n \gg 1$ is the limit; that is, we have a limit of *large quantum numbers*.

Anther way we might see classical mechanics emerge is through Ehrenfest's theorem. For the potential problem, this states
```{math}
m \frac{d}{dt} \vev{x^i} = - \vev{\frac{\del}{\del x^i} V(x)}
```
This is exactly the classical equations of motion for $x^i$ if 
```{math}
 \vev{\frac{\del}{\del x^i} V(x)} = \frac{\del}{\del x^i} V(\vev{x^i})
```
As it happens this is trivially true for the SHO, for which the WKB approximation is known to be exact. More generally, if we write ${\hat x} = \vev{x} + \delta x$, we need that $\vev{x}^n \gg \vev{\delta x^n}$. The latter measures the spread of the wavefunction; we need this to be small compared to the range of variation of the position variable. This should be related to the kind of high-energy limit we are discussing in which the wavelengths used are small compared to the range of variation of the potential. We can realize this by constructing *coherent states* which realize these conditions explicitly.  In view of time, however, I will press on.

### Comment: the path integral picture

Let us return to the Feynman path integral for solutions to the time-*dependent* Schroedinger equation:
```{math}
\psi(x,t) = \int Dx e^{i S([x(t)])/\hbar}
```
This would yield the WKB approximation if the dominant contribution to the integral was $e^{i S_{cl}[x]/\hbar}$. As it happens, this emerges fairly naturally. I will sketch out a hand-waving description here.

Let us first consider the general 1d integral
```{math}
I(t) = \int dx e^{i t f(x)}
```
As $t \to \infty$, if $f(x)$ varies nontrivially with $x$, eg $f_x \sim \cO(1)$, the integrand will oscillate rapidly and the integral will vanish. The leading contributions to this integral occur when $f$ changes slowly, that is, near $f_x = 0$. In this region, we can write $f(x) = f(x_0) + \half (x - x_0)^2 f''(x_0) + \ldots$. If we insert this expansion into the integrand, 
```{math}
\begin{align}
I(t) & = \int dx e^{i t (f(x_0) + \half (x - x_0)^2 f''(x_0))}\left(1 + \frac{1}{4!}(x - x_0)^4 f^{(iv)}(x_0) + \ldots\right)\\
& = \sqrt{\frac{2 \pi}{t f''(x_0)}} \left(1 + \cO\left(\frac{1}{t^2}\right) + \ldots\right)
\end{align}
```
(we expect the cubic term  in the integrand to drop out as it is odd and the exponential even). The resulting leading-order approximation is known as the *stationary phase* approximation (and is related to the saddle-point approximation for more general integrals in the complex plane). 

If we assume that this approximation applies to the Feynman path integral, we should replace the point $x_0$ by the classical trajectory $x(t)$ about which $S$ is stationary. We are thus led to
```{math}
\psi(x,t) \sim e^{i S_{cl}[x(t)]/\hbar}
```
times a prefactor. Here $S$ is the classical action, and we have shown that it solves the Hamilton-Jacobi equation.

In general, this works when $S_{cl}/\hbar \gg 1$. In explicit examples, you can show that this ratio controls the corrections to the semiclassical approximation, whether you work in the path integral formulation or with the Schroedinger equation. Such large actions arise from highly excited states.

