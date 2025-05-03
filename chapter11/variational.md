# The Variational Method

The next two techniques we wish to discuss are cases in which the Hamiltonian is not obviously close to solvable; thus, we consider them "nonperturbative". These are the variational method and the WKBJ approximation. Essentially, the former works for ground state energies and the latter for highly excited states. 

The essential point is as follows. Consider any state $\ket{\psi}$. We will not worry about normalization; the expectation value ofthe Hamiltonian (the average of the measured energy over many measurements) is:
```{math}
\vev{E} = \frac{\bra{\psi} H ket{\psi}}{\brket{\psi}{\psi}}
```
Now insert a resolution of the identity ${\bf 1} = \sum_n \ket{n}\bra{n}$ where the sum is over all energy eigenstates starting with the ground state $n = 0$. Then
```{math}
\begin{align}
\vev{E} & = \frac{\brket{\psi}{n}\bra{n} H \ket{\psi}}{\brket{\psi}{\psi}}\\
& = \sum_n E_n \frac{\brket{\psi}{n}\brket{n}{\psi}}{\brket{\psi}{\psi}}\\
& \geq E_0 \sum_n  \frac{\brket{\psi}{n}\brket{n}{\psi}}{\brket{\psi}{\psi}} = E_0
\end{align}
```
where we have used $E_n \geq E_0$. Thus any such expectation value is bounded from below by the ground state energy.

The variational principle uses this by starting with a family of states $\ket{\psi,\lambda}$ where $\lambda$ indexes that family; we then minimize $\vev{E}$ over $\lambda$, to get an estimate of the ground state energy. This is worthwhile if we want to get an estimate of how this energy depends on parameters of teh Hailotnian, for example, in situations for which the spectrum of the Hamiltonian cannot be solved for even in perturbation theory.

The essential reason this can work is as follows. Let us say we guess the ground state wavefunction with some error, $\ket{\psi} = \ket{0} + \eps \ket{err}$ where $\brket{err}{0} = 0$. Then
```{math}
\vev{E} = E_0 + \eps^2 \frac{\bra{err} H \ket{err}}{1 + \eps^2 \brket{err}{err}}
```
Thus the error in our esptimate of $E_0$ is smaller by $\cO(\eps)$ than our error in guessing the state.

The trick is to find a set of trial states for which 
1. We know how to compute $\vev{H}$, and
2. For which we can guess, based on simple principles, that the family overlaps strongly with the ground state. For bound state problems in one dimension, we can first ensure that the wavefunction has no nodes, and that it falls off at infinity. If the potential is parity-symmetric, we can guess that the ground state wavefunction is also and choose a family of trial wavefunctions which are also parity symmetric.

Past this point, it is most illumating to work through some examples.

### Infinite square well

We know how to solve this; the point is to see how well the variational technique works.

We consider a 1d square well:
```{math}
V(x) = \begin{cases} \infty & x \leq -L \\ 0 & -L < x < L \\ \infty & x \geq L \end{cases}
```
As a reminder, the ground state eigenfunction is
```{math}
\psi_n(x) = \frac{1}{\sqrt{L}} \cos\left(\frac{\pi x}{L}\right)
```
and the energy is
```{math}
E_0 = \frac{\hbar^2\pi^2}{8 m L^2}
```

Now let us pretend we didn't know this. We do know that the wavefunction has to vanish for $|x| \geq L$, and that as a ground state it should have no nodes, and be parity even. We will throw caution to the wind and try
```{math}
\psi(x) = |L|^{\lambda} - |x|^{\lambda}
```
A short computation yields
```{math}
\vev{E} = \frac{(\lambda + 1)(2\lambda + 1)}{2\lambda - 1} \frac{\hbar^2}{4 m^2 \eps^2}
```
This is minimized when
```{math}
\lambda = \frac{1 + \sqrt{6}}{2} \sim 1.72
```
for which
```{math}
\vev{A} = \frac{5 + 2\sqrt{6}}{\pi^2} E_0 \sim 1.003 E_0
```
SO even with this ridiculous wavefunction we get $.3\%$ accuracy.  Note that we also get the parametric dependence of $E$ on $\hbar, m, L$ (though dimensional analysis would have done the job in this case -- you should convince yourself of this!).

