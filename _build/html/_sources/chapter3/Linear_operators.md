
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

3. Let $V$ be a vector space over $\CF$. A **linear operator** *f* is a linear map $F: V \to V$. 

For $\CF = \CC$, an **antilinear operator** *g* is an antilinear map $g: V \to V$. 

Antilinear operators include the operator that implements time reversal, which is important in various condensed matter physics and particle physics contexts.

Abstractly we usually denote operators by capital letters $A$ and the action of operators as $A: \ket{V} \to A\ket{v}$.

### Examples

1. The identity operator ${\bf 1}\ket{v} = \ket{v} \forall \ket{v}$. 

2. The zero operator $\varnothing: \ket{V} \to \ket{0}$.

3. More generally, scalar multiplication by any scalar in $\CF$ is a linear operator.

4. For $C = \CC^n$, $n \times n$ matrices acting on column vectors by the usual rules of matrix multiplication are all linear operators. In fact one can represent any finite-dimensional vector space of dimension $n$ by $\CC^n$, and every operator as a matrix acting on $\CC^n$.

5. A more interesting example: consider the (infinite-dimensional) space of all polynomials. We can represent these as 
```{math}
\ket{a_0,a_1,a_2,\ldots} = \sum_{k = 0}^{\infty} a_k x^k
```
The following operators
- shifts or multiplication by $x$

```{math}
S\ket{a_0,a_1,\ldots} = \ket{0,a_0,a_1,\ldots} = \sum_{k = 0}^{\infty} a_k x^{k+1} = x \sum_{k = 0}^{\infty} a_k x^{k}
```

- derivatives with repect to $x$

```{math}
T \ket{a_0,a_1,\ldots} = \ket{a_1,2 a_2,3 a_3,\ldots} = \sum_{k = 1}^{\infty}k_{k-1} k x^k = \frac{d}{dx} \sum_{k = 0}^{\infty} a_k x^k
```

are linear operators on $V$.

6. As a next step, consider the vector space of swuare-integrable complex functions. You can convince yourself that multiplication by $x$ and differentiation are linear operators. There are some subtleties here; it can be that these take the function out of the Hilbert space (eg multiplication can, if $f$ falls off as $1/|x|$ at infinity).

## Operator algebras

In general we can combine operators to form new linear operator in various ways: technically, they define an *algebra:

1. Operators can be added: for operators $A_1,A_2$ acting on a vector space $V$, we can define
```{math}
:label: add_ops
(a A_1 + b A_2)\ket{v} \equiv a (A_1 \ket{v}) + b (A_2 \ket{v})
```
for any $\ket{v} \in V$, and $a,b \in \CF$.

It is straightforward to see that $(a A_1 + b A_2)$ is thus a linear operator, Note that $A + \varnothing = A$ under this rule, $A_1 + A_2 = A_2 + A_1$, and if $a = 0$, $a A = \varnothing$.

2. We can also multiply operators. For any two linear operators $A_1,A_2$, we define
```{math}
:label: op_mult
(A_1 A_2)\ket{v} = A_1(A_2\ket{v})
```
With a little work you can show that $A_1 A_2$ is a linear operator. Note that if $\bf{1}$ is the identity operator, $\bf{1} A = A \bf{1} = A$. Multiplication is *associative*: that is, if $A_3$ is also a linear operator, $((A_1 A_2) A_3) = (A_1(A_2 A_3))$. However, it does not have to be commutative. For example, for $V = \CC^n$ with operators equal to $n\times n$ matrices, operator multiplication is just matrix multiplication which is certainly not commutative. Consider $V = \CC^2$, and operators
```{math}
	A_1 = \begin{pmatrix} 0 & 1 \\ 1 & 0\end{pmatrix}\ ; \ \ A_2 = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
```
then operator multiplication is simply matrix multiplication which we know is not commutative. In part
```{math}
A_1 A_2 = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}\ ; \ \ A_2 A_1 = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix} = - A_1 A_2 \neq A_1 A_2
```

In general we measure the lack of commutativity with the *commutator*:
```{math}
:label: commutator
[A_1,A_2] = A_1 A_2 - A_2 A_1
```
Note that the commutator is itself a linear operator.

## Kernel, range, and inverse

### Kernel of an operator

1. **Definition**: Consider a vector space $V$ and a linear operator $A$ acting on it. The *kernel$ of $A$ is defined as
```{math}
:label: kernel
\text{Ker}(A) = \left\{ \ket{v}\in V | A\ket{v} = \ket{0} \right\}
```
As an example, consider $V = \CC^4$, and the operator
```{math}
A = \begin{pmatrix} a & 0 & 0 & b \\ c & 0 & 0 & d \\ e & 0 & 0 & f \\ g & 0 & 0 & h\end{pmatrix{
```
for $a,\ldots h \in \CC$. With a little work you can show that
```{matrix}
\text{Ker}(A) = \left\{ \begin{pmatrix} 0 \\ c_1 \\ c_2 \\ 0 \end{pmatrix} \forall c_{1,2} \in \CC \right\}
```

Note that this is a vector subspace of $\CC^4$. This is no accident, as we can prove:

2. **Theorem**. For any vector space $V$ and linear operator $A$ acting on it, $\text{Ker}(A)$ is a vector subspace of $V$. (The proof in your problem set for the week).

3. **Definition**. A linear operator $A$ acting on a vector space $V$ is *injectove* or *one-to-one* if
```{math}
:label: injective
A\ket{v} = A\ket{w} \Rightarrow \ket{v} = \ket{w}
```

![injective map](injective.png)

4. **Theorem**. A linear operator $A$ is injective if and only if $\text{Ker}(A) = 0$.
