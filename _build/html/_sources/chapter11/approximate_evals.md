# Approximation schemes for eigenvalues

## Perturbative techniques

So far we have focused, for the most part, on exactly solvable problems. But no real world systems correspond to exactly solvable problems. However, they are often "very close" in some sense (which we will describe) to problems that are.

A classic example we already discussed is the general potential $V(x)$ near its minimum. For sufficiently low energy states, such that the wavefunciton dies off rapidly away from the minimum, we have
```{math}
V(x) = V(x_0) + \half V''(x_0) (x - x_0)^2 +frac{1}{6} V'''(x_0) (x - x_0)^3 + \ldots
```
If the terms higher than quadratic are small (which will be true when $(x - x_0)$ is small enough), we can consider the non-quadratic terms as a "small correction" to the quadratic terms. (How this happens in quantum mechanics when $x 1 x_0$ is an operator, not a number we can ask to be small, we will discuss below).

IN the case of the hydrogen atom, corrections from special relativity can break the large degeneracy due to teh Runge-Lenz vector. The first comes from the fact that for a free particle, the energy is 
```{math}
\begin{align}
E & = \sqrt{m^2 c^4 + p^2 c^2}\\
& \sim m c^2 + \frac{p^2}{2m} - \frac{p^4}{8 m^3 c^2} + \ldots
\end{align}
```
The second effect is the *spin-orbit coupling*. Crudely, the electron is moving through a Coulomb electric field. In its rest frame, it will feel a magnetic field due to the transformation of the Maxwell field under Lorentz boosts. The electron spin then couples to this magnetic field. Since the motion is due to an gular momentum, we can guess that the energy is something like ${\vec S}\cdot{\vec L}$. In practice we need to derive this from a fully relativistic treatment (eg by starting with the Dirac equation). The result is that the leadig correction is
```{math}
\delta H = \frac{e^2}{2 \mu^2 c^2 r^3} {\vec L}\cdot{\vec S}
```
We will have to show that these terms give small corrections to the spectra of teh Coulomb Hamiltonian.

## Non-perturbative techniques.

In some case the Hamiltonian is far from exactly solvable. Nonetheless, there are still domains for which there are powerful approximation techniques. For finding the groun state energy, the *variational method* works beautifully -- we simply adopt some mathematical model of the wavfunction and vary the parameters of this model to minimize the expectation value of the energy.

For highkly excited states, there is another approximation method known as teh WKB approximation. This works when the de Broglie wavelenth of the particle is small compared to the length scale over which the potential varies. Then we can consider essentially plane wave states, whose wavelength is varies over the rangel of the wavefunction.