### Linear potential

Next, consider the potential
```{math}
V(x) = g |x|
```
This can be solved with Airy functions, but it is a pain and we can show that the variational method does well. The actual ground state energy is
```{math}
E_0 \sim .8086 \left(\frac{g^2 \hbar^2}{m}\right)
```

Again, we demand parity symmetry, the lack of nodes, and normalizability (also of the expectation value of the Hamiltonian, since $V$ grows linearly). A good trial wavefunction is
```{math}
\psi = \left(\frac{2\alpha}{\pi}\right)^{1/4} e^{-\alpha x^2}
```
which we have selected to be properly normalized. The parameter $\alpha$, the width of the Gaussian, is what we will vary.

Now
```{math}
\vev{E} = \int_{-\infty}^{\infty} dx \psi^*(x) \left[- \frac{\hbar^2}{2m} \frac{\del^2}{\del x^2} + g|x|\right) \psi(x) = \frac{\hbar^2\alpha}{2m} + \frac{g}{\sqrt{2\pi \alpha}
```
The minimum is determined by
```{math}
\frac{\del \vev{E}}{\del \alpha} = \frac{\hbar^2}{2m} - \frac{g}{2\sqrt{2\pi} \alpha^{3/2}} \Rightarrow \alpha = \left(\frac{m g}{\sqrt{2\pi} \hbar^2}\right)^{2/3}
```
Some algebra finally gives us
```{math}
\vev{E} = \frac{1}{\pi^{1/3}}\left(\frac{1}{2^{4/3}} + \frac{1}{2^{1/3}}\right)\left(\frac{g^2 \hbar^2}{m}\right)^{1/3} \sim .813 \left(\frac{g^2 \hbar^2}{m}\right)^{1/3}
```
which is a $.5\%$ error.

### Helium atom

Finally, a more realistic situation is that of the Helium atom, with fixed nucleaus and Hamiltonian for the electrons:
```{math}
H = \frac{{\vec p}_1^2}{2m} + \frac{{\vec p}_2^2}{2m} - \frac{2 e^2}{r_1} - \frac{2 e^2}{r_2} + \frac{e^2}{|{\vec r}_1 - {\vec r}_2|}
```
here ${\vec r}_i$ is the distance of each electron to the nucleus.

Now as it happens, the ground state is in a spin singlet state. One standard argument is that if we make an approximation that the electron-electron interaction is absent, the gorund state is clearly one in which each electron is in the ground state of the coulomb problem with a charge-2 nucleus. This is symmetric, so by the Pauli principle (which we have not yet discussed!) the spin degrees of freedom are antisymmetric.

To movivate the choice of a trial wavefunction, we postulate that each electron will provide a partial screening of the charge of the nucleus. Thus, we choose the wavefunction
```{math}
\psi(x_1,x_2) = \left(\frac{Z^3}{\pi a_0^2}\right) e^{- Z(r_1 + r_2)/(2 a_0)}
```
where $a_0$ is the Bohr radius of the hydrogen atom. This is the product of the ground state wavefunction for each electron in a Coulomb potential created by a nucleus with positive charge $Z e$. We then compute $\vev{E}$ and vary it with respect to $Z$. 
```{math}
\vev{E} = - 2 \frac{m e^4}{2\hbar^2} \left(4 Z - Z^2 - \frac{5}{8} Z\right)
```
This is minimized when $Z = \frac{27}{16}$ which we note is between $1$ and $2$, so it is consistent with our heuristic of the nucleus being partially screened by the electron.

The actual ground state energy can be measured as
```{math}
E_0 = - 78.8\ eV
```
We can try to compute this by treating the electron-electron interaction as a perturbation, with the unperturbed wavefunction being the product of the relevant ground states of the $Z = 2$ Coulomb problem. This yields:
```{math}
E_0^{pert} = - 74.8\ eV
```
which is a $5\%$ error. Not too bad! The variational calculation, however, yields
```{math}
E_0^{var} = - 77.5\ eV
```
which is a $1.6\%$ error, even better.
