# Dynamics I

Before continuing to specific systems, we want to make a couple general comments on dynamics.

## Energy-time uncertainty

The position-momentum uncertainty principle is often complemented with an energy-time uncertainty principle:
```{math}
:label: energy-time-unc
\Delta E \delta t \geq \frac{\hbar}{2}
```
This could be argued for, for example, by noting that the energy is a component of a four-vector for which the spatial momenta are also components, $p^{\mu} = (E/c, {\vec p})$, and similarly for time and space: $x^{\mu} = (ct, {\vec x})$. But that isn't the strongest argument, and at any rate we are dealing with non-relativistic theories. For starters, in this case $t$ is a parameter not an operator. 

Another handwaving argument is that if we measure a system over a finite time $\Delta t$, the measurement process itself violates time translation invariance. In quantum mechanics as well as in classical mechanics, the conservation of energy follows from this invariance; thus in a measurement $E$ is no longer conserved.

But we can make a more precise statement that gives some definition of $\Delta t$. Let $H$ be the Hamiltonian and $A$ some Hermitian operator. We have already shown that
```{math}
:label: et-precise
\begin{align}
(\Delta H)^2 (\Delta A)^2 & \geq \frac{1}{4} \Big|\bra{\psi} [H,A]\ket{\psi}\Big|^2\\
& = \frac{1}{4} \Big| i\hbar \bra{\psi}\frac{\del A}{\del t}\ket{\psi}\Big|^2\\
& \Rightarrow \Delta E \left(\frac{\Delta A}{\vev{\frac{\del A}{\del t}}}\right) \geq \frac{\hbar}{2}
\end{align}
```
If we define $\Delta H \equiv \Delta E$ and
```{math}
\Delta t = \frac{\Delta A}{\vev{\frac{\del A}{\del t}}}
```
then we get our uncertainty principle. We can ghink of $\Delta t$ as the time it takes for $\vev{A}$ to change by an amount $\Delta A$ -- that is, the time scale for a change in the state to be noticeable.

## Conservation of probability

We have noted before that $\psi^*({\vec x}\psi({\vec x})$ is a probability *density*; one integrates it over a region to find the probability that a particle lives in that region.

Now the total probability in a system must be $1$. But over time, the probability that a particle is found in a given region *can* change; however it must change in such a way that the integrated probability does not.

To see how this works, we can use the Schroedinger equation and compute:
```{math}
:label: cont_eqn
\begin{align}
\frac{\del}{\del t} \psi^*\psi & = \frac{\hbar}{2im} (\nabla^2\psi^*\psi - \psi^* \nabla^2 \psi)\\
& = \vec{\nabla}\cdot\left(\frac{\hbar}{2im}\right)\left({\vec\nabla}\psi^* \psi - \psi^* {\vec{\nabla}}\psi\right)
\end{align}
```
Note how the potential has dropped out of this equation. If we define the probability current as:
```{math}
:label: prob_current
{\vec J}_{prob} = \frac{\hbar}{2im} \left(\psi^* {\vec\nabla}\psi - ({\vec\nabla}\psi^*) \psi\right)
```
and the probability density as:
```{math}
:label: prob_dens
\rho = \psi^*\psi
```
then we get the continuity equation
```{math}
:label: continuity_eqn
\frac{\del \rho}{\del t} + {\vec\nabla}\cdot{\vec J} = 0
```
That is, the change of probability in a region is due to the flux of ${\vec J}$ into and out of that region. This guarantees the conservation of probability in the entire space so long as ${\vec J}$ vanishes quickly enough at infinity. 
