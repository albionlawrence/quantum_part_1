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
:label: lagrangian_bc
x^a_{k, } = x^a_k(t_i)\ ; \ \ x^a_{k,f} = x^a_k(t_f)
```

A "classical trajectory" $x^a_{k,c}$ is one that satisfies the boundary conditions and one for which the action does not change if we make an infinitestimal change of the path. That is, consider two trajectories:

```{math}
:label: deformed_trajectories
	x^a_{k,c}(t)\ ; \ x^a_{k,c}(t) + \epsilon \delta x^a_k
```	

satisfying the same boundary conditions. This means that $\delta x^a_{k}(t_{i,f)) = 0$. We take $\eps \ll 1$ to be a small dimensionless parameters. For small enough $\eps$ we can therefore expand 

```{math}
:label: expand_action
S[\{x^a_{k,c}(t) + \epsilon \delta x^a_k)\}] = S[\{x^a_k(t)\}] + \eps \delta S^{(1)} + \eps^2 \delta S^{(2)} + {\cal O}(\eps^3)
```

If $\Delta^{(1)}S[\{x^a_{k,c}\}] = 0$, then $x^a_{k,c}$ is a classical trajectory.

## The Euler-Lagrange equations

So far this is all fairly abstract. In fact the principle of stationary action leads to a set of differential equations known as the *Euler-Lagrange* equations which generalize Newton's second law. We can write down these equations explicitly in terms of $L$, by computing $S^{(1)}$. Let us cary out the expansion explicitly:

```{math}
:label: explicit_expansion
\begin{align}
S[\{x^a_{k,c}(t) + \epsilon \delta x^a_k)\}] & = S[\{x^a_k(t)\}] + \eps \delta S^{(1)}+ \ldots \\
& = \int_{t_i}^{t_f} dt L(x^a_{k,c}(t) + \epsilon \delta x^a_k, \dot{x}^a_{k,c}(t) + \epsilon \delta \dot{x^a_k}) + {\cal O}(\eps^2)\\
& = S[\{x^a_k(t)\}] + \eps \int_{t_i}^{t_f} \left[ \delta x^a_k \frac{\del L}{\del x^a_k(t)} + \delta {\dot x}^a_k(t) \frac{\del L}{\del \dot{x}^a_k(t)}\right]\big|_{x = x_c}
+ {\cal O}(\eps^2)
\end{align}
```

where we are using the Einstein summation notation (see Appendix). Note that $L$ is a standard function of the coordinates and velocities at a fixed time $t$, so that this makes sense. Now, recall that $\delta \dot{x} = \frac{d}{dt} \delta x$. Integrating the second term in the last line by parts, we find that

```{math}
:label: first_order_variation
\delta S^{(1)} = \int_{t_i}^{t_f} dt \delta x^a_k \left[ \frac{\del L}{\del x^a_k} - \frac{d}{dt} \frac{\del L}{\del \dot{x}^a_k}\right]\Big|_{x = x_c} + \delta x^a_k \frac{\del L}{\del \dot{x}^a_k} \Big|^{t = t_f}_{t = t_i} 
```

Now, by the boundary conditions, $\delta x^a_k(t_{i,f}) = 0$ so that the final boundary term vanishes. We have demanded that $\delta S^{(1)}$ vanish for *any* infinitesimal deformation of $x^a_{k,c}$, that is for *any* $\delta x^a_{k,c}$ vanishing at $t_{i,f}$ (at least, if $\eps$ is sufficiently small). Thus, the principle of stationary action is equivalent to the *Euler-Lagrange equations*:

```{math}
:label: euler_lagrange
\frac{\delta S}{\delta x^a_k(t)}\Big|_{x = x_c} \equiv \frac{\del L}{\del x^a_i(t)}(x^a_{k,c}, \dot{x}^a_{k,c}(t)) - \frac{d}{dt} \frac{\del L}{\del \dot{x}^a_i(t)}(x^a\
_{k,c}, \dot{x}^a_{k,c}(t)) = 0
```

The first equality defines a *functional derivative* of $S$. In the end, all that matters is that this vanishes -- that $S$ does not vary at ${\cal O}(\eps)$. Classical mechanics does not care whether $S$ is a local or global maximum, local or global minimum, or "saddle point" in which some deformations increase the action at ${\cal O}(\eps^2)$ and oher deformations decrease $S$.

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

There is a lot more to classical mechanics than just the motion of a collection of point particles in Euclidean space. Other systems include:

1. The motion of the orientational degrees of freedom of a rigid body such as a top or a satellite.
2. The dynamics of some elastic system such as a rubber sheet or even a piece of metal.
3. Continuum fields such as the electromagnetic or gravitational fields

All of these can be described within the framework of Lagrangian mechanics.

In general we start with a set of *generalize coordinates* $q^I$. These could be the position variables $x^a_k$ for particles in Euclidean space, or anyo of the above examples. If we have a Lagrangian $L(q^I, {\dot q}^I, t)$, and an action

```{math}
:label: gen_action
S[\{q^I(t)\}] = \int_{t_i}^{t_f} dt L(q^I, {\dot q}^I, t)
```

The Euler-Lagrange equations are

```{math}
:label: gen_el
\frac{\del L}{\del q^I} - \frac{d}{dt} \frac{\del L}{\del \dot{q}^I} = 0
```

If we define the *generalized momentum* as

```{math}
:label: gen_mom
p_I(q^I, \dot{q}^I) = \frac{\del L}{\del\dot{q}^I}
```

and the *generalized force* as 

```{math}
:label: gen_force
{\cal F}_I(q^I, \dot{q}^I) = \frac{\del L}{\del q^I}
```

then the Euler-Lagrange equations can be written as

```{math}
:label: gen_second
\frac{d}{dt} p_I = {\cal F}_I
```

which clearly takes the form of Newton's second law.

All of this discussion has been fairly abstract, so let us study a few examples.


### Particle in a magnetic field

Alternatively we consider the case where we have standard coordinates but a nontrivial generalized momentum. That is, consider a particle with mass $m$ and charge $e$ in a static magnetic field $\vec{B}$. Maxwell's equations (assuming no magnetic monoploes; we haven't observed them at any rate) imply that $\vec{\nabla} \cdot \vec{B} = $, which means that in Euclidean space without any holes we can use the Poincar\'e theorem to write

```{math}
:label: vector_potential
\vec{B} = \vec{\nabla} \times \vec {A}
```

for some $\vec{A}$. I claim the correct Lagrangian for a particle in this field is:

```{math}
:label: charged_particle_B
L = \half m \dot{\vec{x}}^2 + \frac{e}{c} \dot{\vec{x}} \cdot \vec{A}(x)
```

The generalized momentum is

```{math}
:label: B_gen_mom
p_i = \frac{\del L}{\del \dot{x}^i} = m \dot{x}^i + \frac{e}{c} A^i
```

and the generalized force is

```{math}
:label: B_gen_force
{\cal F}^i = \frac{\del L}{\del x^i} = \frac{e}{c} \dot{x}^j \del_i A^j
```

The Euler-Lagrange equations become

```{math}
:label: B_EL
\begin{align}
	\frac{d p^i}{dt} & = m \ddot{x}^i + \frac{e}{c} \dot{x}^j \del_j A^i\\
	& = {\cal F} \\
	& = \frac{e}{c} \dot{x}^j \del_i A^j
