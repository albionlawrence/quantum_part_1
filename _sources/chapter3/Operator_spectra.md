# Spectra of Hermitian and Unitary Operators

The following is *central* to the workings of quantum mechanics.

## Eigenvalues and eigenvectors for Hermitian operators

Consider a Hermitian operator $A = A^{\dagger}$.

1. ***Theorem**. The eigenvalues of $A$ are real.

**Proof**. Consider a normalized eigenvector $\ket{a}$ (||a|| = 1$) such that $A \ket{a} = a \ket{a}$. This means that $\bra{a} A \ket{a} = a$. By the skew-symmetry of the adjoint, 
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

- If there are $d_k$ identical eigenvalues, one needs to show (and I will not) that this means the space of vectors which are eigenvectors of $A$ with eignevalue $a_k$ form a $d_k$-dimensional subspace. This can mbe made into an orthonormal basis via teh Gram-Schmidt machine.

