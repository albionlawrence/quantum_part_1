# Lagrangian Mechanics

## Principle of Stationary Action

The basic object in Lagrangian mechanics is...you guessed it...a *Lagrangian*; this is a function of the positions and velocities of one or several particles:

```{math}
:label: Lagrangian
L = L(x^a_k(t), {\dot x}^a_k(t), t)
```

where $a \in \{1,\ldots,d\}$ is the coordinate index for particles in $d$ dimensions (for example, if $d = 3$ we might call $x^1 \equiv x$, $x^2 \equiv y$, $x^3 \equiv z$), and $k = 1,\ldots,M$ labels different particles. Note that $L$ is a *function* of $x, {\dot x}$ at a fixed time; thus, even if there is no explicit $t$-dependence, if $x^a(t)$ is a known trajectory, $L$ depends on $t$.

Given $L$, and initial and final times $t_{i,f}$ we can define an *action functional* (usually called just the action):

```{math} 
:label: action_definition
S[\{x(t)\}] = \int_{t_i}^{t_f} dt L( x^a_k(t), {\dot x}^a_k(t), t)
```

For any trajectory $x^i(t)$, defined between $t_i$ and $t_f$, the action is a real number. We call it a "functional" because it can be thought of as a function whose dependent variables are not a collection of discrete numbers, but functions.

The principle of stationary action (sometimes call the "principle of least action", but this is something of a misnomer). We consider all paths with fixed coordinates at $t_{i,f}$, defined as

```{math}
x^a_{k, } = x^a_k(t_i)\ ; \ \ x^a_{k,f} = x^a_k(t_f)
```

A "classical trajectory" $x^a_{k,c}$ is one that satisfies the boundary conditions and one for which the action does not change if we make an infinitestimal change of the path. That is, consider two trajectories:

```{math}
	x^a_{k,c}(t)\ ; \ x^a_{k,c}(t) + \epsilon \delta x^a_k
```	

satisfying the same boundary conditions. This means that $\delta x^a_{k}(t_{i,f)) = 0$. We take $\eps \ll 1$ to be a small dimensionless parameters. For small enough $\eps$ we can therefore expand 

```{math}
S[\{x^a_{k,c}(t) + \epsilon \delta x^a_k)\}] = S[\{x^a_k(t)\}] + \eps \delta S^{(1)} + \eps^2 \delta S^{(2)} + {\cal O}(\eps^3)
```

If $\Delta^{(1)}S[\{x^a_{k,c}\}] = 0$, then $x^a_{k,c}$ is a classical trajectory.

## The Euler-Lagrange equations

So far this is all fairly abstract. In fact the principle of stationary action leads to a set of differential equations known as the *Euler-Lagrange* equations which generalize Newton's second law. We can write down these equations explicitly in terms of $L$, by computing $S^{(1)}$. Let us cary out the expansion explicitly:

```{math}
\begin{align}
S[\{x^a_{k,c}(t) + \epsilon \delta x^a_k)\}] & = S[\{x^a_k(t)\}] + \eps \delta S^{(1)}+ \ldots \\
& = \int_{t_i}^{t_f} dt L(x^a_{k,c}(t) + \epsilon \delta x^a_k, \dot{x}^a_{k,c}(t) + \epsilon \delta \dot{x^a_k}) + {\cal O}(\eps^2)\\
& = S[\{x^a_k(t)\}] + \eps \int_{t_i}^{t_f} \left[ \delta x^a_k \frac{\del L}{\del x^a_k(t)} + \delta {\dot x}^a_k(t) \frac{\del L}{\del \dot{x}^a_k(t)}\right]\big|_{x = x_c}
+ {\cal O}(\eps^2)
\end{align}
```

where we are using the Einstein summation notation (see Appendix). Note that $L$ is a standard function of the coordinates and velocities at a fixed time $t$, so that this makes sense. Now, recall that $\delta \dot{x} = \frac{d}{dt} \delta x$. Integrating the second term in the last line by parts, we find that

```{math}
\delta S^{(2)} = \int_{t_i}^{t_f} dt \delta x^a_k \left[ \frac{\del L}{\del x^a_k} - \frac{d}{dt} \frac{\del L}{\del \dot{x}^a_k}\right]\Big|_{x = x_c} + \delta x^a_k \frac{\del L}{\del \dot{x}^a_k} \Big|^{t = t_f}_{t = t_i} 
```

Now, by the boundary conditions, $\delta x^a_k(t_{i,f}) = 0$ so that the final boundary term vanishes. We have demanded that $\delta S^{(1)}$ vanish for *any* infinitesimal deformation of $x^a_{k,c}$, that is for *any* $\delta x^a_{k,c}$ vanishing at $t_{i,f}$ (at least, if $\eps$ is sufficiently small). Thus, the principle of stationary action is equivalent to the *Euler-Lagrange equations*:

```{math}
:label: euler_lagrange
\frac{\delta S}{\delta x^a_k(t)}\Big|_{x = x_c} \equiv \frac{\del L}{\del x^a_i(t)}(x^a_{k,c}, \dot{x}^a_{k,c}(t)) - \frac{d}{dt} \frac{\del L}{\del \dot{x}^a_i(t)}(x^a\
_{k,c}, \dot{x}^a_{k,c}(t)) = 0
```

Note that this defines a *functional derivative* of $S$. $\frac{\delta S}{\delta x}$. 

Without going any further, we can see that this will define $d M$ second order differential equations in time for the $dM$ variables $x^a_k$.

This formalism naturally includes Newton's laws. Consider the following Lagrangian for a single particle with mass $m$ in $d$ dimensions:

```{math}
:label: newton_lag
L = \half m \dot{\vec x} \cdot \dot{\vec x} - V({\vec x})
```

Here ${\vec V}\cdot{\vec V} = V^j V^j$ for any vector ${\vec V}$, where $j$ labels the components. The Euler-Lagrange equations give us:

```{math}
:label: el_newton
- \frac{\del V}{\del x^i} - m \frac{d}{dt} \dot{x}^i = 0
\Rightarrow m \ddot{x}^i = - \left(\vec{\nabla} V\right)^i \equiv F^i
```

Here ${\vec F} = - \vec{\nabla} V$ is the conservative force associated to the potential $V$. Note that we have a definite restriction on systems which are well-described by Lagrangian dynamics: many forces are not easily or usefully described in the Lagrangian framework. A classic example is a particle subject to a frictional force linear in velocity:

```{math}
:label: friction_example
m \ddot{x} = - \lambda \dot{x} - V'(x)
```

(It is not impossible to get this from a variational principle directly in terms of $x$ but this formulation ends up not being especially useful. More insight can be gained by embedding the system in a larger system so that the dynamics of $x$ alone has friction; the energy lost by friction is exchanged with the larger system. But then the dynamics of all of the degrees of freedom can be described by a more conventional if complicated Lagrangian.)

On the other hand, this formalism allows us to generalize away from Newton's laws in many other directions, including other velocity-dependent forces such as the Lorentz force, and provides new tools for constraining the motion.

## Euler-Lagrange equation and generalized coordinates

As we know, there is a lot more to classical mechanics than just the motion of a collection of point particles in Euclidean space. Other systems include:

1. The motion of the orientational degrees of freedom of a rigid body such as a top or a satellite.
2. The dynamics of some elastic system such as a rubber sheet or even a piece of metal.



