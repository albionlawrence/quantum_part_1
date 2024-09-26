# Vector spaces

## Definition

We will consider complex vector spaces but let us start with a bit of generality so that we can compare them to more familiar real vector spaces. Consider $\mathbb{F} = \mathbb{R}$ or $\mathbb{C}$. (Actually the following works for many *filds* whjich includes the rational numbers, integers modulo $p$, and so forth). A *vector space over* $\mathbb{F}$ also called "real" and "complex" vector spaces for $F = \mathbb{R},\mathbb{C}$ respectively, is a set $V$ of elements $\ket{v}$ with the following properties:

1. **Vector addition**. For all $\ket{v},\ket{w}\in V$ there is a notion of addition $\ket{v} +  \ket{w} \in V$ wuth the following properties:
  - Addition is *commutative*: $\ket{v} + \ket{w} = \ket{w} + \ket{v}$.
  - Addition is *associative. If there is a third vector $\ket{y} \in V$,

```{math}
:label: add_assoc
(\ket{v} + \ket{w}) + \ket{y} = \ket{v} + (\ket{w} + \ket{y})
```

  - a zero vector $\ket{0}\in V$ exists such that $\ket{v} + \ket{0} = \ket{v}$.
  
2. **Scalar multiplication**. For all $a \in \mathbb{F}$, $\ket{v} \in V$, there is a notion of scalar multiplication such that $a\ket{v} \in V$ with the following properties:
  - Multiplication is *associative*: For all $b \in \mathbb{F}$, $a(b\ket{v}) = (ab)\ket{v}$, where $ab$ is the standard mjultiplication of numbers in $\mathbb{F}$.
  - $1\ket{v} = \ket{v}$.
  - $0 \ket{v} = \ket{0}$.
  
3. Distributive properties
- For all $a\in \mathbb{F}$, $\ket{v},\ket{w} \in V$,
```{math}
:label: distributive_mult
a\left(\ket{v} + \ket{w}\right) = a \ket{v} + b \ket{w}
```
- for all $a,b \in \mathbb{F}$, $\ket{v} \in V$,
```{math}
:label: distributive_add
(a + b)\ket{v} = a\ket{v} + b \ket{v}
```

From these rules we can also deduce the existence of an *additive inverse*: for enery $\ket{v} \in V$, there exists a vector $\ket{-v} \in V$ such that $\ket{v} + \ket{-v} = \ket{0}$. This can be seen bu construction: set $\ket{-v} = (-1) \ket{v}$. Then
```{math}
:label: additive_inverse
\ket{v} + \ket{-v} = \ket{v} + (-1) \ket{v} = (1 + (-1) \ket{v} = 0 \ket{v} = \ket{0}
```

Note that I have not yet introduced any notion ofthe length of a vector, whetehr two vectors are orthogonal, and so on. As we will see, this requires som eadditional structure.

## Examples

Theer are a number of more and less familiar examples.

1. $\mathbb{C}^n$, the space of $n$-component column vectors
```{math}
\ket{v} = \begin{pmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{pmatrix}
```
with $c_k \in \mathbb{C}$. We define vector addition and scalar multiplication in the usual way:

```{math}
:label: cn_addition
\begin{pmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{pmatrix} + \begin{pmatrix} d_1 \\ d_2 \\ \vdots \\ d_n \end{pmatrix} = \begin{pmatrix} c_1+ d_1 \\ c_2+d_2 \\ \vdots \\ c_n+d_n \end{pmatrix}
```

```{math}
:label: cn_mult
a \begin{pmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{pmatrix} = \begin{pmatrix} a c_1 \\ a c_2 \\ \vdots \\ a c_n \end{pmatrix}
```
for any $a \in \mathbb{C}$. 

Note we can do ths same with $c_k, d_k \in \mathbb{R}$: then we have a real vector space. Here the zero vector is defined by $c_k = 0$.

