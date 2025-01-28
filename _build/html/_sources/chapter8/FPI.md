# The Feynman Path Integral

Up to now we have developed a version of quantum mechanics based on the Hamiltonian. Classically, Hamilton's equations are first order equations in $2N$ phase space variables, and have unique solution when initial conditions for these variables are specified. Quantum mechanically, the time-dependent Schroedinger equation 
```{math}
i \del_t {\psi} = H \ket{\psi}
```
is a first-order equation whose solution is specified by an initial condition on the quantum state, and the Hamiltonian is the essential object that generated changes in time.

One might ask whether there is a quantum analog of the Lagrangian formulation. Indeed there is. We will focus on particle mechanics -- path integral formulations can be constructed for, eg, quantum spins, but this is a more complicated (though extremely interesting) story.

Recall that classicalt, the Lagrangian story begins by specifying the classical action 
```{math}
S[x^I(t)] = \int_{t_0}^{t_1} dt L(x^I(t), {\dot x}^I(t), t)
```
we assume $I \in \{1,\ldots,N\}$. Classically one considers all paths with $N$ initial conditions $x^I(t_0)$ and $N$ final conditions $x^I(t_1)$; the path that is an extremum of $S$ satisfies the Euler-Lagrange equations. 

We will find that there is a formulation of the quantum problem that involves an integral over all such paths, each given a complex weight $e^{i S[x(t)]/\hbar}$. 

## Building the propagator

Recall that we defined the *propagator*
```{math}
K(x_1^I, t_1; x_0^I, t_0) = \bra{x_1} U(t_1,t_0) \ket{x_0}
```
where $U$ is the unitary operator implementing time evolution:
```{math}
 \ket{\psi(t_1)} = U(t_1,t_0) \ket{\psi(t_0)}
```
The propagator completely determines the time evolution of a state, as
```{math}
\begin{align}
\psi(x^I_1, t_1) & = \brket{x^I_1}{\psi(t_1)} \\
& = \bra{x^I_1} U(t_1,t_0) \ket{\psi(t_0)} \\
& = \int d^Nx_0 \bra{x^I_1} U(t_1,t_0)\ket{x_0}\brket{x_0}{\psi(t_0)}\\
& = \int d^Nx_0 K(x^I_1,t_1; x^I_0,t_0)\psi(x_0,t_0)
\end{align}
```
It is a function of the initial and final positions, so one might imagine that it has a natural relationship to the Lagrangian formulation.

Now the axion of unitary time evolution applies to any initial and final time. This means that given $t_2 > t_1 > t_0$, we have
```{math}
\begin{align}
\ket{\psi(t_2)} & = U(t_2,t_1)\ket{\psi(t_1)} \\
& = U(t_2,t_1)U(t_1,t_0)\ket{\psi(t_0)}\\
& = U(t_2,t_0) \ket{\psi(t_0)}
\end{align}
```
That is, these unitary operators satsify a composition law: $U(t_2,t_0) = U(t_2,t_1)U(t_1,t_0)$. Written in terms of propagators,
```{math}
\begin{align}
K(x_2,t_2;x_0,t_0) & = \bra{x_2} U(t_2,t_0) \ket{x_i}\\
& =  \bra{x_2} U(t_2,t_1)U(t_1,t_0) \ket{x_0}\\
& = \int d^Dx_1 \bra{x_2} U(t_2,t_1)\ket{x_1}\bra{x_1} U(t_1,t_0) \ket{x_0}\\
& = \int d^Dx_1 K(x_2,t_2;x_1,t_1)K(x_1,t_1;x_0,t_0)
\end{align}
```
Following this logic, we let $t_f = t_i + M \delta t$, and write
```{math}
K(x_f,t_f;x_i,t_i) = \int dx_{M-1} dx_{M-2}\ldots dx_1 dx_0 K(x_f,t_f; x_{M-1},t_{M-1})K(x_{M-1},t_{M-1};x_{M-2},t_{M-2})\ldots K(x_1,t_1;x_i,t_i)
```
The goal is to find $K(x_k,t_{K-1}+\delta t; x_{k-1},t_{k-1})$ as $\delta t \to 0$, $\delta M \to \infty$, $M\delta t$ fixed. It is clear that the above integral can be considered as one over all trajectories from $x_i$ at time $t_0$ to $x_f$ at time $t_f$. 

## The short-time kernel

Our next step is to compute $K(x_k, t_k;x_{k-1},t_{k-1})$ for $\delta t$ "small". In principal we should be careful about what is meant by "small" -- as always for dimensionful numbers, "small compared to what?" is the important question. 

