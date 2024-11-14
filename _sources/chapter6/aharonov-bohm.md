# The Aharonov-Bohm effect

The first system we will explore is a particle moving in a region containing a magnetic field. This allows us to explore the structure of quantum mechanics in a background electromagnetic field, and leads to a surprising consequence -- even when the field vanishes where the particle can move, it has a measurable effect on the particle's wavefunction.

## Charged particle in an electromagnetic field>

So far we have considered the case of a constant magnetic field. Here we will consider the more general case of an electromagnetic field. 

Two of Maxwell's equations,
```{math}
:label: bianchi_ident
\begin{align}
\frac{\del {\vec E}}{\del t} & = c {\vec\nabla}\times{\vec B}\\ 
{\vec\nabla}\cdot{\vec B} & = 0
\end{align}
```
imply that in a simply connected region, ${\vec E}$, {\vec B}$ can be written in the form
```{math}
:label: gauge_potentials
\begin{align}
{\vec E} & = - \frac{1}{c} \frac{\del {\vec A}}{\del t} - {\vec \nabla} \Phi\\
{\vec B} & = {\vec\nabla}\times{\vec A}
\end{align}
```
The fact that a single solution ${\vec A}, \Phi$ can generally only be found in a simply connected region will become important to us below.

The Lagrangian for a charged particle in this background is
```{math}
:label: em_lag
L - \half m {\dot{\vec x}}^2 + \frac{e}{c} {\dot{\vec x}}\cdot{\vec A} - q \Phi
```
where $q$ is the charge of the particle. Applying the Euler-Lagrange equation to this, combined with {eq}`gauge_potentials`, leads to the Lorentz force law
```{math}
:label: 
m {\ddot{\vec x}} = \frac{q}{c}{\vec{\dot x}}\times{\vec B} + q {\vec E}
```
As it happens we cannot simply write $L$ in terms of the physical field variables ${\vec E}, {\vec B}$. To get a sensible variational principle the Lagrangian needs to be written a s afunction of the vector and scalar potentials $\Phi, {\vec A}$. 

It is important to note that $\Phi, {\vec A}$ are ambiguously defined via {eq}`gauge_potentials`. If we shift 
```{math}
:label: gt_potentials
\begin{align}
{\vec A} & \to {\vec A} - {\vec\nabla}\Lambda \\
\Phi & \to \Phi + \frac{1}{c} \frac{\del \Lambda}{\del t}
\end{align}
```
then the electric and magnetic fields do not change. This shift in fact makes no real physical change: it is called a *gauge transformation* or *gauge symmetry*. You can show that the action $S = \int dt L$ changes only by boundary terms (that is, by the integral of a divergence), so that the gauge symetry is a symmetry of the dynamics. 

The Hamiltonian becomes
```{math}
:label: charged_particle_ham
H = \frac{1}{2m} \left({\vec p} - \frac{q}{c} {\vec A}({\vec x}, t)\right)^2 + q \Phi({\vec x},t)
```
where the canonical momentum is
```{math}
:label: charged_particle_cm
p_i = m {\dot x}^i + \frac{e}{c} A^i
```
Since ${\dot x}^i$ does not transform under gauge transformations, this means that $p_i$ does:
```{math}
:label: gauge_shift_p
p_i \to p_i - \frac{e}{c} \frac{\del \Lambda}{\del x^i}
```
Thus the first term in {eq}`charged_particle_ham` is gauge invariant. The last term shifs by
```{math}
H \to H + \frac{e}{c} \frac{\del}{\del t} \Lambda
```
This shift affects Hamiltons equations:
```{math}
\frac{d}{dt} p \to \frac{d]{dt} - \frac{e}{c} \frac{\del}{\del t} \frac{\del}{\del x^i} \Lambda
```
consistent with the gauge transformation of $p$.

In the quantum case, if we let $\psi(x,t) = e^{- i \frac{e}{\hbar c} \Lambda} \psi'$, then
```{math}
{\hat p}_i  e^{- i \frac{e}{\hbar c} \Lambda} \psi' = e^{- i \frac{e}{\hbar c} \Lambda} ({\hat p_i} - \frac{e}{c}\frac{\del \Lambda}{\del x^i})\psi'
```
Similarly, 
```{math}
i\hbar \frac{\del}{\del t} e^{- i \frac{e}{\hbar c} \Lambda} \psi' =  e^{- i \frac{e}{\hbar c} \Lambda} (i\hbar \frac{\del}{\del t} + \frac{e}{c} \frac{\del \Lambda}{\del t})\psi'
```
Thus, if we apply {eq}`gt_potentials` to $A,\Phi$ in the quantum Hamiltonian, and also shift $\psi \to e^{-i e\Lambda/(\hbar c)}\psi$, the Schroedinger equation remains unchanged.
