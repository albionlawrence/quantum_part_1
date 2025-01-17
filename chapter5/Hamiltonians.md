# Designing Hamiltonians

(section:lattice)=
## Free particle on a lattice

Let us start with a particle on an $N$-site lattice with periodic boundary conditions. We assume that there is a binding energy $E = - |E|$ at each site, and a hopping rate $A/\hbar$ between *adjacent* sites. Since $A$ has units of energy, a natural Hamiltonian is
```{math}
:lable: hopping_ham
H_{ij} = E \delta_{ij} - A \delta_{i,i+1} - A\delta_{i,i-1}
```
where $i \equiv i \pm N$. In matrix form this is
```{math}
H = \begin{pmatrix} E & -A & 0 & \ldots & 0 \\
-A & E & -A & \ldots & 0 \\
0 & -A & E & \ldots & 0 \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
\vdots & \vdots & \vdots & E & -A \\
0 & 0 & \ldots & -A & E \end{pmatrix}
```

How does this act on wavefunctions? In the basis of position eigenstates,
$\ket{\psi} = \sum_{k=0}^{N-1}\psi(x_k)\ket{x_k}$, we have
```{math}
H\ket{\psi} = \sum_{k=0}^{N-1} \left(E\psi(x_k) - A (\psi(x_{k+1}) + \psi(x_{k-1}))\right)\ket{x_k}
```
Writing 
```{math}
	\psi(x_k) = \frac{1}{\sqrt{N}} \sum_{m=0}^{N-1} e^{2\pi i m k/N} {\tilde\psi}(m)
```
and 
```{math}
\ket{x_k} = \frac{1}{\sqrt{N}} \sum_m e^{-2\pi i m k/N}\ket{\phi_m}
```
we can show after some work that 
```{math}
H\ket{\psi} = \sum_m \left(E - 2 A \cos \frac{2\pi m}{N}\right) {\tilde \psi}(m)\ket{\phi_m}
```
Now let us assume we are looking near the continuum limit. We expect that the wavefunction should involve wavelengths that are much larger than the lattice spacing, so that the lattice becomes irrelevant. In this case we expect that only terms in the sum with $m \ll N$ really contribute, as we can approximate it by
```{math}
H\ket{\psi} = \sum_m \left(E - 2A + A\frac{(2\pi m)^2}{N^2}\right) {\tilde \phi}(m) \ket{\phi_m}
```
Defining $m = R p/\hbar$, we can rewrite
```{math}
H \sim (E - 2A) + A\left(\frac{\eps}{\hbar}\right)^2 {\hat p}^2 + \ldots
```
The constant term leads to a constant phase $e^{-i (E = 2A) t/\hbar}$ in front of all states; this contributes nothing to any measureable quantity, and we can ignore it. For the second term we can define $m = \half \frac{\hbar^2}{A \eps^2}$, so that
```{math}
H \sim \frac{{\hat p}^2}{2m}
```
This looks very much like the Hamiltonian of a free particle, if this were classical mechanics!

We could also assume a varying binding energy $E + V_k$ at site $k$; thus if we define $V_k \equiv V(x_k)$ we would add to $H\ket{\psi}$
```{math}
\sum_{k=0}^{N-1} V(x_k) \psi(x_k) \ket{\psi} = V({\hat x}) \ket{\psi}
```
On the circle ${\hat x}$ does not make sense; however, if $V$ is a periodic function, $V({\hat x})$ can make sense. The resulting Hamiltonian is
```{math}
:label: 1d_ham
H = \frac{{\hat p}^2}{2m} + V({\hat x})
```
Note that here w have still assumed that the hopping rate *between* sites does not change. We are not choosing the most general Hamiltonian. 

Finally, we can assume that $H$ takes this form even on the continuum line, at which point there is no periodicity restriction on $V$. 

## Ehrenfest's theorem