To start with, we will now focus on the case that $H = \frac{{\vec p}^2}{2m} + V({\vec x})$. Since this is time-independent, we can write
```{math}
U(t_f,t_i) = e^{- i H (t_f-t_i)/\hbar}
```
In the case that $t_k - t_{k-1} = \delta t$, we imagine that we can expand $U$ to first order in $\delta t$. This only makes sense inside expectation values. We will continue nonetheless and approximate
```{math}
\bra{x_k} U(\delta t, 0) \ket{x_{k-1}} \sim \bra{x_k} \left(1 - 
\frac{i \delta t}{\hbar} \left(\frac{{\vec p}^2}{2m} + V\right)\right)\ket{x_{k-1}} + {\cal O}(\delta t^2)
```
New we insert ${\bf 1} = \int d^d p_{k-1} \ket{p_{k-1}}\bra{p_{k-1}}$, and using $\brket{x_k}{p_{k-1}} = \frac{1}{(2\pi\hbar)^{d/2}}e^{i {\vec p}_{k-1}\cdot{\vec x}_k/\hbar}$, we find:
```{math}
\bra{x_k} U(\delta t, 0) \ket{x_{k-1}} \sim \int \frac{d^d p_{k-1}}{(2\pi\hbar)^d} e^{i {\vec p}_{k-1}\cdot({\vec x}_k - {\vec x}_{k-1})/\hbar} \left(1 - \frac{i \delta t}{\hbar}\left(\frac{{\vec p}_{k-1}^2}{2m} + V({\vec x}_{k-1})\right)\right) + {\cal O}(\delta t^2)
```
Now we make two approximations. First, if we write $x_k \equiv x(t_k)$, then as $\delta t \to 0$, we should be able to write $(x_k - x_{k-1}) \sim \delta t {\dot x}(t_{k-1})$, We also write $p_{k-1} = p(t_{k-1})$. Secondly, to ${\cal O}(\delta t^2)$, we can write $1 - i a \delta t \sim e^{-i a \delta t}$; applying this we find
```{math}
:label: st_kernel
\bra{x_k} U(\delta t, 0) \ket{x_{k-1}} \sim \int \frac{d^d p(t_{k-1})}{(2\pi\hbar)^d} e^{i \delta t \left(p(t_{k-1}) \dot{x}(t_{k-1})/\hbar - \frac{p(t_{k-1})^2}{2m} - V(x(t_{k-1}))\right)}
```

## The full propagator

Thus, we can write
```{math}
\begin{align}
& K(x_f,t_f;x_i,t_i) \\
& = \int \frac{d^d x_1\ldots d^d x_{N-1} d^d p_0\ldots d^d p_{N-1}}{(2\pi)^{N d}}\exp\left(i \frac{\delta t}{\hbar} \sum_{k=0}^{N-1} \left(p(t_k){\dot x}(t_k) - \frac{p(t_k)^2}{2m} - V(x(t_k))\right)\right)\\
& \sim  \int \frac{d^d x_1\ldots d^d x_{N-1} d^d p_0\ldots d^d p_{N-1}}{(2\pi)^{N d}} \exp\left(\frac{i}{\hbar} \int_{t_i}^{t_f} dt \left(p(t) {\dot x(t)} - \frac{p(t)^2}{2m} - V(x(t))\right)\right)
\end{align}
```
We can recognize the integral as that over a path $(x(t), p(t))$ in phase space. The integrand is the exponential of the Lagrangian written in phase space variables, as the Legendre transform of the Hamiltonian.

On the other hand, we can go back to Eq. ({ref}`st_kernel`) and do the integral over $p_{k-1}$, This is a Gaussian integral; if we let $\delta t \to \delta t - i \eps$ with $\eps$ real, then the integrand is well defined at large $p, x$ so long as $V(x) > 0$ as $|{\vec x}| \to \infty$. The result is that
```{math}
\bra{x_k} U(\delta t, 0) \ket{x_{k-1}} \sim \left(\frac{-i m\hbar }{2\pi i\delta t}\right)^{1/2} e^{\frac{i \delta t}{\hbar} \left(\frac{m {\dot x}^2}{2} - V(x(t))\right)}
```
We can thus follow the same prescription as above to find that
```{math}
\begin{align}
K(x_f,t_f) & = {\cal N} \int_{x(t_i) = x_i, x(t_f) = x_f}  Dx \exp\left(\frac{i}{\hbar}\int_{t_i}^{t_f} dt L(x, {\dot x})\right) \\
& = {\cal N} \int_{x(t_i) = x_i, x(t_f) = x_f} Dx \exp\left(\frac{i}{\hbar} S[x(t)]\right)
\end{align}
```
Here ${\cal N}$ is some normalization factor, and $Dx(t)$ is the integral over all paths $x(t)$, $t\in [t_i, t_f]$, with the specified boundary conditions.

Note that in addition to being dependent on the Lagrangian or the classical action, the boundary conditions specified are on the initial and final positions, in analogy to the boundary conditions specified in classical Lagrangian mechanics.

