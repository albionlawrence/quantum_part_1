# Symmetries and conservation laws

Consider a Lagrangian $L(q^I, \dot{q}^I)$. A *symmetry* is a transformation

```{math}
:label: gen_transf
q^I \to (q^I)'(q^I)
```

such that

```{math}
:label: symmetry_condition
L(q^I, \dot{q}^I) = L((q^I)', (\dot{q}^I)') + \frac{d\Lambda(q,\dot q)}{dt}
```

where $(\dot{q}^I)' = \frac{d}{dt} (q^I)'$. The last term in {eq}`gen_transf` is a total derivative; thus (as one can see by studying the resulting action) it does not contribute to the equations of motion. 

In other words, the action is invariant up to a boundary term.

## Example: cyclic coordinates

The simplest example is a Lagrangian which does not even depend on soem subset of the coordinates, only their velocities. Consider $L(q^I, \dot{q}^I)$ to be independent of $q^k$ for some $k$ (but *still depend on* $\dot{q}^k$). Then the transformation $q^k \to (q^k)' = q^k + \alpha$ for $\alpha$ a constant real number. Clearly $\dot{q}^k$ is invariant, so the entire Lagrangian is. We call $q^k$ a *cyclic coordinate*.

What does this mean for the equations of motion? Well, we know that 

```{math}
:label: cyclic_force
{\cal F}_k = \frac{\del L}{\del q^k} = 0
```

The Euler-Lagrange equations for $q^k$ become:

```{math}
:label: cyclic_el
\dot{p}^k = \frac{\del L}{\del \dot{q}^k} = 0
```

In other words, the generalized momentum $p^k$ is *conserved*.

Some examples:

1. Consider $L = \half m(\dot{x}^2 + \dot{y}^2 + \dot{z}^2) - V(x,y)$. Then $z$ is a cyclic coordinate, and the momentum $p_z = m \dot{z}$ is conserved, as a result of invariance of the action under translations in teh $z$ direction.

2. A particle in polar coordinates in a central force, $L = \half m (\dot{r}^2 + r^2 \dot{\phi}^2) - V(r)$. We studied this last time; the cyclic coordinate is $\phi$ and the conserved conjugate momentum os $p_{\phi} = m r^2 \dot{\phi}$ which is the angular momentum. Thus, invariance under rotations implies the conservation of angular momentum.

These suggest a more general story to which we now turn.

## Noether's theorem

Noether's theorem applies to *continuous* symmetries, that is, to a continuous family of transformations $(q^I)' = (q^I)'(q^I\ ; \alpha)$ where $\alpha$ is some real parameter and $(q^I)'(q^I\ ; 0) = q^I$. Noether showed that every such famikly of symmetries implied a *conservation law*.

We will provide a constuctive proof. Let $(q^I)' = q^I + \delta q^I$. If this transformation is a symmetry, then

```{math}
:label: trans_lag
\begin{align}
L(q^I, + \delta q^I, \dot{q}^I + \delta \dot{q}^I) & = L(q^I \dot{q}^I) + frac{d\Lambda}{dt} \\
= L(q^I, \dot{q}^I) + \delta q^I \frac{\del L}{\del q^I} + \delta \dot{q}^I \frac{\del L}{\del \dot{q}^I} + {\cal O}(\delta q^2)
\end{align}
```

Working to first order in $\delta q$, the fact that this is a symmetry means that

```{math}
:label: constructing_conserved_q
\begin{align}
\delta q^I \frac{\del L}{\del q^I} + \delta \dot{q}^I \frac{\del L}{\del \dot{q}^I} & = \frac{d\Lambda}{dt}\\
& = \delta q^I \frac{\del L}{\del q^I} + \frac{d}{dt} \left(\delta q^I \frac{\del L}{\del \dot{q}^I}\right) - \delta q^I \frac{d}{dt} \frac{\del L}{\del \dot{q}^I}
\end{align}
```

Now the first and last terms on the second line are just $\delta q^I$ times the Euler-Lagrange equations, and so vanish if $q^I$(t)$ satisfies the classical equations of motion. When it does, we are left with

```{math}
:label: Noether_charge_cons
\frac{d}{dt} \left(\delta q^I \frac{\del L}{\del \dot{q}^I} - \Lambda\right) = \frac{d}{dt} \left(\delta q^I p_I - \Lambda\right) = 0
```

Thus we have a *conserved charge*, sometimes called a *Noether charge, 

```{math}
:label: Noerther_charge
Q = \delta q^I p_I - \Lambda
```

for every infinitesimal symmetry transformation $q \to q + \delta q$.


### Examples.

1. We have given two classic examples in the discussion above, of linear and angular momentum, and I invite the student to show that the charges $Q$ associated to translational and rotational invariance lead to the same conserved quantities. 

2. Similarly, one can work in Cartesian coordinates with the infinitesimal rotation
$x \to \cos\epsilon x - \sin \epsilon y$ and $y \to \cos \epsilon y + \sin \epsilon x$. For infinitesimal $\epsilon$, $\delta x = - \epsilon y$ and $\delta y = \epsilon x$. For the Lagrangian $L = \half m (\dot{x}^2 + \dot{y}^2) = V(\sqrt{x^2 + y^2})$, which is clearly invariant under rotations, the associated Noether charge is

```{math}
:label: rot_noether
Q = \delta x p_x + \delta y p_y = - y p_x + x p_y = L
```

where $L$ is the angular momentum in Cartesioan coordinates. I leave it to the student to show that this is the same as the generalized momentum $p_{\phi}$ dreived in polar coordinates.

3. Another important symmetry is *time translation invariance*; the symmetry is a shift $t \to t + \eps$. Consider a Lagrangian which is explicitly time-independent. Then 

```{math}
:label: time_shift
\begin{align}
L(q(t + \eps), \dot{q}(t + \eps)) & = L(q + \eps \dot{q}, \dot{q} + \eps \ddot{q}) \\
& = L(q,\dot{q}) + \eps \left[\dot{q}^I \frac{\del L}{\del q^I} + \ddot{q}^I \frac{\del L}{\del \dot{q}^I}\right]\\
& = L + \eps \frac{d}{dt} L(q,\dot{q})
\end{align}
```

The conserved quantity is thus

```{math}
:label: tt_conserved
Q = \eps (\dot{q}^I p_I - L)
```
The quantity $H - \dot{q}^I p_I - L$ is known as the *Hamiltonian* and the energy can be defined as the value of this Hamiltonian. As an example, for $L = \half m \dot{\vec{x}}^2 - V({\vec x})$, the Hamiltonian is clearly

```{math}
:label: simplest_H
\begin{align}
H & = \dot{\vec x} \cdot \vec{p} - \half m \dot{\vec{x}}^2 + V({\vec x})\\
& = \frac{1}{2m}{\vec p}^2 + V
\end{align}
```

where in the final line we used $\vec{p} = m\dot{\vec{x}}$. In this case $H$ is clearly the kinetic plus potential energy. More generally, we *define* $H$ as the energy of the system, and so the conservation of energy is a consequence of invariance under time translation.


