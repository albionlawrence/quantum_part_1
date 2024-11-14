# The Schroedinger wave function and its dynamics


## Operators and expectation values

Consistent with the rules ${\hat x}^i \ket{\psi} = \ket{x^i \psi}$, and ${\hat p}_i \ket{\psi} = \ket{\frac{\hbar}{i}\frac{\del}{\del x^i}\psi}$, we simply write
```{math}
\begin{align}
& x^i: \psi \to x^i\psi\\
& p_i: \psi \to \frac{\hbar}{i} \frac{\del}{\del x^i} \psi
\end{align}
```

To find inner products, recall that $\brket{\chi}{\psi} = \int d^d x \chi^*(x) \psi(x)$. Thus
```{math}
:label: op_ev
\begin{align}
& \bra{\chi}{\hat x}^i \ket{\psi} = \brket{\chi}{x^i\psi} = \int d^d x \chi^*(x) x^i \psi(x)\\
& \bra{\chi}{|hat p}^i \ket{\psi} = \int d^d x \chi^*(x) \frac{\hbar}{i} \frac{\del}{\del x^i} \psi(x)
\end{align}
```

It is easy to show from this representation that ${\hat x}, {\hat p}$ are Hermitian. To see this, recall that the adjoint map takes $O\ket{\chi} \to \bra{\chi}O^{\dagger}$. We want to show that $\bra{\chi}O\ket{\psi} = \bra{\chi}O^{\dagger}\ket{\psi}$ for all $\ket{\chi},\ket{\psi}$. for the position operator, $x^i\ket{\chi} = \ket{x^i\chi}$ and $\bra{x^i \chi} = \bra{\chi}(x^i)^{\dagger}$. But
```{math}
\begin{align}
\brket{x^i \chi}{\psi} & = \bra{\chi}(x^i)^{\dagger}\ket{\psi}\\
& = \int d^d x (x^i \chi)^* \psi \\
& = \int d^d x \chi^* x^i \psi \\
& = \int d^d x \chi^*(x^i\psi) = \bra{\chi} x^i \ket{\psi}
\end{align}
```
so that $x^i = (x^i)^{\dagger}$. 

For ${\hat p}_i$ it is slighly more complicated. Now since 
```{math}
{\hat p}_i \ket{\chi} = \ket{\frac{\hbar}{i}\frac{\del}{\del x^i}\chi}
```
this mwans that
```{math}
\begin{align}
\brket{\frac{\hbar}{i}\frac{\del}{\del x^i}\chi}{\psi} & = \bra{\chi}{\hat p}_i^{\dagger}\ket{\psi}\\
& = \int d^d x (\frac{\hbar}{i}\frac{\del\chi}{\del x^i})^*\psi\\
& = - \int d^d x \frac{\hbar}{i} \frac{\del \chi^*}{\del x^i} \psi\\
& = \int d^d x \chi^* \frac{\hbar}{i} \frac{\del}{\del x^i} \psi\\
& = \bra{\chi} {\hat p}_i \ket{\psi}
\end{align}
```
where in the second to last line we integrated by parts. Since teh functions must be square integrable, they vanish at infinity, and the bounary term you get from integrating by parts should vanish also.


## Wave equation

We have to date discussed quantum mechanics in terms of abstract vector spaces, including the space of functions. In the case of particles moving in space, we have argued that this vector space is the vector space of square-integrable functions. In the case of particles in $d$ dimensions this is $L^2(\CR^d)$, that is, complex functions on $\CR^d$ which satisfy 
```{math}
\int d^d x |\psi({\vec x})|^2 < \infty
```

In general we expect that we can write the dynamics of the states in terms of the function $\psi$. First, since any state at any time can be represented by a complex function $\psi$, we can write it as $\ket{\psi(x,t)}$ .For the Hamiltonians such as 
```{math}
:label: 3d_ham
H = \frac{{\hat{\vec p}}^2}{2m} + V({\vec x})
```
or {eq}`mag_field_ham`, the quantum dynamics can be easily written as local partial differential equations for $\psi(x,t)$. Using the actions
```{math}
\begin{align}
{\hat p}_i \ket{\psi({\vec x},t)} & = \ket{\frac{\hbar}{i} \frac{\del}{\del x^i} \psi(x,t)}\\
{\hat x}^i \ket{\psi} & = \ket{x^i \psi({\vec x},t)}\\
\frac{\del}{\del t} \ket{\psi} & = \ket{\frac{\del}{\del t}\psi}
\end{align}
```
This last can be shown via representing the derivative as the limit of a difference between $\psi(x,t+\eps) - \psi(t)$, and using the linearity of quantum mechanics which means that 
```{math}
\ket{\psi(t+\eps)} - \ket{\psi(t)} = \ket{\psi(t+\eps) - \psi(t)}
```
The upshot of this is that the time-dependent Schrodinger equation can be written as
```{math}
:label: 3d_wave_eqn
- \frac{\hbar^2}{2m} {\vec\nabla}^2 \psi({\vec x}, t) + V({\vec x}) \psi({\vec x},t) = i\hbar \frac{\del}{\del t} \psi({\vec x}, t)
```
Relatedly, the time-*independent* Schrodinger equation for energy eigenstates becomes
```{math}
:label 3d_evalue
- \frac{\hbar^2}{2m} {\vec\nabla}^2 \psi({\vec x}, t) + V({\vec x}) \psi({\vec x},t) = E \psi({\vec x}, t)
```
Practically speaking, this is the form we work with for particles moving in space -- for the simple harmonic oscillator, or particles in a magnetic field (eg in the quantum hall systems), the hydrogen atom (ignoring spin), and so on. In the end, though, we should remember we are working with a vector space, and that the Schrodinger equation remains a linear equation.
