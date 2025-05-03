# Quantization of the electromagnetic field

A proof of the spin-statistics theorem is beyond what we can do in this course -- it is typically not taught even in a standard QFT course, though one usually sees some additional arguments for it. However, the statistics emerge naturally from the quantization of *fields*. This is something I think everybody needs to see, so I will close by quantizing the electromagnetic field. It is not quite the simplest example, but it leads to some important applications.

Another way to approach this subject (particularly for massive particles) is called *second quantization*. It is equivalent to field quantization, but the starting point is to *assume* single-particle states, built multiparticle states as in the last section, and then assume that the full Hilbert space has the structure
```{math}
\cO = \cH_{no\ particles} \oplus \cH_{1\ particle} \oplus \cH_{2\ particles} \oplus \cdots
```
One can then include interaction terms which allow for changes in the number of particles through absorbption and decay. This is called "second quantization" because it is built on the "first-quantized" Hilbert space of single particles. This is often a useful starting point, but we will work a different way that makes clear that we can get all of this from standard quantization applied to a *field*.

## The classical electromagnetic field

### Lagrangian treatment

Recall that we can write the electromagnetic field in terms of a vector and scalar potential:
```{math}
\begin{align}
{\vec E} & = {\vec\nabla} \phi + \frac{1}{c} \frac{\del}{\del t} {\vec A}\\
{\vec B} & = {\vec\nabla}\times{\vec A}
\end{align}
```
This form automatically yields half of Maxwell's equations:
```{math}
:label: bianchi_ident
\begin{align}
{\vec\nabla}\cdot {\vec B} & = 0\\
\frac{1}{c} \frac{\del}{\del t} {\vec B} - {\vec\nabla} \times{\vec E} & = 0
\end{align}
```
We note here that the vector and scalar potentials are redundant: if we shift them by the *gauge transformations* 
```{math}
\begin{align}
A_i & \to a_i + p_i \Lambda \\
\phi & \to - \del_t \lambda 
\end{align}
```
then the physical fields ${\vec E}, {\vec B}$ (those which apepar in the Lorentz force law and in Maxwell's equations) are invariant. This will become important below.

The other two of Maxwell's equations follow from the Euler-Lagrange equations associated to the following action:
```{math}
\begin{align}
S & = \frac{1}{8\pi} \int dt \int d^3 x \left[{\vec E}^2 - {\vec B}^2\right]\\
& =  \frac{1}{8\pi} \int dt \int d^3 x \left[\left( {\vec\nabla} \phi + \frac{1}{c} \frac{\del}{\del t} {\vec A}\right)^2 - ({\vec\nabla}\times{\vec A})^2\right]\\
& = \int dt L\\
& = \int dt d^3 x {\cal L}
\end{align}
```
The important point is that to get the equations of motion (the remaining two Maxwell equations), we demand stationarity under variations of $\phi, {\vec A}$: clearly directly varying ${\vec E}, {\vec B}$ would just yield trivial equations!
Nore here that the Lagrangian $L$ is the spatial integral $\int d^3 x {\cal L}$ of the {\it Lagrangian density} ${\cal L}$. We can think of this as a collection of variables $\phi({\vec x}, t)$, ${\vec A}({\vec x}, t)$, one for each point in space. 

We thus write $\phi = \phi_{cl} + \eps\delta\phi$, ${\vec A} = {\vec A}_{cl} + \eps \delta{\vec A}$; expand 
```{math}
\begin{align}
S & = S_{cl}[\phi_{cl},{\vec A}_{cl} + \eps \int dt d^3 x \left[ \delta\phi \delta_{\phi} S + \delta A^i \cdot\delta_i S\right] + \cO(\eps^2)\\
& = S_{cl} + \eps S_1 + \cO(\eps^2)
\end{align}
```
and demand $\delta_{\phi}S = \delta_i S = 0$ to get equations for $\phi_{cl}, A^i_{cl}$. 

At first order,
```{math}
\begin{align}
S_1 & = \frac{1}{4\pi}\int dt d^3 x {\vec\nabla}\delta\phi\cdot\left({\vec \nabla} + \frac{1}{c}\frac{\del}{\del t} {\vec A}\right)\\
& = - \frac{1}{4\pi} \int dt d^3 x \delta\phi {\vec\nabla}\cdot{\vec E} + {\rm boundary\ terms}
\end{align}
```
We will assume that the fields vanish at infinity so that the boundary terms vanish. The result is Gauss' law without matter:
```{math}
{\vec \nabla} \cdot{\vec E} = 0
```
We can do a similar calculation for the coefficient of $\delta A^i$: the result is Faraday's law in the absence of currents:
```{math}
{\vec\nabla}\times{\vec B} - \frac{1}{c} \frac{\del {\vec E}}{\del t} = 0
```
Note that when we couple to matter, these two equations get modified with source terms proportional to the charge density and current, respectively. The equations {ref}`bianchi_ident` are, in this formalism, mathematical identities. The situation changes in the presence of magnetic charges, eg magnetic monopoles and the associated currents. These have not been observed (well, one might have been seen once), and are not required by the Standard Model of particle physics. Certain "beyond-the-standard-model" theories have them; in these electromagnetism is embedded in something much more complex. In the presence of such monopoles, one cannot globally write the electric and magnetic fields in terms of a scalar and vector potential; it is fair to say that a proper Lagrangian treatment that includes both kinds of chanrges remains an open problem.


### Hamiltonian treatment

We start by finding the conjugate momentum. We can consider the fields $\phi, {\vec A}$ as collections of variables, one at each point ${\vec x}$, and compute the associated cononical momentum. In this we can consider the position ${\vec x}$ as a kind of index. This is complicated by the indices being continuous, so that the analog of the Kronecker delta function is the Dirac delta function.

We will adopt the definitions
```{math}
\begin{align}
p_{\phi} & = \frac{\delta L}{\delta {\dot\phi}}\\
p_{AI]} & \equiv p_i =  \frac{\delta L}{\delta {\dot A}}({\vec x}, t)
\end{align}
```
The right hand side of these are functional derivatives. Consider some Lagrangian 
```{math}
L = \int d^3 x {\cal L}(\psi({\vec x}, t), {\dot\psi}({\vec x}, t))
```
Write $\psi = \psi_0 + \delta\psi$, ${\dot\psi} = {\dot\psi}_0 + \delta{\dot\psi}$. The functional derivatives with respect to $\psi, {\dot\psi}$ can be written as:
```{math}
L =  \int d^3 x {\cal L}(\psi_0({\vec x}, t), {\dot\psi}_0({\vec x}, t)) + \int d^3 x \left[ \delta\psi \frac{\delta L}{\delta \psi}(psi_0,{\dot\psi}_0) + \delta{\dot\psi}   \frac{\delta L}{\delta {\dot\psi}}\right] + \cO(\delta^2)
```
Thus,
```{math}
\begin{align}
p_i & = \frac{1}{4\pi c} \left(\frac{1}{c} {\dot A}^i + \del_i \phi\right)\\
p_{\phi} & = 0
\end{align}
```
This second term is a constraint, which is intimately tied up with gauge invariance, and the fact that the vector and scalar potentials carry redundant information. It complicates writing down a Hamiltonian and associated Poisson brackets. Our solution. The general treatment of constrained Hamiltonian systems is an interesting one that we will have to leave aside; a nice review is in {cite:p}`Hanson:1976cn` (I believe you can find PDFs online). It is also discussed in Weinberg's quantum field theory book {cite:p}`Weinberg:1995mt`. 

At this point we will solve the constraint by "fixing a gauge"; that is, imposing a constraint on $A_i, \phi$ so that the gauge redundancy is completely removed. We will find that when we solve for this constraint, we can recast the dynamics in terms of canonical variables with a familiar Hamiltonian, and quantize in the standard way.

There are many gauges we can fix: we will choose the *Coulomb gauge* 
```{math}
{\vec\nabla}\cdot{\vec A} = 0\ , \ \ \phi = {\rm const.}
```
My claim is that we can always find a gauge in which this holds. Given any cector potential ${\vec A}$, define ${\vec A}' = {\vec A} + {\vec\nabla}\Lambda$. Then ${\vec A}'$ will satisfy the Coulomb gauge condition if
```{math}
\nabla^2 \phi = - {\vec\nabla}\cdot{\vec A}
```
But this is just the Poisson equation, which generally has a solution. Now, we consider the Gauss' law
```{math}
{\vec \nabla} \cdot{\vec E} = \frac{1}{c}{\vec\nabla}\cdot\del_t {\vec A} + \nabla^2 \phi = 0
```
The first term on the right hand side vanishes; the second term is Laplace's equation. If there are no charges, we impose the boundary condition $\phi \to {\rm const.}$ as $|{\vec x}| \to \infty$, guaranteeing the vanishing of the electric field. But then in a vacuum, the unique solution is $\phi = {\rm const.}$ everywhere. (With this argument $\phi$ could change with time; we could remove it with a time-dependent but spatially constant gauge transformation, although we usually demand that only gauge transformations suitably vanishing at infinity are true redundancies of the theory. At any rate this mode does not appear in the electric or magnetic fields, or in the Hamiltonian).

We will start by writing the Hamiltonian for ${\vec A}_i$ without explicitly imposing ${\vec\nabla}\cdot{\vec A} = 0$ -- we will solve for this constraint along the way, in such a way that the number of independent modes of $A_i, p_i$ are the same. Keeping $\phi = 0$ we simply write the Hamiltonian in the most boneheaded way possible:
```{math}
H = \int d^3 x \left[p_i(x,t) {\dot A}_i(x,t) - L(A_i, {\dot A}_i)\right] = \int d^3 x \left[ 2\pi c^2 (p_i)^2 + \frac{1}{8\pi}{\vec\nabla}\times{\vec A}\right]
```
It turns out to be easier to impose Coulomb gauge after taking a Fourier transform. Writing
```{math}
\begin{align}
{\vec A}(x,t) & = \int\frac{d^3 k}{(2\pi)^3} \left[{\vec{\tilde A}}(k,t)e^{i{\vec k}\cdot{\vec x}} + {\rm c.c.} \right]\\
{\vec p}(x,t) & = \int\frac{d^3 k}{(2\pi)^3} \frac{c|k|}{i}\left({\vec{\tilde A}}(k,t)e^{i{\vec k}\cdot{\vec x}} - {\rm c.c.} \right]
\end{align}
```
These are the real and imahginary parts of a complex function, so they are completely independent. Now, to solve for the Coulomb gauge constraint, we note that
```{math}
{\vec\nabla} \cdot{\vec A} = \int\frac{d^3 k}{(2\pi)^3} \left[i {\vec k}\cdot{\vec{\tilde A}}(k,t)e^{i{\vec k}\cdot{\vec x}} - {\rm c.c.} \right]
```
Thus, we must impose the condition ${\vec k}\cdot{\vec{\tilde A}} = 0$. To do so, for each ${\vec k}$ we consider a two-dimensional basis of complex vectors ${\vec \eps}^{a = 1,2}$ satisfying ${\vec k}\cdot{\vec \eps}^a = 0$, which are appropriately orthonormal $({\vec \eps}^a)^{\ast}\cdot{\vec \eps}^b = \delta^{ab}$. Given these, we write
```{math}
{\vec{\tilde A}}(k) = \sum_a {\vec\eps}^a A_a(k)
```
We impose this on ${\tilde A}$ as it appears in both $A_i, p_i$. This would emerge from a more systematic treatment of constrained Hamiltonian systems; I will just assert here that it is the right thing to do.

Next, we write the fields in a different linear combination. Defining $\omega = c|k|$, we have:
```{math}
\begin{align}
A_a & \equiv \sqrt{\frac{2\pi c^2}{\omega}} a_a\\
Q_a & \equiv \frac{1}{\sqrt{2\omega}}(a_a + a_a^*)\\
P_a & \equiv - i \sqrt{\frac{\omega}{2}}(a_a - a_a^*)
\end{align}
```
With this redefinition,
```{math}
H = \sum_a \int \frac{d^3 k}{(2\pi)^3}\left(\half P_a P_a + \half \omega(k)^2 Q_a Q_a\right)
```
We just have a set of simple harmonic oscillators! The one complication is that they are a continuous collection. We can work with this up to a point. The Poisson brackets become
```{math}
\{Q_a(k), P_b(k')\} = (2\pi)^3 \delta^{(3)}({\vec k} - {\vec k}') \delta_{ab}
```
and Hamilton's equations are
```{math}
\begin{align}
{\dot Q}_a(k) & = \frac{\delta H}{\delta P_a(k)} \{Q_a(k), H\} = P_a(k)\\
{\dot P}_a(k) & = - \frac{\delta H}{\delta Q_a(k)} \{P_a(k), H\} = \omega^2(k) Q_a(k)
\end{align}
```

We can make this easier by putting the system in a box of finite volume. If the box is cubical, with sides of length $L$ and volume $V = L^3$, then with the appropriate boundary conditions, the allowed wavenumbers are:
```{math}
{\vec k} = \frac{2\pi {\vec n}}{L} = \left(\frac{2\pi n_x}{L}, \frac{2\pi n_y}{L}, \frac{2\pi n_z}{L}\right)
```
Further rescaling $P = \sqrt{V} p$, $Q = \sqrt{V} q$, we have
```{math}
H = \sum_{{\vec k}, a} \left(\half p_{a,{\vec k}}^2 + \half \omega(k)^2 q_{a,{\vec k}}^2\right)
```
which is an ordinary harmonic oscillator for every ${\vec k}, a$.

Quantization is now straightforward. If we write
```{math}
\begin{align}
Q_a(k) & = \sqrt{\frac{\hbar}{2\omega(k)}}\left(a_a(k) + a_a(k)^{\dagger}\right)\\
P_a(k) & = \sqrt{\frac{\hbar\omega}{2}}\frac{1}{i}\left((a_a(k) - a_a(k)^{\dagger}\right)
\end{align}
```
Then $a_a$ satisfies the commutation relations
```{math}
[a_a(k), a_b^{\dagger}(k')] = (2\pi)^3\delta^{(3)}({\vec k} - {\vec k}')\delta){ab}
```
for the infinite volume case, or
```{math}
[a_a(k), a_b^{\dagger}(k')] = \delta_{{\vec k}, {\vec k}'}\delta){ab}
```
In these cases, 
```{math}
H = \sum_a \int \frac{d^3 k}{(2\pi)^3} \hbar \omega(k) \left(a^{\dagger}_a(k) a_a(k) + \half\right)
```
or, in finite volume,
```{math}
H = \sum_{a,{\vec k}} \hbar \omega(k) \left(a^{\dagger}_a(k) a_a(k) + \half\right)
```

We can define the vacuum via 
```{math}
a_a\ket{0} = 0
```
The excitations are (here we will work in finite volume):
```{math}
\frac{(a_{a_1}(k_1)^{\dagger})^{n_1}\cdots(a_{a_N}(k_N)^{\dagger})^{n_N}}{\sqrt{n_1!\cdots n_N!}} \ket{0}
```
The interpretation is that we have $n_k$ photons with polarization $a_k$ and wavenumber $k_k$. Note that it does not matter we arrange the creation operators since they commute; furthermore, all we can do for fixed polarization and wavenumber i scount the number of photons. We can create photons at fixed locations via
```{math}
\ket{x_1,x_2} = \sum_{{\vec k}_1,{\vec k}_2} e^{i k_1 x_1 + i k_2 x_2} a_{a_1}(k_1)^{\dagger} a_{a_2}(k_2)^{\dagger} \ket{0}
```
but since the creation operators commute, $\ket{x_1,x_2} = \ket{x_2,x_2}$. In other words, these are automatically bosons. The upshow is that by quantizing the electromagnetic field we automatically get particle-like excitations, and those particles are bosons. We can do this similarly for spin-0 particles (in fact the field theory is much simpler -- the fields are just scalars $\phi(x,t)$, and there is no gauge invariance to worry about.)

It is less trivial to go through this procedure for spin-$\half$ particles. One needs to start with fields which are *GHrassman variables* -- that is, even as classical fields they anticommute. The upshot of the spin-statistics theorem is that we *must* go this route for half-integer spins, to get fermionic particles satisfying the Pauli principle. This follows from the demands that the theory be causal (eg information cannot propagate faster than the speed of light), that the vacuum is stable and all states with particles have higher energy, and that there are no negative-probability states.

Finally, give these operators, we can go back and write *field operators* which appear in the interaction Hamiltonian:
```{math}
\begin{align}
{\hat{\vec A}} & = \int \frac{d^3 k}{(2\pi)^3}\left(\frac{2\pi \hbar c^2}{\omega(k)}\right)^{1/2}\left\{ a_a(k) \eps_a(k) e^{i{\vec k}\cdot{\vec x}} + {\rm h.c.}\right\}\\
{\hat{\vec p}} & = -i \int \frac{d^3 k}{(2\pi)^3}\left(\frac{\hbar \omega(k)}{2\pi c^2}\right)^{1/2}\left\{ a_a(k) \eps_a(k) e^{i{\vec k}\cdot{\vec x}} - {\rm h.c.}\right\}
\end{align}
```

### Interactions with charged matter

We can argue for the interaction of the electromagnetic field with charged matter in several directions. One is to recall that the Hamiltonian for some set of $M$ charged particle in a vector potential is
```{math}
H = \sum_{i = 1}^M \frac{1}{2m_i}\left({\vec p}_i - \frac{e_i}{c}{\vec A}({\vec x}_i)^2\right)
```
We can expand this in powers of ${\vec A}$; we have in mind time-dependent perturbation theory for which the strength of the field is the perturbation parameter. We will ignore the $\cO(A^2)$ terms for now, but they are important as we go to second order. The result is
```{math}
H = \sum_{i = 1}^M \frac{1}{2m_i}{\vec p}_i^2 - \frac{e_i}{2m_ic}\left({\vec p}_i \cdot{\vec A}(x_i) + {\vec A}(x_i)\cdot{\vec p}_i\right)
```
Now ${\vec p} = \frac{\hbar}{i} {\vec \nabla}$. If ${\vec A}$ is in Coulomb gauge, 
```{math}
{\vec p}\cdot{\vec A}\ket{\psi} = \frac{\hbar}{i}({\vec\nabla}\cdot{\vec A}\ket{\psi} + {\vec A}\cdot{\vec p}\ket{\psi} =  {\vec A}\cdot{\vec p}\ket{\psi}
```
That is, $p$ and $A$ commute. Now we promote ${\vec A}$ to a field operator. As such, the *argument* cannot itself be an operator. We take care of this by writing
```{math}
\begin{align}
H_1 & = \sum_i \frac{e_i}{m_ic}{\vec A}\cdot{\vec p}_i\\
& = \int d^3 x {\vec A}({\vec x})\sum_i e_i \delta({\vec x} - {\hat{\vec x}}_i) {\vec p}_i\\
& =  \int d^3 x {\vec A}({\vec x}) {\vec J}
\end{align}
```
Properly speaking, to make ${\vec J}$ a Hermitian operator, we write it as
```{math}
{\hat{\vec J}} = \half \sum_i e_i \left\{{\hat{\vec p}}_i,\delta({\vec x} - {\hat {\vec x}_i})\right\}
```
which is the charge current operator. The total Hamiltonian is then
```{math}
H = H_{particles} + H_{em} + H_1
```
where $H_{particles}$ is the Hamiltonian of the charged particls absent the interaction with the quantized electromagnetic field.

Now we consider the process of a transition between, for example, states of some atom coupled to the electromagnetic field. The initial state $\ket{i}$ will correspond to the eigenstate of the Hamiltonian of the atom, and some number of photons, so that $\ker{i}$ is an eigenstate of $H_{particles} + H_{em}$. We wish to study the transition amplitude to a state $\ket{f}$ which is also an eigenstate of  $H_{particles} + H_{em}$. To first order in $H_1$, the transition amplitude is:
```{math}
c_k = - \frac{i}{\hbar} \int_0^t dt' d^3 x \ket{f} {\hat {\vec A}}({\vec x})\cdot{\vec J} \bra{i}
```
At this order, $\ket{i},\ket{f}$ clearly can differ only by a single photon; ${\vec J}$ is proportional to the momenta and acts as a vector operator, so these transitions will be appropriately constrained by angular momentum selection rulesWith this formalism we can understand various processes such as spontaneous emission in the electromagnetic vacuum through the transition of the atom to a lower-energy state via the emission of a photon; stimulated emission between the same atomic states in the presence of photons, the amplitude of which scales as $\sqrt{N + 1}$ where $N$ is the number of photons with the appropriate wavenumber; and excitation of atioms via the absorption of photons.

At second order in the field the transitions amplitudes are matrix elements of two powers of $H_1$ and of the ${\vec A}^2$ term we ignored; such transitions involve the change in the number of photons by 2, 0, or -2.

Such processes are discussed in a variety of textbooks, such as Shankar and Baym, which I recommend highly for further study.
