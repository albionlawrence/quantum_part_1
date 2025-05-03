# Transition amplitudes

## Solving the TDSE

Consider a Hamiltonian with the following structure
```{math}
H = H_0 + \eps V(t)
```
where we know the eigenvectors $\ket{n}$ of $H_0$ and the associated eigenvalues $E_n$. At any time $t$ we can expand our state in the basis $\ket{n}$ which we take to be orthonormal (as such a basis of eigenvectors of the Hermitian operator $H_0$ always exists).:
```{math}
\ket{\psi(t)} = \sum_n c_n(t) \ket{n}
```
We can then write the time-dependent Schroedinger equation
```{math}
i\hbar \del_t \ket{\psi(t)} = (H_0 + \eps V)\ket{\psi(t)}
```
as
```{math}
\sum_n i\hbar{\dot c}_n \ket{n} = \sum_n c_n(t)(E_n + \eps V)\ket{n}
```
taking the inner product with a specific eigenket $\bra{n}$ we have
```{math}
i\hbar {\dot c}_n = E_n c_n + \eps \sum_m \bra{n} V(t) \ket{m} c_m(t)
```
which is a coupled set of first order differential equations.

## The interaction picture

Now the first time on the right hand side is a nuisance and at any rate does not correspond to a change in teh amplitude of $c_n$. To see this, we redefine
```{math}
c_n(t) = {\tilde c}_n(t) e^{- i E_n t/\hbar}
```
Making this substitution, we find that the time derivative acting on $c_n$ includes a term that cancels the $E_n c_n$ term. The upshot is:
```{math}
:label: ip_tdse_exp
\begin{align}
i\hbar {\dot{\tilde c}}_n & = \sum_m \bra{n} \eps V\ket{m} e^{i (E_n - E_m) t/\hbar} {\tilde c}_m(t)\\
& = \sum_m \bra{n} e^{i H_0 t/\hbar} \eps V e^{-i H_0 t/\hbar} \ket{m} {\tilde c}_m\\
& \equiv  \sum_m \bra{n} \eps V_I(t) \ket{m} {\tilde c}_m(t)
\end{align}
```
where we define *interaction picture* operators as
```{math}
\cO_I(t) =  e^{i H_0 t/\hbar} \cO_S(t)  e^{-i H_0 t/\hbar}
```
Here $\cO_S(t)$ is a Schrodinger picture operator, which we have allowed to have explicit time-dependence (for example, if we want to subject a charged particle to a time-dependent electromagnetic field). We can also define the state in the interaction picture as
```{math}
\ket{\psi(t)}_I = e^{i H_0 t/\hbar} \ket{\psi(t)} = \sum_n {\tilde c}(t)\ket{n}
```
This is like the Heisenberg picture, but instead of evolving the actual state from $t$ back to $t = 0$ with the full Hamiltonian, we do so with the unperturbed Hamiltonian $H_0$. The difference between these two protocols is a measure of the degree of interaction. Indeed, we can see from equation {eq}`ip_tdse_exp` that the Schroedinger equation can be written as
```{math}
i\hbar \del_t \ket{\psi(t)}_I = \eps V_I(t) \ket{\psi(t)}_I
```
Since we are interested in transitions (changes of the state) induced by interactions, this formulation isolates the questions at hand.