\end{align}
```

so that

```{math}
:label: B_eom
\begin{align}
m \ddot x^i & = \frac{e}{c} {\dot x}^j (\del_i A^j - \del_j A^i)\\
& = \frac{e}{c} {\dot x}^j \epsilon_{ijk} (\vec{\nabla}\times {\vec A})^k\\
& = \frac{e}{c} {\dot x}^j \epsilon_{ijk} B^k \\
& = \frac{e}{c} (\dot{\vec{x}}\times\vec{B})^i
\end{align}
```

which is the Lorentz force law.

Note that the final equations of motion depend on the magnetic field $B$ and not on the vector potential $A$. People often assume that the physical fields are the electromagnetic fields, and $A$ is not unquely determined since the "gauge transformation"

```{math}
:label: gauge_trans
\vec{A} \to \vec{A} + \vec{\nabla} \Lambda
```

does not change $E$ or $B$. The generalized momentum *does* depend explicitly on ${\cal A}$, and so in this case is not invariant under gauge transformations.

## Lagrangians and coordinate changes

### General statement

Consider a change of coordinates from $x^a_k$ to $q^{I = 1,\ldots Md}$.
In this case we can write
```{math}
 :label: change_coords_lag
 L(x, \dot{x}) = L(x(q), \dot{x}(q,\dot q) = \tilde{L}(q, \dot{q})
```

where

```{math}
:label: gc_chain
\dot{x}^a_k = \dot{q}^I \frac{\del x^a_k}{\del q^I}
```

We claim that the Euler-Lagrange equations for $x^a_k$ derived from $L$ and the Euler-Lagrange equations for $q^I$ derived from ${\tilde L}$ are in fact equivalent. That is,

```{math}
\frac{\del L}{\del x^a_k} - \frac{d}{dt} \frac{\del L}{\del\dot{x}^a_k} = 0 \Leftrightarrow \frac{\del {\tilde L}}{\del q^I} - \frac{d}{dt} \frac{\del {\tilde L}}{\del \dot{q}^I} = 0
```

The point is that you can perform your coordinate transformations at the level of the Lagrangian, and *then* compute the Euler-Lagrange equations in the new coordinates, which is often easier than computing the change of variables at the level of the equations of motion.


To start with, the partial derivatives in {eq}`gc_chain`

```{math}
:label: jacobian_mat
{\cal M}(ak\ ; I) = \frac{\del x^a_k}{\del q^I}
```

can be thought of as an $dM \times dM$ matrix at a given value of $q^I$; this is the "Jacobian" of the coordinate transformation between $x$ and $q$, and it is an invertible matrix if the coordinate transformation is itself non-singular (is a good coordinate transformation). In particular, we can define the inverse Jacobian as

```{math}
:label: inverse_Jacobian
{\cal M}^{-1}(I\ ; ak)
```

By the chain rule, 

```{math}
:label: jac_inv_jac
{\cal M}(I'\; ak) {\cal M}(ak, I) = \frac{\del q^{I'}}{\del x^a_k} \frac{\del x^a_k}{q^I} = \frac{\del q^{I'}}{\del q^I} = \delta^I_{I'}
```

where $\delta^I_{I'}$ is the Kronecker delta symbol (see the Appendix for a definition). We can similarly show that

```{math}
:label: jac_jac_inv
{\cal M}(ak\; I) {\cal M}^{-1}(I\; a'k') = \delta^a_{a'} \delta^k_{k'}
```

To see why invertability is important let us think of the canse of $dM = 1$. Then the matrix is just ${\cal M} = \frac{\del x}{\del q}$. Consider a particular point $q_0$ about which we wish to study the coordinate transformation. the value of $x$ is $x_0 = x(q_0)$. At an infinitesimal distance $\delta q$ away from $q_0$, we have

```{math}
:label: oned_transf
x(q_0 + \delta q) = x_0 + \frac{\del x}{\del q} \delta q + {\cal O}(\delta q^2)
```

Now the inverse of $\frac{\del x}{\del q}$ is just $\left(\frac{\del x}{\del q}\right)^{-1}$, so ${\cal M}$ fails to be invertible if it is zero. If it is zero at $q_0$ the $x = x_0 + {\cal O}(\delta q^2)$. In ither words, at leading order in $\delta q$,$x$ does not change and at this order the coordinate change from $q \to x$ is a many-to-one map. For the rest of this section we will assume the coordinate transformation is invertible but there are many cases where it fails to be at least at a point: a good example is the transformation from Catrtesian to polar coordinates in $d = 2$, for which the origin is a singular point.

Now, 

```{math}
:label: gen_mom_transf
\begin{align}
p_I & = \frac{\partial {\tilde L}}{\partial \dot{q}^I}\\
& = \frac{\del}{\del \dot{q}^I} L(x(q), {\cal M}(ak; I) \dot{q}^I)\\
& = {\cal M}(ak\ ; I) p^a_k
\end{align}
```

while

```{math}
:label: gen_force_transf
\begin{align}
{\cal F}_I & = \frac{\del}{\del q^I} L(x(q), {\cal M}(ak\ ; I) \dot{q}^I) \\
& = {\cal M}(ak\ ; I) {\cal F}^a_k + \frac{\del {\cal M}(ak\ ; J)}{\del q^I} \dot{q}^J p^a_k 
\end{align}
```

The Euler-Lagrange equations we derive from ${\tilde L}$ for $q^I$ are:

```{math}
:label: transf_el
\begin{align}
\frac{d}{dt} p_I - {\cal F}_I & = \frac{d}{dt} \left(\frac{\del x^a_k}{\del q^I} p_a^k\right) - \frac{\del x^a_k}{\del q^I} {\cal F}^a_k - \frac{\del^2 x^a_k}{\del q^I \del q^J} \dot{q}^J p^a_k \\
& = \frac{\del x^a_k}{\del q^I}\left({\dot p}^a_k - {\cal F}^a_k\right)
+ \frac{\del^2 x^a_k}{\del q^J \del q^I} \dot{q}^J p_a^k -  \frac{\del^2 x^a_k}{\del q^I \del q^J} \dot{q}^J p^a_k \\
& = {\cal M}(ak\ ; I) \left(\dot{p}^a_k - {\cal F}^a_k\right)
\end{align}
```

The second line follows from applying Leibniz's rule to the time derivative of ${\cal M} p$. The last line is an invertible matrix times the Euler-Lagrange equations for $x^a_k$ derived from $L$. Thus the two forms of the Euler-Lagrange equations are equivalent; one vanishes if and only if the other does (assuming the coordinate transformation is invertible).

### Example: changing to polar coordinates

Consider a single particle in two dimensions with the Lagrangian

```{math}
:label: twod_lagr
L = \half m (\dot{x}^2 + \dot{y}^2) - V(r = \sqrt{x^2 + y^2})
```

The Euler-Lagrange equations are:

```{math}
:label: twod_el
\begin{align}
m \ddot{x} & = - \del_x V = - \frac{x}{r} V'(r)\\
m \ddot{y} & = = \del_y V = - \frac{y}{r} V'(r)\\
\end{align}
```

We can consider instead polar coordinates $(r,\phi)$, defined by:

```{math}
:label: polar_coords
x = r \cos\phi\ , \ \ y = r \sin \phi
```

To change to equations in polar coordinates, we find:

```{math}
\ddot{x} = \ddot{r}\cos\phi - 2 \dot{r} \dot{\phi} \sin\phi - r \ddot\phi\cos\phi
```
 
and similarly for $y$. On the other hand, we can quickly show that

```{math}
L = \half m \left(\dot{r}^2 + r^2 \dot{\phi}^2\right) - V(r)
```

where I have tropped the tilde. Note that $r\dot{\phi}$ is the physical velocity in the ${\hat \phi}$ direction, and $\dot{r}$ is of course the radial velocity $v^{\phi}

We can first compute the generalized momentum

```{math}
\begin{align}
p_r & = \frac{\del L}{\del \dot{r}} = m \dot{r}\\
p_{\phi} & = \frac{\del L}{\del\dot{\phi}} = m r^2 \dot \phi = m r v^{\phi} = \ell
\end{align}
```

The point is that the generalized momentum $p_{\phi}$ can be identified with the alngular momentum $\ell$ about the origin $r = 0$. The Euler-Lagrange equations are:

```{math}
\begin{align}
m \ddot{r} & = - \del_r V\\
\frac{d}{dt} m r^2 \phi & = \frac{d}{dt} \ell = 0
\end{align}
```

which you can also show are the equations of motion by applying the transformation from Euclidean to polar coordinates to the Euler-Lagrange equations for $x,y$. Note that $V = V(r)$ inplies that there is no generalized force associated to the generalized momentum or angular momentum $\ell$; in other words, there is no torque. There would be torque (aka a generalized force in the angular direction) if $V$ had any $\phi$-dependence in it. The relationship between the independence of $L$ of certain coordinates, and a conservation law such as the conservation of angular momentum, is a general story we will return to below. 

