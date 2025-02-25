# Orbital Angular Momentum

Let us consider particles with no intrinsic spin. (Except for the Higgs boson, these will typically be composite particles such as atoms whose total spin vanishes, where we treat the atoms as point particles. Anothe rexample is the $\alpha$-particle which is a helium-4 nucleus, a spin-$0$ bound state of 2 protons and 2 neutrons.) If the particles are moving in $\mathbb{R}^3$, their Hilbert space is $L^2(\CR^3)$, and rotations act nontrivially. We can define the action of rotations in the position basis:
```{math}
U(R)\ket{\vec x} = \ket{\vec{R x}}
```
where $R$ is the $3\times 3$ matrix acting on vectors in $\CR^3$. Note that this means that
```{math}
\bra{x} U(R) = \bra{x} U^{\dagger}(R^{-1}) = \bra{(R^{-1} x}
```
Thus, if we let $\ket{\psi'} = U(R) \ket{\psi}$,
```{math}
\psi'(x) = \brket{x}{\psi'} = \bra{x} U(R)\ket{\psi} = \brket{R^{-1} x}{\psi} = \psi(R^{-1}x)
```
Let us conisder infinitesimal rotations by an angle $\theta$ about the $z$ axis, for which 
```{nath}
\begin{align}
x & \to x - \theta y\\
y & \to y + \theta x\\
z & \to z
\end{align}
```
Then
```{math}
\begin{align}
\psi'(x) & = \psi(x + \theta y, y - \theta x, z) = \psi(x) + \theta y\frac{\del}{\del x} \psi - \theta x \frac{\del}{\del y} \psi\\
& = {\bf 1} - \frac{i\theta}{\hbar} (J_z \psi)(x)
\end{align}
```
Since $\frac{\del}{\del x^i} = \frac{i}{\hbar} p_i$, we have
```{math}
J_z = {\hat x} {\hat p}_y - {\hat y} {\hat p}_x
```
Similar arguments yield
```{math}
\begin{align}
J_x & = {\hat y} {\hat p}_z - {\hat z}{\hat p}_y \\
J_y & = {\hat z} {\hat p}_x - {\hat x}{\hat p}_z
\end{align}
```
or
```{math}
{\vec J} = {\hat{\vec x}} \times {\hat{\vec p}}
```

If we replaced the operators by classical observables, there would just be the classical angular momenta. We can check that, acting on states, these have the correct commutation relations $[J_I, J_J] = i \hbar \epsilon_{IJK} J^K$.
