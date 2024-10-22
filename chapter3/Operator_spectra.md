# Spectra of Hermitian and Unitary Operators

The following is *central* to the workings of quantum mechanics.

## Eigenvalues and eigenvectors for Hermitian operators

Consider a Hermitian operator $A = A^{\dagger}$.

1. **Theorem**. The eigenvalues of $A$ are real.

**Proof**. Consider a normalized eigenvector $\ket{a}$ ($||a|| = 1$) such that $A \ket{a} = a \ket{a}$. This means that $\bra{a} A \ket{a} = a$. By the skew-symmetry of the adjoint, 
```{math}
a^* = \bra{a} A \ket{a}^* = \bra{a} A^{\dagger} \ket{a} = \bra{a} A \ket{a} = a
```

2. **Theorem**. Eigenvectors of $A = A^{\dagger}$ with *distinct* eigenvalues are orthogonal

**Proof** Consider eigenvectors $\ket{a}, \ket{b}$ such that
```{math}
A\ket{a} = a \ket{a}\ ; \ \ A \ket{b} = b \ket{b} 
```
Then 
```{math}
\bra{b} A \ket{a} = \brket{b}{a} a = b \brket{b}{a}
```
for $a \neq b$ this is only possible if $\brket{b}{a} = 0$. 

3. **Theorem**. The eigenvectors of $A = A^{\dagger}$ can be constructed to form an orthonormal basis $\ket{a_i}$ such that $A\ket{a_i} = a_i \ket{a_i}$. 

I will only sketch a proof.

- The eigenvalues satisfy $\text{det}(A - a {\bf 1}) = 0$ is a $D$th-order polynomial equation in $a$ (where $d = \text{dim}(V)$). Thus
```{math}
\text{det}(A - a {\bf 1}) = c \prod_{I = 1}^d (a - a_i)
```
There are always $d$ complex roots to this equation. If $A = A^{\dagger}$ all eigenbvalues are real so all $a_i$ are real. There are still $d$ roots.
Hhere $a_i$ are the eigenvalues. If $a_i \neq a_j$ for $i \neq j$, we are done, as $\brket{a_i}{a_j} = \delta_{ij}$ and there are $d$ such eigenvectors.

- If there are $d_k$ identical eigenvalues, one needs to show (and I will not) that this means the space of vectors which are eigenvectors of $A$ with eigenvalue $a_k$ form a $d_k$-dimensional subspace. This can be made into an orthonormal basis via teh Gram-Schmidt machine.

4. **Theorem**. For any Hermitian operator $A$, there exists a unitary matrix $U$ and a diagonal matrix $\Lambda$ such that $A = U^{\dagger} \Lambda U$, and the entries of $\Lambda$ are the eigenvalues, such than an eigenvalue $a_k$ with degree of degeneracy $d_k$ appears in $d_k$ entries.

