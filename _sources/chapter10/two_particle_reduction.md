# Reduction of the Two-Body Problem

Our goal here is to set up the Hilbert space and the Hamiltonian, for the pruposes of solving the time-independent Schroedinger equation.

## The Hilbert space

At its core we are studying the Coulomb attraction between two spin-$\half$ particles (the proton and the electron) moving in space. Each of them can be labeled by their position (in a position basis) and their spin. For this section of the notes we will mostly ignore the spin degrees of freedom (they will come back later). The resulting Hilbert space is
```{math}
\cH = L^2(\CR^3)_1\otimes \CC^2_1\otimes L^2(\CR^3)_2\otimes \CC^2_2$
```
where the subscrips label the particles, $L^2(\CR^3)$ denotes the Hilbert space related to particle position, and $\CC^2$ is the Hilbert space for the spin degrees of freedom (when the particles carry spin-$\half$). 

Ignoring the spin degrees of freedom, the Hilbert space of the spatial degrees of freedom is the space of linear combinations of wavecfunctins $\psi_1({\vec x}_1)\psi_2({\vec x}_2)$, which are just general functions $\Psi({\vec x}_1,{\vec x}_2)$. As we will see, it is convenient to write these as functions of a different linear combination of variables, teh *relative position ${\vec x} = {\vec x}_1 - {\vec x}_2$ and the *center of mass position*
```{math}
{\vec X} = \frac{m_1 {\vec x}_1 + m_2 {\vec x}_2}{m_1 + m_2}
```
where $m_i$ are the passes of the $i$th particles, a parameter which appears in teh Hamiltonian. We can solve for ${\vec x}_i$ in terms of ${\vec X}$, ${\vec x}$, and so write $\Psi = \Psi({\vec X}, {\vec x})$. Thus, the Hilbert space is, equivalently, 
```{math}
\cH = L^2(\CR^3)_{X}\otimes L^2(\CR^3)_{x}
```

## The Hamiltonian

Our strategy (which works quite well in practice) is to write the Hamiltonian for the non-relativistic Coulomb problem and promote it to a quantim operator in the usual way, replacing the classical positions and momenta with quantum operators. In cgs units, this is
```{math}
H = \frac{{\vec p}_p^2}{2 m_p} + \frac{{\vec p}_e^2}{2 m_p} - \frac{e^2}{|{\vec c}_p - {\vec x}_e|}
```
where the subscripts $p,e$ refer to proton and electron, and $e$ as a dimensionful number is the electron charge. At this point we are ignoring spin. This is the Hamiltonian in the non-relativistic limit. In fact there are important and measurable additional terms that are higher order in ${\vec p}^2$ or which couple the spin and orbital anglar momenta, that arise from a fully relativistic treatment, but they are small, of order the fine structure constant $\alpha = \frac{e^2}{\hbar c} \sim \frac{1}{137}$. We will discuss some of these later, and learn how to treat them in a systematic fashion.

Note that the interaction between these particles depends only on the relative position. Our experience with classical mechanics (for this problem or for the mathematically equivalent gravitational two-body problem) indicates that the Hamiltonian should be indepdendent of the center of mass, and thus that the center of mass momentum is conserved. 

We start with the change of coordinates
```{math}
\begin{align}
{\vec X} & = \frac{m_p {\vec x}_p + m_e {\vec x}_e}{m_p + m_e}\\
{\vec x} & = {\vec x}_e - {\vec x}_p
\end{align}
```
We can then ask, what are the conjugate momenta in terms of ${\vec p}_{p,e}$? There are several ways we could do this. In the classical case, we can perform the above transformation at the level of the Lagrangian, for which we find
```{math}
:label: com_lag
L = \half M {\dot{\vec X}}^2 + \half \mu {\dot {\vec x}}^2 + \frac{e^2}{|{\vec x}|}
```
where $M = m_e + m_p$ is the *total mass*, and
```{math}
\mu = \frac{m_e m_p}{m_e + m_p}
```
is the *reduced mass. In terms of these, 
```{math}
\begin{align}
{\vec P}_{X} & = {\vec p}_e + {\vec p}_p\\
{\vec p}_{x} & = \frac{m_p {\vec p}_e - m_e {\vec p}_p}{m_e + m_p}
\end{align}
```
You can show that $\{X^i, P_j\} = \delta^i_j$, $\{x^i,p_j\} = \delta^i_j$, $\{x^i,P_j\} = \{X^i,p_j\} = 0$, as a consequence of the canonical commutation relations for the positions and momenta of the proton and electron. Alternatively, in the quantum mechanical case, if we represent the momentum operators in terms of gradients, we can derive the same relationship.

We can then rewrite the Hamiltonian by taking the Legendre transform of Eq. {eq}`com_lag`, to find:
```{math}
H = \frac{{\vec P}^2}{2M} + \frac{{\vec p}^2}{2\mu} - \frac{e^2}{|{\vec x}|}
```
where we have dropped the subscripts on $P,p$.

## Separating out the center of mass coordinates

Classically, the center of mass coordinate simply travels in a straight line; the Lagrangian {eq}`com_lag` as the equations of motion for ${\vec X}$:
```{math}
M\ddot{\vec X} = {\dot {\vec P}} = 0
```
The center of mass momentum is conserved.

In quantum mechanics, we wish to solve the equation
```{math}
H\ket{\Psi} = E\ket{\Psi} \Rightarrow - \frac{\hbar^2}{2M} {\vec \nabla}^2_X \Psi(X,x) - \frac{\hbar^2}{2\mu} {\nabla}^2_x \Psi - \frac{e^2}{|{\vec x}|}\Psi = E \Psi
```
We will use the technique of separation of variables to pull apart the dependence on $X, x$. If we take the ansatz $\Psi = \chi(X)\psi(x)$, insert this into the Schroedinger equation above, and divide by $\Psi$, we find
```{math}
- \frac{1}{\chi}\frac{\hbar^2}{2M} {\vec \nabla}^2_X - \frac{1}{\psi} \frac{\hbar^2}{2\mu} {\vec \nabla}^2_x \psi - \frac{e^2}{|{\vec x}|} = E
```
Since the second and third terms on the RHS as well as $E$ are independent of $X$, the first term must also be independent of $X$, that is, a constant, which we will call $E_{com}$; thus
```{math}
- \frac{\hbar^2}{2M} {\vec \nabla}^2_X \chi = E_{com}\chi
```
This is the equation for a free particle, whose solutions are plane waves. Following this, we are left with
```{math}
- \frac{\hbar^2}{2\mu} {\vec \nabla}^2_x \psi - \frac{e^2}{|{\vec x}|} \psi = (E - E_{com})\psi
```
This is the equation we will solve in the next section. 

Note that we could also do this for the time-dependent Schroedinger equation; if we assume the total wavfunction factorizes into $\chi(X,t)\psi(x,t)$, then we find
```{math}
\frac{1}{\chi}\left[i\hbar \frac{\del}{\del t} \chi + \frac{\hbar^2}{2M}\chi\right] + \frac{1}{\psi} \left[i\hbar \frac{\del}{\del t} \psi + \frac{\hbar^2}{2\mu} {\vec\nabla}^2_x \psi + \frac{e^2}{|{\vec x}|} \psi\right] = 0
```
Now each of the two terms must be an equal and opposite constant; we can remove this constant by rotating $\chi,\psi$ by a time-dependent phase. In this case we could set up a wavepacked for the center of mass motion.

In both cases, entangled states with respect to the $X,x$ degrees of freedom are possible; we leave these aside.



