# Adjoints and inner products

## Dual vector spaces

### Definition

Let $V$ be a vector space over $\CC$. the *dual vector space* $V^*$ is the space of all linear maps $f:V \to \CC$.

### Properties and notation

1. $V^*$ is a vector space.

Consider linear maps $f_{1,2}$, and $a,b \in \CC$. Then we can define a linear map $a f_1 * b f_2$ by their action on a vector $\ket{v}$. 

```{math}
:label: sum_of_linear
(a f_1 + b f_2)(\ket{v}) = a f_1(\ket{v}) + b f_2(\ket{v})
```

One can show that this defines a linear map: for any $c,d\in \CC$ and $\ket{v_{1,2}} \in V$,
```{math}
(a f_1 + b f_2)(c \ket{v_1} + d \ket{v_2}) = c (a f_1 + b f_2)\ket{v_1} + d (a f_1 + b f_2)(\ket{v_2})
```
which follows from $f_{1,2}$ being linear maps/

2. $\text{dim}(V^*) = \text{dim}(V)$. It is instructive to show this. Consider a basis $\ket{i}$ of $V$, $i = 1,\ldots d = \text{dim}(V)$. A general vector $\ket{v}$ can be expressed as 
```{math}
\ket{v} = \sum_{i = 1}^d c_i \ket{i}
```
for a unique set of coefficients $c_i \in \CC$. Now 
```{math}
f(\ket{v}) = \sum_{i = 1}^d c_c f(\ket{i})
```
Thus, the map $f$ is completely specified by $d$ complex numbers $f(\ket{i}) = c_i \in CC$. Thus, if we define $f_i$ by $f_i(\ket{j}) = \delta_{ij}$, we can show that each $f_i$ is a linear map. Furthermore, $f_i$ is linearly independent of $f_{j \neq i}$ (you should convince yourself of this). 

Any function $f$ can always be written as $f = \sum_{i = 1}^d c_i f_i$, so this basis is maximal, and $f_i$ form a complete basis for $V^*$. There are $d$ such independent basis functions, so $\text{dim}(V^*) = d$. 

3. *Notation*. We can express $f \in V^*$ as a "bra vector" $\bra{f}$. We then call elements $\ket{v} \in V$ "ket vectors". We can then write
```{math}
\brket{f}{v} \equiv f(\ket{v})
```
as a "bra(c)ket". I didn't do this, please blame Dirac. Anyhow the notation is unfortunately standard. With this notation we can define the linear structure of $V^*$ as
```{math}
\bra{a f_1 + b f_2} = a \bra{f_1} + b \bra{f_2}
```

4. Finally, The dual vector space for $V^*$ is $V$, or $(V^*)^* = V$: for any $\ket{v}$ the map from $V^* \to \CC$ is just $\ket{v}: f \to \brket{f}{v}$.

### Example