**Proof** (sketch). Given an orthonormal basis $\ket{i}$, $A_{ij} = \bra{i} A \ket{j}$. On the other hand there is an orthonormal basis of eigenvectors $\ket{a_k,\alpha_k}$, where $A \ket{a_k,\alpha_k} = a_k \ket{a_k,\alpha_k}$, $\alpha_k = 1,\ldots,d_k$, and $\brket{a_k,\alpha_k}{a_{\ell},\beta_{\ell}} = \delta_{kl} \delta_{\alpha_k,\beta_{\ell}$. Let us relabel $(a_k,\alpha_k) \to {\tilde a}$. Then $\bra{\tilde a} A \ket{\tilde b} = \Lambda_{{\tilde a}{\tilde b}}$, where $\Lambda$ is diagonal with the entries equal to the eigenvalues in the way described. Now using ${\bf 1} = \sum_{{\tilde a}} \ket{{\tilde a}}\bra{{\tilde a}}$, we can write
```{math}
A_{ij} = \sum_{{\tilde a},{\tilde b}} \brket{i}{\tilde a}\bra{\tilde a} A \ket{\tilde b} \brket{\tilde b}{j} = U^{\dagger}_{i{\tilde a}} \Lambda_{{\tilde a}{\tilde b}} U_{{\tilde b} j}
```
where $U_{{\tilde a}i} = \brket{{\tilde a}}{i}$, and $U^{\dagger}_{j{\tilde a}} = \brket{j}{{\tilde a}}$. You can convince yourselves that these are Hermitian conjugates of each other. We have already shown in {ref}`changes_of_basis` that these are inverses of each other, so $U$ is a unitary matrix and the statement holds. 

For those familiar with the singular value decomposition of matrices, this is of course a special case.

The next theorem will be central to the uncertainty principle.

5. **Theorem**. Two Hermitian operators $A,B$ are diagonal in the same orthonormal basis if and only if $[A,B] = 0$. 

**Proof (partial)**. For the "only if" part, if $A,B$ are diagonal in the same basis, we use the fact that we can writ $A = U^{\dagger} \Lambda_A U$, $B = U^{\dagger} \Lambda_B U$, following the construction above. $A,B$ are diagonalized by teh same unitary matrix because this matrix implements the change of basis and by supposition the basis of eigenvectors is the same. Then since diagonal matrices commute,
```{math}
AB = U^{\dagger} \Lambda_A U U^{\dagger} \Lambda_B U = U^{\dagger} \Lambda_A \Lambda_B U = U^{\dagger} \Lambda_B \lambda_A U = U^{\dagger}\Lambda_B U U^{\dagger}\Lambda_A U = BA
```

For the "if" part, let $A,B$ commute. We take the case that the eigenvalues of $A,B$ are distinct (see for example {cite:p}`bellac2006quantum`). Then if $A \ket{a_i} = a_i \ket{a_i}$, $A(B \ket{a_i}) = BA \ket{a_i} = a_i B \ket{a_i}$. That is, $B\ket{a_i}$ is an eigenvector of $A$. But by supposition the subspace of eigenvectors with a fixed eigenvalue is one-dimensional, $B\ket{a_i} = b_i \ket{a_i}$ for some $b_i$ which is clearly an eigenvalue of $b_i$. 

## Unitary operators

**Theorem** For any unitary operator $U$ we can write $U = V^{\dagger}\Lambda V$ where $V$ is a unitary matrix, and $\Lambda$ diagonal with enries of the form $e^{i\lambda}$, $\lambda \in \CR$.

## Operators on the space of functions

For functions with periodic boundary conditions, the functions $\psi_n(x) = \frac{1}{\sqrt{L}} e^{2\pi i n x/L}$, $n \in \CZ$ are a basis (since Fourier modes are a basis of periodic functions. In this case, ${\hat p} \psi_n = \frac{2\pi \hbar n}{L} \psi_n$; this basis is a basis of eigenfunctions of ${\hat p}$. Note that ${\hat x}:\psi(x) \to x\psi(x)$ is not an operator in this space.

For $L^2(\CR)$, ${\hat x}$ is almost such an operator, if we focus on $\psi(x)$ falling off fast enough (faster than $\frac{1}{|x|^{3/2}}$). The fact that it fails in some cases means that ${\hat x}$ is not a *bounded* operator. One can also show the same for the momentum operator ${\hat p} = \frac{\hbar}{i} \frac{\del}{\del x}$. Nonetheless, these operators are useful and we will use them. I will table a discussion of them for a week or two, when we get to wave mechanics.

## Projection operators and spectral representations

### Projection operators

1. **Definition**. Let $V$ be a vector space over $\CC$ and $W_{1,2} \subset V$ be vector subspaces of $V$. $W_1$, $W_2$ are *orthogonal* (denoted $W_1 \perp W_2$) if $\forall \ket{w_1} \in W_1, \ket{w_2} \in W_2$, $\brket{w_1}{w_2} = 0$.

2. **Theorem**. $\forall W ]subset V$ vector subspaces, there exists a subspace $W^{\perp} \subset V$ such that $\forall \ket{v} \in V$, there exists a unique expression
```{math}
:label: ortho_decomp
\ket{v} = \ket{w} + \ket{w^{\perp}}
```
with $\ket{w} \in W$, $
\ket{w^{\perp}} \in W^{\perp}$. This is known as an *orthogonal decomposition* of $\ket{v}$.  I will forgo a proof here.

Note that we can form orthogonal/orthonormal bases $\ket{i}, \ket{I}$ for $W,W^{\perp}$ respectively; by teh above theorem, since any vector can be written as a sum of vectors in the wubspaces $W,W^{\perp}$, the collection of basis elemenbts $\ket{i},\ket{I}$ are a basis for $V$. Thus if $d = \text{dim} V$, $d_W = \text{dim}(W)$, $d_{W^{\perp}} = \text{dim}(W^{\perp})$, we have
```{math}
:label: od_dims
d = d_W + d_{W^{\perp}}
```

3. **Definition**. A *projection operator* $\CP$ is a Hermitian operator such that $\CP^2 = \CP$. The reasons for calling this a projection operator will become clear as we explore its properties.

- The eigenvalues of $\CP$ are either 1 or 0. Given an eigenvector $\ket{a}$ with $\CP\ket{a} = a \ket{a}$, we can apply $\CP$ to both sides to find
```{math}
\CP^2 \ket{a} = \CP a \ket{a} \Rightarrow \CP \ket{a} = a^2 \ket{a} \Rightarrow a^2 = a
```
The only solutions are $a = 1$ or $a = 0$.

- **Theorem**. Eigenvectors with zero eigenvalue span $\text{Ker}(\CP)$. (Stated without proof).

- ${\bf 1} - \CP$ is also a projection operator. 

- **Theorem**. Eigenvectors with unit eigenvalue span $(\text{Ker}(\CP))^{\perp}= \text{Ker}({\bf 1} - \CP)$ which is also the range of $\CP$

- In an orthonormal basis of eigenvectors of $\CP$, we can write a matrix representation of $\CP$ as:
```{math}
\CP = \begin{pmatrix} {\bf 1}_{d_P\times d_P} & {\bf 0}_{d_P \times d_{P^{\perp}}} \\ {\bf 0}_{d_{P^{\perp}}\times d_{P^{\perp}}} & {\bf 0}_{d_{P^{\perp}} \times d_{P^{\perp}}}
\end{pmatrix}
```
where $\text{dim}(\text{range}(\CP)) = d_P$ and $\text{dim}(\text{Ker}(\CP)) = d_{P^{\perp}}$. If the eigenvectors of $\CP$ with unit eigenvalues are $\ket{i}$, $i \in \{1, \ldots , d_P\}$, then we can also write
```{math}
:label: abstract_proj_rep
\CP = \sum_{i = 1}^{d_P} \ket{i}\bra{i}
```
In the latter case, we can show this is Hermitian by first realizing that
```{math}
:label: adjoint_vectorrep
\left(\ket{\chi}\bra{\psi}\right)^{\dagger} = \ket{\psi}\bra{\chi}
```
(can you shouw this?), and then showing that
```{math}
:label: projection_squared
\CP^2 = \sum_i \ket{i}\bra{i} \sum_j \ket{j}\bra{j} = \sum_{i,j} \ket{i}\brket{i}{j}\bra{j} = \sum_{i,j} \ket{i}\delta_{ij} \bra{j} = \CP
```

### Spectral representation of Hermitian operators

Consider a vector space $V$ and a Hermitian operator $A: V\to V$ with a basis of eigenstates $\ket{a_i,\alpha_i}$, where $A\ket{a_i,\alpha_i} = a_i \ket{a_i,\alpha_i}$, $\alpha_i \in \{1,\ldots,d_i\}$, and $\brket{a_i,\alpha_i}{a_j,\alpha_j} = \delta_{ij}\delta_{\alpha_i,\alpha_j}$. Here if $d_i > 1$ then $a_i$ is a degenerate eigenvalue and $d_i$ is the degree of degeneracy. We can write a projection operator 
```{math}
\CP_i = \sum_{\alpha_i = 1}^{d_i} \ket{a_i,\alpha_i}\bra{a_i,\alpha_i}
```
which projects onto the subspace $V_i \subset V$ of vectors with eigenvalue $a_i$. We can then write the operator $A$ as
```{math}
:label: spectral_rep 
A = \sum_i a_i \CP_i
```
The right hand side has the same eigenvalues and eigenvector as $A$, by construction; thus it has the same matrix elements in a basis of eigenvectors of $A$, and so must be the same operator as $A$.

Note that the fact that $\ket{a_i,\alpha_i}$ are a complete orthonormal basis for $V$ means that
```{math}
:label: evector_resolution_identity
{\bf 1} = \sum_{i,\alpha_i} \ket{a_i,\alpha_i}\bra{a_i,\alpha_i} = \sum_i \CP_i
```


