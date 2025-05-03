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

### Linear potential

```{math}
V(x) = g |x|
```

Again this can be solved with Airy functions, but it is a pain and we can show that the variatoipnal method does well.

### Helium atom
