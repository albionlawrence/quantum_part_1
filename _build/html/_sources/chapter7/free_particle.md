# The free nonrelativistic particle

We begin by considering the "free" nonrelativistic particle in $d$ dimensions -- that is, a particle with no force acting on it. The Hamiltonian is 
```{math}
:label: h_free
H = \frac{{\vec p}^2}{2m}
```
where $m$ is the particle mass. The time-dependent Schroedinger equation is
```{math}
:label: tdse_free
- \frac{\hbar^2}{2m} \psi({\vec x}, t) = i \hbar \frac{\del}{\del t} \psi({\vec x}, t)
```
The solutions to the time-*independent* Schrodinger equation are clearly
```{math}
:label: 
\psi_E({\vec x}) = \frac{1}{(2\pi\hbar)^{d/2}} e^{i {\vec p}\cdot{\vec x}/\hbar}
```
which has energy $E = \frac{{\vec p}^2}{2m}$. In this case the energy eigenstates are not quite in the Hilbert space. But we will ignore this complication. 

We can treat the time-dependent equation as an initial value problem. At time $t = t_0$, we rpescribe a wavefunction $\psi({\vec x}, t_0)$. This can be expressed in a Fourier integral:
```{math}
\psi(x,t_0) = \int \frac{d^d p}{(2\pi \hbar)^{d/2}} e^{ i {\vec p}\cdot{\vec x}/\hbar} 
{\tilde \psi}({\vec p})
```
Since an energy eigenstate evolves simply as 
```{math}
\psi_E({\vec x},t) = e^{-i E(t = t_0)/\hbar} \psi_E({\vec x}, t_0)
```
then the full state $\psi$ evolves as
```{math}
\psi(x,t) = \int \frac{d^d p}{(2\pi \hbar)^{d/2}} e^{- {\vec p}\cdot{\vec x}/\hbar} e^{- i \frac{{\vec p}^2}{2m} t} {\tilde \psi}({\vec p})
```

An equivalent strategy is to start with the formula
```{math}
:label: prop_solution
\begin{align}
\psi({\vec x},t) & = \bra{x}U(t,t_0)\ket{\psi(t_0)} \\
& = \int d^d y \bra{x}U(t,t_0)\ket{y}\bra{y}\ket{\psi(t_0)}\\
& \equiv \int d^d y G_0(x,t; y,t_0) \psi(y,t_0)
\end{align}
```
where $G_0(x,t;ymt_0) = \bra{x} U(t,t_0) \ket{y}$ and $U(t,t_0) = e^{-i H (t-t_0)/\hbar}$. $G_0$ is called the *propagator* or Green function. With some work you can show that
```{math}
- \frac{\hbar^2}{2m} {\vec\nabla}^2 G_0 = i \hbar \frac{\del}{\del t} G_0\ ,
```
that is, it solves the Schroedinger equation, and that 
```{math}
G_0(x,t;y,t_0) \xrightarrow[t \to t_0]{} \delta^d({\vec x} - {\vec y})
```
Given $G_0$ you can find a solution for any initial value, by doing the integral in {eq}`prop_solution`. 

od find $G_0$ we insert resolutions of the identity ${\bf 1} = \int d^d p \ket{p}\bra{p}$ and use $\brket{x}{p} = \frac{1}{(2\pi \hbar)^{d/2}} e^{i{\vec p}\cdot{\vec x}/\hbar}$:
```{math}
:label: prop_solution
\begin{align}
G_0(x,t;y,t_0) & = \int d^d p \int d^d p' \brket{x}{p} \bra{p} U(t,t_0) \ket{p'}\brket{p'}{y}\\
& = \int\frac{d^3 p d^3 p'}{(2\pi \hbar)^d} e^{i{\vec p}\cdot{\vec x}/\hbar - i {\vec p}'\cdot{\vec y}/\hbar} e^{-i\frac{{\vec p}^2}{2m\hbar} (t - t_0)} \brket{p}{p'}\\
& = \int \frac{d^d p}{(2\pi \hbar)^d} e^{i {\vec p}\cdot({\vec x} - {\vec y})/\hbar - i \frac{{\vec p}^2}{2m\hbar} t}
\end{align}
```
Now this is a Gaussian integral. The argument is pure imaginart, but if we let $t \to t - i\eps$, then the integrand will die off exponentially as $\sim e^{-\eps p^2 t/(2m\hbar)}$ for large $p^2$. We can then use the standard formulae for Gaussian integrals
```{math}
\int_{-\infty}^{\infty} d q e^{-a q^2} = \sqrt{\frac{\pi}{a}}
```
To do the integral above we need to complete the square. Writing the argument of the exponential as (setting $t_0 = 0$; this is just a choice of coordinates)
```{math}
\begin{align}
& \frac{- i t}{2m\hbar}\left(p^2 - \frac{2m}{t}{\vec p}\cdot({\vec x - \vec y})\right)\\
& \ \ = - \frac{i t}{2m\hbar}\left(p^2 - \frac{2m}{t}{\vec p}\cdot({\vec x - \vec y}) + \frac{m^2}{t^2}(x - y)^2\right) + \frac{i m}{\hbar t}(x - y)^2\\
& \ \ = - \frac{i t}{2m\hbar}(p - \frac{m}{t}(x - y))^2 + \frac{i m}{\hbar t}(x - y)^2
\end{align}
```

We can shift the origin of integration by setting ${\vec p} \to {\vec p} + \frac{m}{t}({\vec x} - {\vec y})$ and performing the Gaussian integrals. The result, when the dust settles, is
```{math}
:label: fp_prop
G_0(x,t; y,t_0) = \left(\frac{m}{2\pi i \hbar (t - t_0)}\right)^{d/2} e^{\frac{m({\vec x} - {\vec y})^2}{2i \hbar t}}
```

This is an exponential which oscillates more slowly at ${\vec x} = {\vec y}$ and more quickly as we go off to infinity. The width of the slowly oscillating region increases as a square root of $t = t_0$; this is the origin of the spreading of the wavefunction. To get some intuition, note that if we set $t = - i \tau$, the Schroedinger equation becomes
```{math}
\hbar \frac{\del}{\del \tau} \psi = \frac{\hbar^2}{2m} \nabla^2 \psi \Rightarrow \del_{\tau}\psi = D \nabla^2 \psi
```
where $D = \frac{\hbar}{2m}$. This latter equation is the diffusion equation (a special case of the Fokker-Planck equation). The interpretation is different: $\psi$ is a density or a probability distribution (rather than a complex amplitude you square to get thr probability). But it turns out you can get some mileage from the realization that there is a formal relation (in many cases) between diffusion problems (and their underlying stochastic dynamics) and quantum problems.
