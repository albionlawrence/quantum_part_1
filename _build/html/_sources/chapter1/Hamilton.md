# Hamiltonian Mechanics

## Introduction

Recall that we can write the Euler-Lagrange equations as

```{math}
:label: el_redux
\frac{d p_I}{dt} = {\cal F}_I(q^I, \dot{q}^I)
```

where

```{math}
:label: gm_redux
p_I(q_I, \dot{q}^I) = \frac{\del L}{\del \dot{q^I}}
```

and

```{math}
:label: gf_redux
{\cal F}_I(q^I, \dot{q}^I) = \frac{\del L}{\del q^I}
```

and $L(q^I, \dot{q}^I,t)$ is the Lagrangian.

We can, in general, solve for {eq}`gm_redux` to get $\dot{q}^I(q^I,p_I)$. Now the state of the system can be described by specifying $(q^I, p_I)$; these are coordinates in *phase space*. We will demonstrate below that if we start with

```{math}
:label: hamilt
H(q^I,p_I) = p_I \dot{q}^I(q^I,p_I) - L(q^I,\dot{q}(q^I,p_I))
```

then we can rewrite the equations of motion as

```{math}
:label: he_intro
\begin{align}
\dot{q}^I & = \frac{\del H}{\del p_I}\\
\dot{p}_I & = - \frac{\del H}{\del q^I}
\end{align}
```

Note that when the Lagrangian is time-independent, the quantity {eq}`hamil` is exactly the quantity which we showed, via Noether's theorem, is conserved. $H$, called the *Hamiltonian* is the energy of this system. The equations {eq}`he_intro_ are known as *Hamilton's Equations* and they are completely equivalent to the Euler-Lagrange equations.

Why would we daopt this formalism?

1. If $I \in (1,\ldots, D)$, Hamilton's equations are $2D$ first order differential equations. If we specify the data $(q^I,p_I)$ at any initial time $t_0$,  these equations have a unique solution for all future times. Thus the state of the system at any time is copmpletely described by $(q^I, p_I)$. The set of all states so specified is known as *phase space*. Thus, the space of states is given by $2D$ independent variables, and we can formulate mechanics as an initial value problem.

2. Because Hamilton's equations are first order in time derivatives, they are particularly amenable to numerical integration.

3. Phase space has a geometric structure (it is a *symplectic manifold*) that gives powerful insights into the dynamics; Hamilton's equations are formulated nicely using this structure.

4. The description and consequence of symmetries emerges very naturally.

5. This structure emerges naturally from quantum mechanics.

## Derivation from Lagrangian dynamics

We start with the definition of generalized momentum in Lagrangian mechanics:

```{math}
:label: gm_deriv
p_I = \frac{\del L}{\del \dot{q}^I}(q^I, \dot{q}^I)
```

Assume this can be uniquely solved for $\dot{q}^I = \dot{q}^I(q^I,p_I)$. We can then performa a *Legendre transformation* to define the Hamiltonian $H(p,q)$:

```{math}
:label: legendre_trans
H(q^I,p_I) = p_I \dot{q}^I(q^I,p_I) - L(q^I,\dot{q}^I(q^I,p_I))
```

