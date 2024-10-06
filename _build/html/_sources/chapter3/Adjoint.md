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

Let $V$ be a vector space over $\CC$. An *adjoint map* is a map $A: V \to V^*$, which we denote by $A\ket{v} \equiv \bra{f_v}$ with the properties

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
