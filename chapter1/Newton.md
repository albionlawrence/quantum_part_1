# Newtonian mechanics.

## The second law 

The classic presentation of Newton's second law of motion is the famous

```{math}
:label: newton_second
\begin{align}
{\vec F}_{k = 1,ldots N}(t) & = m_k {\vec a}_k \\
& \equiv m_k \ddot{\vec x}_k(t) \\
& \equiv m_k \frac{d^2}{dt^2} {\vec x}_k(t)
\end{align}
```



where we have written this for $N$ particles with masses $m_k$ and positions ${\vec x}_k(t)$ in 3 dimensions. It is important that the force is considered to be a known function of time and of the positions and velocities at that time. This equation is the core of Newtonian mechanics. (The first and third laws are also deep and important of course).

This is a *second order differential equation in time*. The upshot of this is that if we know the positions and velocities of the particles at some initial time $t_i$, we know the trajectories at all time. To start with, at time $t_i + \Delta t$,

```{math}
:label: newton_evolve
\begin{align}
{\vec x}_k(t_i + \Delta t) & = {\vec x}_k(t_i) + \Delta t \dot{\vec x}_k(t_1) + \ldots\\
\dot{\vec x}_k(t_i + \Delta t) & = \dot{\vec x}_k(t_i) + \Delta t \ddot{\vec x}_k(t_i) + \ldots \\
& = \dot{\vec x}_k(t_i) + \Delta t {\vec F}_k(t_i) + \ldots
\end{align}
```

where we have used the Taylor expansion in the small time scale $\Delta t$, and dropped all terms of order ${\cal O}(\Delta t^2)$. So with the initial conditions and the force given at initial time $t_i$, we then know the positions and velocities at $t_i + \Delta t$. The same argument gives us the positions and velocitie s at ttime $t_i + 2 \Delta t$ and so forth. Of course we still have the higher-order terms, but eventually we can take the limit $\Delta t \to 0$ and we get a contionuous trajectory determined by the initial positions and velocities.

Note that this interative process is essentially how we would solve the problems on a computer, though we might find a more sophisticated representation of teh time derivative to control the ${\cal O}(\Delta t^2)$ errors.

The form given above is not the most general form of Newton's laws. In general, we write them as

```{math}
:label: second_general
{\vec F}_k(t) = \dot{\vec p}_k({\vec x}(t), \dot{\vec x}(t))
```

where ${\vec p}$ is the *momentum*. In the classic version of Newton's laws, ${\vec p}+k = m_k {\vec x}_k$. But there are many cases where the momentum tyhat appears is a more complicated function of positions and velocities. One is the case of a particle inn a magnetic field, which we will discuss later. Another is the case of particle mechanics in special relativity, where the s[atial momentum is:

```{math}
:label: sr_momentum
{\vec p}_k = \frac{m_k \dot{\vec x}_k}{\sqrt{1 - \dot{\vec x}_k^2/c^2}}
```

where $c = 3\times 10^8\ m/s$ is the speed of light. (The story look smore like the classic version if we work with 4-vectors and proper time, but we will shelve that for now.) This more general form of ${\vec p}$ is called *generalized momentum*.

Generalized momentum emerges naturally from Lagrangian mechanics, which will be one reason to adopt it. Another reason is that it allows us to compute trajectories of systems from the initial and final positions ${\vec x}_k(t_i), {\vec x}_k(t_f)$. That you should be able to do this seems reasonable. Given initial positions and velocities you can deduce the final positions, tyhe equations are deterministic, and the amount of data you specify each way is the same. (Actually it is more complicated than that because there can be multiple trajectories with didderent initial velocities and the same final positions: consider two particles moving in opposite directions on a circle, and bumping into each other later on).