If $V = \CC^3$ is represented as the space of column vectors. we can represent $V^*$ as the set of row vectors. That is, consider a basis
```{math}
\ket{1} = \begin{pmatrix}1 \\ 0 \\ 0 \end{pmatrix}\ ; \ket{2} = \begin{pmatrix}0 \\ 1 \\ 0 \end{pmatrix}\ ; \ket{3} = \begin{pmatrix}0 \\ 0 \\ 1 \end{pmatrix}
```
We can define any linear map $f$ by $f(\ket{i} = c_i$. Then if $\ket{v} = \sum_i a_i \ket{i}$, 
```{math}
f(\ket{v}) = \sum_i c_i a_i = \begin{pmatrix} c_1 & c_2 & c_3 \end{pmatrix} \begin{pmatrix} a_1 \\ a_2 \\ a_3 \end{pmatrix}
```

## Adjoint maps

Since $\dim V = \dim V^*$, we expect that there is an isomorphism (a map that is one-to-one and onto) between them. Choosing such a map leads to a choice of "inner product" on $V$ itself: a way of assigning to $\ket{v}$ a number corresponding to some notion of its length.

### Definition

Let $V$ be a vector space over $\CC$. An *adjoint map* is a map $\cal{A}: V \to V^*$, which we denote by $A\ket{v} \equiv \bra{f_v}$ with the properties

1. Skew symmetry: $\brket{f_w}{v} = \brket{f_v}{w}^*$.
2. Positive semi-definiteness: 
```{math}
\brket{f_v}{v} \equiv ||v||^2 \geq 0\ ; ||v|| = 0\ \text{iff}\ \ket{v} = 0
```

In general we write $\bra{f_v} = \bra{v}$. 

### Properties

1. *Antilinearity*. Using skew-symmetry you can show that for $\ket{v_{1,2}} \in V$, $a, b \in \CC$, 
```{math}
\bra{a v_1 + b v_2} = a^* \bra{v_1} + b^* \bra{v_2}
```

2. *Schwarz inequality*
```{math}
|\brket{v}{w}| \leq ||v||\ ||w||
```

3. *Triangle inequality*
```{nath}
||u + v|| \neq ||u| + ||v||
```

### Examples

1. $V = \CC^3$.
```{math}
A\begin{pmatrix} c_1 \\ c_2 \\ c_3 \end{pmatrix} = \begin{pmatrix} c_1^* & c_2^* & c_2^* \end{pmatrix}
```
If 
```{math}
\ket{v} = \begin{pmatrix} c_1 \\ c_2 \\ c_3 \end{pmatrix}\ , \ket{w} = \begin{pmatrix} d_1 \\ d_2 \\ d_3 \end{pmatrix}
```
then
```{math}
\brket{v}{w} = c_1^* d_1 + c_2^* d_2 + c_3^* d_3
```


2. $V = M_2(\CC)$. 
```{math}
\brket{M_1}{M_2} = \text{tr} (M_1^{*})^T M_2) = \sum_{i,j} (M_1)^*_{ij} (M_2)_{ij}
```

### Additional definitions and a comment

1. $\brket{v}{w}$ is the *inner product* of $\ket{v}$, $\ket{w}$.
2. $||v||^2 = \brket{v}{v}$ is called the *norm* of $\ket{v}$.
3. $V$ with an adjoint map is called an *inner product space*.
4. An inner product space (over $\CC$) is called a *Hilbert space* if either:
- $\text{dim}(V) < \infty$, or
- Cauchy sequences in $V$ are complete.

To explain the last possibility, note that $\ket{v_i}$, $i = 1,\ldots,\infty$ is a *Cuachy sequence* if for any $\eps > 0$, there exists some integer $N$ such that 
```{math}
|| v_n - v_m || < \eps\ \forall n, m \geq N
```
Such a sequence is *complete* if it converges to a vector in $V$.

4. There is no unique adjoint map.

### Actions of operators

Goven a linear operator $A$ and $\ket{v} \in V$, $A\ket{v}$ is a vector and $\bra{w} A \ket{v}$ is a complex number. We can therefore define $\bra{A w} \equiv \bra{w} A$ such that $\brket{A w}{v} = \bra{w} A \ket{v}$.

## Orthonormal bases

### Definitions

Let $V$ be a vector space over $\CC$.

1. $\ket{v} \in V$ is a *normal vector* if $||v||^2 = \brket{v}{v} = 1$.

2. $\ket{v},\ket{w} \in V$ are *orthogonal* if $\brket{v}{w} = 0$.

3. An *orthonormal basis* is a basis $\ket{i} \in V$, $i = 1,\ldots,d = \text{dim} V$ such that for $\cal{A}: \ket{i} \to \bra{i}$, \brket{i}{j} = \delta_{ij}$. 

### Examples

1. We can write $\ket{v} = \sum_i v_i \ket{i}$; the antilienarity of the adjoint map means that $\bra{v} = \sum_i \bra{i} v^*_i$. This means that 
```{math}
:label: on_norm
\brket{v}{v} = \sum_{i,j} v^*_i \brket{i}{j} v_j = \sum_i |v_i|^2
```
 Similarly, for $\ket{w} = \sum_i w_i \ket{i}$, 
 ```{math}
 :label: inner_product_on_basis
 \brket{w}{v} = \sum_i w^*_i v_i
 ```
 This works if we idenfity 
 ```{math}
 :label: ket_in_on_basis
 \ket{v} \to \begin{pmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{pmatrix}
 ```
and thus
```{math}
:label: bra_in_on_basis
\bra{v} \to \begin{pmatrix} v_1^* & v_2^* & \ldots & v_n^* \end{pmatrix}
```
The basis element $\ket{i}$ is a column vector with all zeros except a $1$ in the $i$th row.

2. If $V = M_2(\CC)$, the space of $2\times 2$ complex matrices,
a natural inner product is
```{math}
\brket{m}{n} = \text{tr} (m^T)^* n
```
where $m,n$ are $2\times 2$ matrices. This clearly defines an adjoint map from $\ket{n}$ to a linear map. An orthonormal basis is:
```{math}
:label: matrix_on_basis
\ket{1} \to \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} \ ; \ \ 
\ket{2} \to \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}\ ; \ \ 
\ket{3} \to \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}\ ; \ \ 
\ket{4} \to \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}
```

### The Gram-Schmidt machine

**Theorem**: every finite-dimensional vector space has an orthonormal basis.

**Proof (partial)**: Given a basis $\ket{v_1},\ket{v_2},\ldots,\ket{v_d}$, we can construct a basis iteratively. Define
```{math}
:label: gs_machine
\begin{align}
\ket{1} & = \frac{\ket{v_1}}{||v_1||}\\
\ket{2} & = \frac{\ket{v_2} - \brket{1}{v_2}\ket{1}}{\sqrt{||v_2||^2 - |\brket{1}{v_2}|^2}}\\
\ket{k} & = \frac{\ket{v_k} - \sum_{n = 0}^{k-1} \ket{n}\brket{n}{v_k}}{\sqrt{||v_k||^2 = \sum_{n = 1}^{k-1} |\brket{v_k}{n}|^2}}
\end{align}
```

### Matrix elements of operators

Since $\ket{i}$ is a basis, we can write the action of operators in this basis: $A\ket{j} = A_{ij}\ket{i}$. As notation, we will sometimes write
```{math}
:label: operator_rep
A = \ket{i} A_{ij} \ket{j}
```
We understand this to mean
```{math}
A\ket{v} = \sum_{i,j} \ket{i} A_{ij} \brket{j}{v} = \sum_{i,j}A_{ij} v_j \ket{i}
```
where $\ket{v} = \sum_i v_i \ket{i}$, and for dual vectors $\bra{v} = \sum_i \bra{i} v_i^*$,
```{math}
\bra{v} A = \sum_{i,k} \bra{i} v^*_k A_{ki}
```
Thus
```{math}
\bra{v} A \ket{w} = \sum_{i,j} v^*_i A_{ij} w_j
```

A particularly important example is the identity operator $\bf{1}$ for which $\bf{1}_{ij} = \delta_{ij}$. This can be represented as above by:

```{math}
:label: resolution_of_identity
{\bf 1} = \sum_i \ket{i}\bra{i}
```

for any orthonormal basis. This is called a *resolution of the identity*, associated to a given basis.

In this basis, an important operator on $A$ is the *transpose*. That is given a linear operator $A$, we can define the transpose $A^T$ via its matrix elements
```{math}
:label: transpose_def
(A^T)_{ij} = A_{ji}
```
In particular, we can write
```{math}
\bra{v}A = \bra{i} v^*_k A_{ki} = \bra{i} (A^T)_{ik} v^*_k
```

### Adjoints of operators

The vector $A\ket{v} \equiv \ket{Av} = A_{lk} v_k \ket{l}$ has a natural adjoint
```{math}
{\cal A} : A\ket{v} \to \bra{l} v_k^* A_{lk}^* = \bra{l} v_k^* (A^T)^*_{kl} \equiv \bra{v} A^{\dagger}
```
which defines the *Hermitian conjugate* $A^{\dagger}$. We can either define it as ${\cal A}: A\ket{v} \to \bra{a} A^{\dagger}$ or via its matrix elements in an orthonormal basis,
```{math}
:label: hermitian_def
A^{\dagger}_{ij} = (A^T)^*_{ij} = A^*_{ji}
```

### Hermitian and unitary operators

1. **Definition**. A *Hermitian operator* is an opertator $A = A^{\dagger}$.

Note that this does not mean the operator has real matrix elements. The following operator on $\CC^2$ is Hermitian:
```{math}
\sigma_y = \begin{pmatrix} 0 & i \\ -i & 0 \end{pmatrix}
```

2. **Definition**. A *Unitary operator* is an operator $U$ such that $U^{|dagger} = U^{-1}$. 

An important property of this operator is that it is *norm-preserving*:
```{math}
|| U\ket{v}||^2 = \bra{v} U^{\dagger} U \ket{v} = \bra{v} U^{-1} U \ket{v} = \brket{v}{v} = ||v||^2
```

An example of a unitary operator acting on $\CC^2$: 
```{math}
U = \begin{pmatrix} \cos\theta & \sin\theta e^{i\phi} \\ - \sin\theta e^{-i\phi} & \cos\theta \end{pmatrix}
```

