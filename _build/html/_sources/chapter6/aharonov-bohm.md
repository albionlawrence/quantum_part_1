# The Aharonov-Bohm effect

The first system we will explore is a particle moving in a region containing a magnetic field. This allows us to explore the structure of quantum mechanics in a background electromagnetic field, and leads to a surprising consequence -- even when the field vanishes where the particle can move, it has a measurable effect on the particle's wavefunction.

## Charged particle in an electromagnetic field

So far we have considered the case of a constant magnetic field. Here we will consider the more general case of an electromagnetic field. 

### Gauge potentials

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

### Classical mechanics

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
\frac{d}{dt} p \to \frac{d}{dt} - \frac{e}{c} \frac{\del}{\del t} \frac{\del}{\del x^i} \Lambda
```
consistent with the gauge transformation of $p$.

### Quantum case

In the quantum case, if we let $\psi(x,t) = e^{- i \frac{e}{\hbar c} \Lambda} \psi'$, then
```{math}
{\hat p}_i  e^{- i \frac{e}{\hbar c} \Lambda} \psi' = e^{- i \frac{e}{\hbar c} \Lambda} ({\hat p_i} - \frac{e}{c}\frac{\del \Lambda}{\del x^i})\psi'
```
Similarly, 
```{math}
i\hbar \frac{\del}{\del t} e^{- i \frac{e}{\hbar c} \Lambda} \psi' =  e^{- i \frac{e}{\hbar c} \Lambda} (i\hbar \frac{\del}{\del t} + \frac{e}{c} \frac{\del \Lambda}{\del t})\psi'
```
Thus, if we apply {eq}`gt_potentials` to $A,\Phi$ in the quantum Hamiltonian, and also shift $\psi \to e^{-i e\Lambda/(\hbar c)}\psi$, the Schroedinger equation remains unchanged.

## The Aharonov-Bohm effect

Now we consider the setup show below, which is a modification of the classic double slit experiment (we will review this below since we haven't covered it yet). A source of some particle at $x = x_{source}$, which we take to produce particles in the same state each time, is behind a screen at $x = 0$ with two slits. The effect of the screen is to split the state into two wavepackets, $\psi_1({\vec x}, t)$ and $\psi_2({\vec x}, t)$. We also assume that if we block slit 1(2) the system is in state $A_1 \psi_1$($A_2 \psi_2$), where $A_i$ enforces $\int d^2 x |A_i|^2 |\psi_i|^2 = 1$. With both slits open the particle is in state $\psi({\vec x},t) = \psi_1 + \psi_2$ such that $\int d^2 x |\psi_1 + \psi_2|^2 = 1$. Note that we are ignoring the $z$ direction here, we can assume that the particles move more or less at $z = 0$, or that the wavefunction is more or less constant in the $z$ direction.

Now let us place a detector with resolution $\delta$ that detects the $y$ position of the particle, ad $x = x_{meas}$. The probability that the particle is detected at $y$ within resolution $\delta$ is
```{math}
:label: detection_prob
p(y,\delta) = |\psi_1 + \psi_2|^2 \delta = \delta\left(|\psi_1|^2 + |\psi_2|^2 + \psi_1^* \psi_2 + \psi_2^* \psi_1\right)
```
The typical story is that $\psi_i(x_{screen},y,t) = \sim f_i(y,t) e^{i k y}$ where $f$ is some envelope function. If we block either screen, we see that envelope function, but if we do not, then we see interference patterns. The point is that the probabilities do not add, the wavefunctions do.

Now let is place a solenoid S just behind the screen. We assume we can arrange it so that $\psi_i$ has negligible support near the solenoid. The solenoid produces a magnetic field ${\vec B} = B{\hat z}$ in the $z$ direction inside, with total magnetic flux $\int_{interior} d^2 x B = \Phi$.

Outside the solenoid, ${\vec B} = 0$. We thus might be tempted to assume that we can set ${\vec A} = 0$. However, we can only do this everywhere in a simply connected region and the region outside of the solenoid fails to be simply connected. This is why I was careful to state that we can solve ${\vec B} = {\vec\nabla} \times{\vec A}$ for ${\vec A}$ in a simply connected region. Consider two overlapping regions $R_1, R_2$ as shown, and take a path $C = C_1 + C_2$ around the solenoid that passes through both of them at $z = 0$, such that $C_i$ lies in region $R_i$. By Stoke's theorem,
```{math}
:label: stokes_theorem
\oint d{\vec l}\cdot({\vec\nabla}\times{\vec A}) = \int_R d^2 x B_z = \Phi = \oint_{C_1}d({\vec l}\cdot({\vec\nabla}\times{\vec A}) + \oint_{C_2}d{\vec l}\cdot{\vec\nabla}\times{\vec A})
```
Now in region $R_1$ or $R_2$ we could set ${\vec A} = 0$ but by the above, we cannot do so in both. If ${\vec A}_i$ is the vector potential in region $R_i$, then in the overlap regions, we must have ${\vec A}_1 = {\vec A}_2 + {\vec\nabla} \Lambda$; they are related by a gauge transformation. 

Now, what do our wavefunctions look like? Outside of the solenoid, they satisfy the time-dependent Schroedinger equation
```{math}
:label: ab_tdse
- \frac{\hbar^2}{2m} \left(-i {\vec\nabla} = \frac{e}{c} {\vec A}\right) \psi = i\hbar \del_t \psi
```
where I have started using the notation $\del_t = \frac{\del}{\del t}$. Now in a region $R_i$, we can write
```{math}
:label: shifted_wavefunction
\psi_i({\vec x},t) = e^{\frac{i e}{c} \int_{x_0}^{\vec x}d{\vec l}\cdot A} \phi_i
```
where the line integral stays in region $R_i$. Using this,
```{math}
(-i{\vec \nabla} - \frac{e}{c} {\vec A})\psi_i = e^{\frac{i e}{c} \int_{x_0}^{\vec x}d{\vec l}\cdot A} (-i{\vec\nabla})\phi_i
```
so that
```{math}
- \frac{\hbar^2}{2m}\nabla^2 \phi_i = i\hbar \del_t \phi_i
```
and $\phi_i$ are the wavefunctions for the double slit experiment absent the screen. 

We assume that the wavefunction $\phi_i$ has support only in $R_i$, so that we can unambigoulsy write $\psi_i$ via the above shift. Now let us measure the position of the particle at $x_{meas}$. 