The Legendre transform appears in both classical mechanics and, in various ways, in statistical mechanics. I will have to put aside the beautiful geometric interpretation of the transform, but I highly recommend {cite:p}`Zia_2009`, whih you can find on the [arXiv.org website](https://arxiv.org/abs/0806.1147).

Given this we can compute

```{math}
:label: he_one
\frac{\del H}{\del p_I}\Big|_{p_{J\neq I}, q^J\ fixed} = \dot{q}^I + p_J \frac{\del \dot{q}^J}{\del p^I} - \frac{\del \dot{q}^J}{\del p^I}\frac{\del L}{\del \dot{q}^J}
```

where the final term comes from using the chain rul to compute $\del L/\del p_I$. Using {eq}`gm_deriv`, this last term becomes equivalent to the second term on the right hand side, and we have one set of Hamilton's equations:

```{math}
:label: he_two
\dot{q}^I = \frac{\del H}{\del p_I}
```

Similarly,

```{math}
:label: he_three
\frac{\del H}{\del q^I}\Big|_{q^{J \neq I}, p_J\ fixed} = p_J \frac{\del \dot{q}^J}{\del q^I} - \frac{\del L}{\del q^I} \Big|_{\dot{q}^I\ fixed} - \frac{\del \dot{q}^J}{\del q^I} \frac{\del L}{\del \dot{q}^J}
```

where in the first term on the right hand side, we have used the fact that we are keepig all $P_J$ fixed in the partial derivative; the second two terms are the derivative of $L(q,\dot{q}(q,p))$ using the chain rule. Using {eq}`gm_deriv`, the first and last terms on the right hand side cancel. Finally, we can use the EUler-Lagrange equation for the middle term to set 

```{math}
:label: el_again
\frac{\del L}{\del q^I} = \frac{d}{dt} \frac{\del L}{\del\dot{q}^I} = \dot{p}_I
```

so we have the remaining set of Hamilton's equations,

```{math}
:label: he_four
\dot{p}_I = - \frac{\del H}{\del q^I}
```

### Examples

1. Particle in a conservative force field.

Start with the Lagrangian

```{math}
:label: nr_part_lag
L(\vec{x},\dot{\vec{x}}) = \half m \dot{\vec{x}}^2 - V({\vec x})
```

The generalized momentum is

```{math}
:label: nr_gen_mom
\vec{p} = m \dot{\vec{x}}
```

so that $\dot{\vec{x}} = \frac{\vec p}{m}$.

The Hamiltonian is thus

```{math}
:label: nr_legendre
\begin{align}
H & = \vec{p} \cdot \dot{\vec{x}} - \half m \dot{\vec{x}}^2 + V({\vec x}) \\
& = \frac{\vec{p}^2}{m} - \half \frac{\vec{p}^2}{2m} + V\\
& = \frac{\vec{p}^2}{2m} + V({\vec x})
\end{align}
```

which is indeed the total energy (kinetic plus potential). We can write Hamilton's equations as

```{math}
:label: nr_Hamilton
\begin{align}
\dot{x}^i & = \frac{\del H}{\del p_i} = \frac{p_i}{m}\\
\dot{p}_i & = - \frac{\del H}{\del x^i} = - \frac{\del V}{\del x^i}
\end{align}
```

The first is the known relation between momentum and velocity; the second is then Newton's laws written in terms of the momentum. If we take the time derivative of the first equation, multiply by $m$, and use the second to solve for $\dot{p}_i$ we have the classic second law:

```{math}
:label: ham_second_law
m\ddot{x}^i = - \frac{\del V}{\del x^i}
```

Note that this gives three second order differential equation; Hamilton's equations give a natural unpacking of this equation into six *first*-order differential equations which are often easier to integrate (analytically or numerically).

2. Free particle in polar coordinates

Here we start with 

```{math}
:label: free_polar
L = \half m (\dot{r}^2 + r^2 \dot{\phi}^2)
```

The generalzied momenta are:

```{math}
:label: polargenmom
\begin{align} 
p_r & = m \dot{r} \Rightarrow \dot{r} = \frac{p_r}{m}\\
p_{\phi} & = m r^2 \dot{\phi} \Rightarrow \dot{\phi} = \frac{p_{\phi}}{m r^2}
\end{align}
```

Thus the Hamiltonian is:

```{math}
:label: polar_ham
\begin{align}
H & = p_r \dot{r} + p_{\phi} \dot{\phi} - \half m (\dot{r}^2 + r^2 \dot{\phi}^2)\\
& = \frac{p_r^2}{2m} + \frac{p_{\phi}^2}{2 m r^2}
\end{align}
```

Hamilton's equations become:

```{math}
:label: polar_he
\begin{align}
\dot{r} & = \frac{\del H}{\del p_r} = \frac{p_r}{m}\\
\dot{p}_r & = - \frac{\del H}{\del r} = \frac{p_{\phi}^2}{m r^3}\\
\dot{\phi} & = \frac{\del H}{\del p_{\phi}} = \frac{p_{\phi}}{m r^2}\\
\dot{p_{\phi}} & = - \frac{\del H}{\del \phi} = 0
\end{align}
```

Note that this last equation is a re-statement of the conservaton of angular momentum, following from $\phi$ being a cyclic coordinate.

3. Charged prrticle in a magnetic field. 

As we stated before, if $\vec{B} = \vec{\nabla}\times\vec{A}$ for the vector potential $\vec{A}$,the Lagrangian is:

```{math}
:label: cpb_lag
L = \half m \dot{\vec{x}}^2 + \frac{e}{c} \dot{\vec{x}}\cdot \vec{A}
```

The conjugate momentum is

```{math}
:label: cpb_cmom
p_i = \frac{\del L}{\del \dot{x}^i} = m \dot{x}^i + \frac{e}{c} A^i \Rightarrow \dot{x}^i = \frac{1}{m} \left(p_i - \frac{e}{c} A^i\right)
```

With a little work we find:

```{math}
:label: cpb_ham
\begin{align}
H & = p_i \dot{x^i} - \half m \dot{\vec{x}}^2 - \frac{e}{c} \dot{\vec{x}}\cdot\vec{A}\\
& = \frac{1}{m} p_i \left(p_i - \frac{e}{c} A_i\right) - \frac{m}{2 m^2}\left({\vec p} - \frac{e}{c} \vec{A}\right)^2 - \frac{e}{mc} \left({\vec p} - \frac{e}{c} \vec{A}\right)^2 - \frac{e}{mc} \left({\vec p} - \frac{e}{c} \vec{A}\right)\cdot\vec{A}\\
& = \frac{1}{2m}\left(\vec{p} - \frac{e}{c}\vec{A}\right)^2
\end{align}
```
