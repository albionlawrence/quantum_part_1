# Linear operators

In classical mechanics we saw that the states of the system were described as points on phase space. Observables of the system were functions on phase space, that could be described as generators of infinitesimal transformations.

In quantum mechanics, the space of ppossible states are described as vectors in a complex vector space (recall the discussion of photon polarization). Observables and generators of transformations are described as *operators* which map vectors to other vectors. More specifically, the correspond to *linear operators* which respect the linear structure of the vector space (addition and scalkar multiplication).

## Definitions

1. Let $V_1,V_2$ be two vector spaces over $\CF$. A **linear map** $F$ is a map
```{math}
f: V_1 \to V_2
```
such that
```{math}
:label: linear_map 
f(a \ket{v} + b \ket{w}) = a f(\ket{v}) + b f(\ket{w})\ \ \ \forall a,b \in \\CF\ ,\ \ \ket{v},\ket{w} \in V_1
```

Note that we can easily prove with this that for the zero vector $\ket{0}_1 \in V_1$, $f(\ket{0}_1) = \ket{0}_2 \in V_2$ where $\ket{0}_2$ is the zero vector.

2. For vector spaces $V_1, V_2$, over the *complex* numbers $\CC$, an **antilinear map** $f$ is a map $f: V_1 \to V_2$ such that
```{math}
:label: antilinear_map
f(a \ket{v} + b \ket{w}) = a^* f(\ket{v}) + b^* f(\ket{w})\ \ \ \forall a,b \in \ \CF\ ,\ \ \ket{v},\ket{w} \in V_1
```
where $a^*, b^*$ are the complex conjugates of $a,b$ respectively. This is important for defining adjoint vectors and normas of vectors.

3. Let $V$ be a vector space pver $\CF$. A **linear operator** *f* is a linear map $F: V \to V$. 

For $\CF = \CC$, an **antilinear operator** *g* is an antilinear map $g: V \to V$. 

Antilinear operators include the operator that implements time reversal, which is important in various condensed matter physics and particle physics contexts.

Abstractly we usually denote operators by capital letters $A$ and the action of operators as $A: \ket{V} \to A\ket{v}$.

### Examples

1. The identity operator ${\bf 1}\ket{v} = \ket{v} \forall \ket{v}$. 

2. The zero operator $\varnothing: \ket{V} \to \ket{0}$.

3. More generally, scalar multiplication by any scalar in $\CF$ is a linear operator.