2. The space of $n\times n$ complex-valued matrices $M_n(\mathbb{C})$. Addition and scalar multiplication are just matrix addition and scalar miltiplication (for $M \in M_n$, $aM$ is elementwise multiplication by $a$.

3. Degree-$n$ polynomials over $\mathbb{C}$: 
```{math}
:label: degree_n 
\ket{a_0,\ldots a_n} = a_0 + a_1 x + a_2 x^2 + \ldots a_n x^n
```
with addition and scalar multiplication working in the standard way. Note that this is clearly equivalent to $\mathbb{C}^n$. Note also that there is no reason for $n$ to be finite -- we could work with the space of *all* polynomials.

3. Complex functions on an interval: let $x \in [0,1]$. The set of all functions $\psi(x)$ forms a vector space under the standard addition and scalar multiplication of functions if we choose the right boundary conditions. These boundary conditions yield vector spaces:
- Dirichlet $\psi(0) = \psi(1) = 0$.
- Neumann $\psi'(0) = \psi'(1) = 0$
- Periodic $\psi(0) = \psi(1)$ (so $\psi$ is a function on a circle).
However, the boundary condition $\psi(0) = a$, $\psi(1) = b$ for nonzero $a,b \in \mathbb{C}$ is not a vector space under standard addition of functions: the sum of two such functions does not satisfy the required boundary conditions and so is not in $V$.

4. Coplex square-integrable functions on $\mathbb{R}$: that is, functions $\psi(x)$ for $x\in \mathbb{R}$ such that
```{math}
:label: square_int
\int_{-\infty}^{\infty} dx |\psi(x)|^2 < \infty
```

## Subspaces

A set $M \subset V$ is a *vector subspace* if it is a vector space under the same laws for addition and svcalar multiplication. A standard example is any plane through the origin, such as $V = \mathbb{C}^3$, 
```{math}
:label: cthree_subspace
M = \left\{ \begin{pmatrix} c_1 \\ c_2 \\ 0 \end{pmatrix} \forall c_i \in \mathbb{C} \right\}
```

Similarly, any complex line through the origin, defined as the set of vectors 
```{math}
:label: complex_line
a \begin{pmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{pmatrix}
```
for fixed $c_k\in \mathbb{C}^n$ and all $a \in \mathbb{C}^n$. 

A counterexample is any complex line that does not run through the origin, defined as the set of all vectors

```{math}
:label: affine_line
a \begin{pmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{pmatrix} + \begin{pmatrix} d_1 \\ d_2 \\ \vdots \\ d_n \end{pmatrix} 
```

with $c_k,d_k$ fixed and the same for all vectors in this space, and $a$ any complex number. It is clear that the sum of two vectors is a different vector, if there is at least one $d_k \neq 0$.

## Linear independence

**Definition**. A set of vectors $\ket{v_1},\ldots,\ket{v_m} \in V$ is *linearly independent* if
```{math}
:label: lin_indep_def
\sum_{i = 1}^m a_k \ket{v_k} = 0 \Leftrightarrow a_k = 0 \forall\ $k = 1,\ldots,n
```

Let us give some examples.

1. $\mathbb{C}^3$. These vectors are linearly independent:
```{math}
\begin{pmatrix} 1 \\ 0 \\ 0 \end{pmatrix}\ ; \ \ \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}\ ; \ \ \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
```

Similarly these ar elinearly independent:

```{math}
\begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}\ ; \ \ \begin{pmatrix} 0 \\ 1 \\ 1 \end{pmatrix}\ ; \ \ \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
```

However, these three are not:

```{math}
\begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}\ ; \ \ \begin{pmatrix} 0 \\ 1 \\ 1 \end{pmatrix}\ ; \ \begin{pmatrix} 1/2 \\ 1/2 \\ 1 \end{pmatrix}
```

as we can see because 

```{math}
\begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix} + \begin{pmatrix} 0 \\ 1 \\ 1 \end{pmatrix} - 2 \begin{pmatrix} 1/2 \\ 1/2 \\ 1 \end{pmatrix} = 0
```

2. In the space of functions on the interval $[0,1]$ satisfying periodic boundary conditions, the vectors
```{math}
\ket{n} = \sin\left(\frac{n\pi x}{L}\right)
```
are linearly independent. Similarly, for $n$th order polynomials, the monomials $\ket{k} = x^k$ are a subspace of the space of $n$th order polynomials.

### Dimension of a vector space

**Definition**: the *dimension* of a vector space $V$ is the maximum number of linearly independent vectors in $V$. Any such maximal collection is called a *basis*. 

**Theorem**: Given a basis $\ket{k}$, $k = 1,\ldots,n$, then for any vector $\ket{v}$ there is a unique set of complex numbers $a_{k - 1,\ldots,n$ such that
```{math}
:label: use_of_basis
\sum_{k = 1}^n a_k \ket{k} 
```

*Proof*. Assume the contrary, that
```{math}
:label: basis_contrary
\ket{v} = \sum_{k = 1}^n a_k \ket{k} = \sum_{k = 1}^n b_k \ket{k}
```
for $a_k,b_k \in \mathbb{C}$ different numbers. The point is that if this is true,
```{math}
:label: add_fakes
\ket{0} = \ket{v} - \ket{v} = \sum_{k = 1}^n a_k \ket{k} - \sum_{k = 1}^n b_k \ket{k} = \sum_{k = 1}^n (a_k + b_k)\ket{k}
```
but this cannot be zero of $a_k,b_k$ differ in any way, so we have a contradiction to our supposition.