The Hamiltonian {eq}`1d_ham` looks suspiciously like the Hamiltonian for a relativistic particle in a potential, with ${\hat p}$ taking the place of momentum. This is one reason we identify ${\hat p}$ with the momentum. To go further we wil consider how expectation values of ${\hat x}$, ${\hat p}$ change with time. Now recall that when we take expectation values,
```{math}
\vev{A} = \bra{\psi(x_0)} A_H(t) \ket{\psi(x_0)} = \bra{\psi(t)} A_S \ket{\psi(t)}
```
where the subscripts $H,S$ refer to the Schr\"odinger and Heisenberg picture, respectively. Let us work in the former. Now 
```{math}
\begin{align}
\left(\frac{{\hat p}^2}{2m}\right)_H & = U^{\dagger} \frac{{\hat p}^2}{2m} U\\
& = \frac{1}{2m} U^{\dagger} {\hat p} U U^{\dagger} {\hat p} U \\
& = \frac{{\hat p}_H^2}{2m} 
\end{align}
```
Similarly we can show that $(V({\hat x})_H = V({\hat x}_H)$ (assuming $V$ can be expressed in a power series in ${\hat x}$. Using {eq}`heisenberg_eom` we have
```{math}
\frac{d}{d t} x_H = \frac{1}{i\hbar} [x_H, H]
```
Note the similarity to Hamilton's equations in Poisson bracket form, if we take $[A,B]/i\hbar \to \{A,B\}$. To compute this we note that
```{math}
[{\hat x}_H,{\hat p}_H] & = U^{\dagger} {\hat x} U U^{\dagger} {\hat p} U - ({\hat x} \leftrightarrow {\hat p})\\
& = U^{\dagger}[{\hat x},{\hat p}] U = U^{\dagger} (i\hbar) U = i\hbar
```
Thus we can show that
```{math}
\frac{d}{dt} {\hat x}_H(t) = \frac{1}{i\hbar} [{\hat x}_H, \frac{{\hat p}^2}{2m}] = \frac{{\hat p}_H}{m}
```
Similarly,
```{math}
\frac{d}{dt} p_H = \frac{1}{i\hbar} [p_H,V] = - V'({\hat x})
```
The Heisenberg equations of motion have the identical formal structure as the classical equations of motion! Note that if the potential $V = 0$, we have translation invariance, and $\frac{d}{dt} {\hat p}_H = 0$, that is, momentum seems to be consserved (we will see down the line that the relation between symetries and conserved quantities holds in quantum mechanics as well as classical mechanics). 

We can insert these into expectation values, for which it does not matter whether we write them in the Schroedinger or Heisenberg picture. 
```{nmath}
:label: ehrenfest_theorem
\frac{d}{dt} \vev{x} & = \frac{\vev{p}}{m}\\
\frac{d}{dt} \vev{p} & = - \langle V(x)\rangle
```
These are almost the classical equations of motion, and comprise *Ehrenfest's theorem*. Note however that in general, $\vev{V(x)} \neq V({\vev x})$, unless $V$ is quadratic and thus $V'$ linear. This fact is an important difference between classical and quantum mechanics. They are only formally the same if $V$ is quadratic. To see this, consider the case that $V(x)$ can be expanded in a power series about some mean $x_0$:
```{math}
V(x) = V(x_0) + ({\hat x} - x_0) V'(v_0) + \half({\hat x} - x_0)^2 V''(x_0) + \frac{1}{3!} ({\hat x} - x_0)^3 + \ldots
```
Then
```{math}
\frac{d}{dt} \vev{{\hat p}} = - V'(x_0) - (\vev{{\hat x}} - x_0) V''(x_0) - \half(\vev{{\hat x}^2}  - 2 \vev{{\hat x}}x_0 + x_0^2)V'''(x_0) + \ldots
```
But in general $\vev{{\hat x}^2} \neq \vev{{\hat x}}^2$. A good example would be the Gaussian wavefunction we have described above: 
```{math}
\psi(x) = \frac{1}{(2\pi \sigma^2)^{1/4}} e^{-x^2/4\sigma^2}
```
here $\vev{{\hat x}} = 0$, and $\vev{{\hat x}^2} = \sigma^2$. We could think of these additional terms as a kind of "quantum force" coming from the fact that the Gaussian feels the curvature of the potential near $\vev{{\hat x}}$. 

## Standard method for choosing a Hamiltonian

The textbook procedure for constructing a Hamiltonian for particles in a potential is to start with a classical Hamiltonian $H(p_i,x^i)$, and promote the position and momentum variables to operators (note here I have passed to the higher-diensional case). The basic reason for doing this is that although quantum mechanics is a microscopic theory and we might think the macroscopic world givesno guide, Bohr's *correspondence principle* sensibly demands that the quantum theory should approximate that of the classical theory in some limit which is often denoted by "small $\hbar$". Now we have to be careful of what we mean by this since $\hbar$ is a dimensionful quantity - that is, we have to compare $\hbar$ to some other scales in the problem with the dimension of "action" ($(energy)\times(time)$). How it appears will depend on the problem at hand. For now we will just say that in the appropriately taken limit, we can often treat $\vev{{\hat x}^n} \sim \vev{{\hat x}}^n$.

Once we do this, Ehrenfests theorem basically reproduces Hamilton's equations. This follows the fact that the structure of teh Heisenberg relations {eq}`heisenberg_eom` is almost idential to Hamilton's equations in Poisson bracket form; the factor of $\hbar$ is compensated by the same factor in the canonical comutation relations $[{\hat x}^i, {\hat p}_j] = i\hbar\delta_{ij}$. 

One place you have to start to be careful is when the classical Hamiltonian has tems which are products of $x, p$, since these do not commute. The classic example is that of particles in a magnetic field ${\vec B} = {\vec\nabla}\times{\vec A}({\vec x})$. The classical Hamiltonian is
```{math}
:label: mag_field_ham
\begin{align}
H & = \frac{1}{2m} \sum_i \left(p_i - \frac{e}{c} A_i({\vec x})\right)^2\\
& = \frac{1}{2m} \left({\vec p}^2 - \frac{e}{c} ({\vec p} \cdot{\vec A} + {\vec A}\cdot{\vec p}) + \frac{e^2}{c^2} {\vec A}^2\right)
\end{align}
```
Classically the middle two terms could be combined to $- \frac{e}{m c} {\vec A}\cdot{\vec p}$. However, when we promote this to a quantum mechanical theory we need to remember that ${\hat x}^i,{\hat{p}_j$ do not in general commute. Then the ordering matters. The ordering presented in {eq}`mag_field_ham` gives us a Hermitian operator, as demanded by the rules of quantum mechanics. In general, these kinds of ordering issues represent an ambiguity in passing from classical to quantum mechanics. This shouldn't be too surprising; classical mechanics emerges as a limit of quantum mechanics and so there is missing physics.

## The Schroedinger wave equation

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