We have not interrogated too closely the validity of our "short time" expansion. I will put this aside for now and assert that I have gotten the right answer, But you would be right to demand an explanation.

## Connections to statistical mechanics.

Below I will outline in a *very* sketchy fashion connections statistical mechanics. In practice this is most interesting if we start from quantum field theory, but the basic arguments already apply to quantum mechanics.

The point of drawing these connections is to tantalize you with the idea that many subjects in physics are mathematically unified. These connections have lead to powerful insights into quantum field theory and statistical mechanics, most especially Ken Wilson's (Nobel Prize-winning) formulation of *renormalization* -- a theory for how the effective description of system changes under successive coarse-grainings.

### Connection to equilibrium quantum statistical mechanics

First, we consider the case of quantum statistical mechanics. In this case we wish to compute
```{math}
Z(\beta) = {\rm Tr} e^{-\beta H} = \int d^d x \bra{x} e^{-\beta H} \ket{x}
```
This describes the propagation from $x$ back to $x$ over an *imaginary* time $- i \hbar \beta$. We could write $e^{\-\beta H} = (e^{- \frac{\beta}{N} H})^N$ and carry out the same procedure as above by inserting resolutions of the identity. We get a similar answer but $t$ is replaced by an imaginary time $t = - i \tau$. The upshot is that
```{math}
Z = \int_{x(0) = x(\hbar \beta)} Dx(\tau)\exp\left(-\int_0^{\hbar \beta} d\tau \left(\frac{m}{2} (\del_{\tau} x)^2 + V(x(\tau))\right)\right)
```
In other words, the path itegral over trajectories in periodic imaginary time yields the quantum statistical mechanical partition function. 

### Connection to classical equilibrium statistical mechanics

If we start with the quantum path integral and simply set $t = - i\tau$, we have
```{math}
K(x_f, t_f; x_i,t_i) \to {\cal N} \int Dx \exp\left( \frac{-1}{\hbar} \int_{\tau_i}^{\tau_f}d\tau \left(\frac{m x_{\tau}^2}{2} + V(x(\tau))\right)\right)
```
If we set $\beta y = \frac{\tau}{\hbar}$, we have
```{math}
K(x_f, t_f; x_i,t_i) \to {\cal N} \int Dx \exp\left( -\beta \int_{y_i}^{y_f}dy \left(\frac{m x_{y}^2}{2\hbar^2\beta^2} + V(x(\tau))\right)\right)
```
If we take $y$ to be a position coordinate, the first term is the elastic energy for a string stretched along $y$ and defiormed in the perpednicular directions ${\vec x}$; $V(x)$ is the potential energy for each point on the string. So this is the classical partition function for an elastic string. This relationship, in which the time direction is transformed into a spatial direction, and the propagator into a classical partition fuinction for a system extended along the "imaginary time" direction, is a key relationship in modern theoretical physics.

### Nonequilibrium statistical mechanics: tochastic processes

Let us consider a particle moving under both friction the influence of a random force $\delta(t)$, in a limit that the friction force $F = - \lambda {\dot x}$ exceeds $m{\ddot x}/2$. Then the equation of motion is
```{math}
\lambda {\dot x} + V'(x) - \zeta = 0
```
where we have included an additional conservative force. We assume that the random noise has a Gaussian distribution at each time, and that the force is uncorrelated between different times. It should be clear that
```{math}
\begin{align}
P(x_f,t_f; x_i t_i) & = \int_{x(t_{i,f}) = x_{i,f}} Dx D\zeta \delta({\dot x} + V'(x) - \zeta)e^{- \frac{1}{2D} \int_{t_i}^{t_f} dt\zeta(z)^2}\\
& = \int_{x(t_{i,f}) = x_{i,f}} Dx e^{- \frac{1}{2D} \int_{t_i}^{t_f} \left({\dot x} + V'(x)\right)^2}
\end{align}
```
where we have set $\lambda = 1$. Here I have been careless about the delta function; in fact there should be a normalization or "Jacobian" factor that guarantees that $\int Dx \delta(\ldots) = 1$. There are related cases where that matters!

This has the structure of a path integral; however, instead of solving the Schroedinger equation it solves the Fokker-Planck equation for the probability density of the particle
```{math}
\frac{\del}{\del t_f} P(x_f,t_f; x_i,t_i) = \frac{\del}{\del x_f}(V'(x_f) P(x_f,t_f; x_i,t_i)) + D \frac{\del^2}{\del x_f^2} P(x_f,t_f;x_i,t_i)
```
which looks rather like the Schroedinger equation if we make time imaginary. This is not the only path integral formulation of stochastic processes, another is known as the "Martin-Siggia-Rose-de Dominicis-Janssen" path integral which can be derived as above but with the delta function first replaced by an integral representation that involves introducing another variable. 

Note that I have been careless here about the continuum limit for the paths, just as for the quantum case. All of this requires more care than I have given it.
