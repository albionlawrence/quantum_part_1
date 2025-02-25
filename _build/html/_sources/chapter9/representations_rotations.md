# Representations of the rotation group

## General structure

We will find that the commutation relations of *infinitesimal* operators put strong constraints o n the irreducible representations of the rotation group. The basic strategy is somewhat analogous to that we used to solve for the simple harmonic oscillator. 

Recall that for infinitesimal rotations by angle $\theta$ about an axis described by unit vector ${\hat n}$, $R \sim \delta - i \theta \frac{{\vec J}\cdot{\hat n}}{\hbar}$; the commutation relations of $J$ are: $[J_I, J_J] = i\hbar \epsilon_{IJK} J^K$. 

In a unitary representation, $U(R) \sim {\bf 1} - i \theta \frac{{\hat J}^I {\hat n}_I}{\hbar}$ where ${\hat J}$ is a Hermitian operator. As we have shown, the commutation relations of infinitesimal operators determine the structure of non-Abelian multiplication for any group elements (which can be built from successive infinitesimal rotations). Therefore ${\hat J}^I$ must satisfy the same algebra as the matrices we constructed above: $[{\hat J}_I, {\hat J}_J] = i \hbar \epsilon_{IJK} {\hat J}^K$. Following the discussion in the previous section, the action of a finite rotation by angle $\theta$ about an axis ${\hat n}$ is then:
```{math}
U(R(\theta,{\hat n})) = e^{- i \theta {\hat n}\cdot{\hat{\vec J}}/\hbar}
```


We start by finding a set of commuting Hermitian operators built from ${\hat{\vec J}}$. These can be mutually diagonalizable. First, you can show that ${\vec J}^2$ commutes with all of ${\hat J}_I$. You can show this by brute force. You can also note that ${\vec J}$ generates infinitesimal rotations; but ${\vec J}^2$ is the square of a vector and isn't exopected to change under rotations. In saying this I am sweeping a lot under the rug -- what is a vector operator and how does it transform?. 

Since ${\vec J}^2$ commutes with $J_I$ for all $I$, the eigenvalue for ${\vec J}^2$ is invariant under rotations. Since the definition of an irreducible representation is that the only subspace which is invariant under rotations is the whole vector space, an irrep must have a fixed value of ${\vec J}^2$.

By tradition we also pick the operator ${\hat J}_z$ and mutually diagonalize ${\vec J}^2$, $J_z$. That is the irrep should have an orthornormal basis $\ket{\alpha,\beta}$ such that ${\vec J}^2\ket{\alpha,\beta} = \alpha \ket{\alpha,\beta}$ and ${\hat J}_z\ket{\alpha,\beta} = \beta\ket{\alpha,\beta}$. 

Next, we construct the operators
```{math}
J_{\pm} = J_x \pm i J_y = J_{\mp}^{\dagger}
```
These satisfy the commutation relations:
```{math}
\begin{align}
[J_z, J_{\pm}] & = \pm \hbar J_{\pm} \\
[J_+,J_-] & = 2\hbar J_z\\
[J_{\pm}, {\vec J}^2] & = 0
\end{align}
```

First, we can show that $\alpha \geq \beta^2$. This is based on the relations:
```{math}
{\vec J}^2 - J_z^2 = J_x^2 J_y^2 = J_+ J_- + J_- J_+
```
Thus
```{math}
\begin{align}
\alpha - \beta^2 & = \bra{\alpha,\beta} ({\vec J}^2 - J_z^2) \ket{\alpha,\beta}\\
& = \bra{\alpha,\beta} (J_+ J_- + J_- J_+)  \ket{\alpha,\beta}\\
& = ||J_- \ket{\alpha,\beta}||^2 + || J_+ \ket{\alpha,\beta}||^2 \geq 0
\end{align}
```


Next, from the commutation relations for $J_{\pm}, J_z$, we find
```{math}
	J_{\pm}\ket{\alpha,\beta} = C_{\pm} \ket{\alpha,\beta \pm \hbar}
```
where $C_{\pm} \in \CC$ is a constant. Given this, $\beta$ will have a maximum $\beta_{max}^2 \leq \alpha$ and a minimum $\beta_{min}^2 \leq \alpha$ such that 
```{math}
\begin{align}
J_+ \ket{\alpha,\beta_{max}} & = 0\\
J_-\ket{\alpha,\beta_{min}} & = 0
\end{align}
```
Now, we can use the commutation relations to find:
```{math}
J_{\pm} J_{\mp} = J_x^2 + J_y^2 \mp [J_x,J_y] = {\vec J}^2 - J_z^2 \pm \hbar J_z
```
Therefore:
```{math}
:label: highest_weights
\begin{align}
J_+ J_- \ket{\alpha,\beta_{min}} & = 0 = \alpha - \beta_{min}^2 + \hbar \beta_{min}\\
J_- J_+ \ket{\alpha,\beta_{max}} & = 0 = \alpha - \beta_{max}^2 - \hbar \beta_{max}
\end{align}
```
Solving the resulting quadratic equation for $\beta_{max}$ we find
```{math}
\beta_{max} = \frac{- \hbar \pm \sqrt{\hbar^2 + \alpha}}{2}
```
The constraint $\alpha \geq \beta_{max}^2$ menas that we must choose the positive branch. Similarly, we can show that 
```{math}
\beta_{min} = \frac{\hbar - \sqrt{\hbar^2 + 4\alpha}}{2} = - \beta_{max}
```

Now if we start with $\ket{\alpha,\beta_{min}}$ and act on it with $J_+^n$ there is some minimum $n$ for which $J_+^{n + 1} \ket{\alpha,\beta_{min}} = 0$. This means that
```{math}
J_+^n \ket{\alpha,\beta_{min}} \propto \ket{\alpha, \beta_{max}}
```
For this to hold, we must have 
```{math}
	\beta_{\max} = n \hbar + \beta_{min} = n\hbar - \beta_{max} \Rightarrow \beta_{max} = \frac{n \hbar}{2}
```
where $n\in \CZ, n \geq 0$. If we define $j = \frac{n}{2} \geq 0$, $\beta_{max} = \hbar j$, the second equation in {eq}`highest_weights` becomes $\alpha = \hbar^2 j(j+1)$. We then have $\beta = m \hbar$, with $m \in (-j, -j + 1, \ldots, j - 1, j)$. From here on out we denote the states $\ket{\alpha,\beta}$ as $\ket{j,m}$, with $\alpha = \hbar^2 j(j+1)$, and $\beta = \hbar m$.

Now, any rotation can be written in terms of infinitesimal rotations using $J_{x,y,z}$. Since $J_{x,y}$ can be written as linear combinations of $J_{\pm}$, we can describe rotations via actions of $J_z$, $J_{\pm}$. These change the values of $m$ by integers, and do not change $j$. Thus, we can write $(2 j + 1)$ states $\ket{j,m}$ as a complete, orthonogonal basis for an irreducible representation of $SO(3)$/$SU(2)$. We can normalize them so that they are an orthonormal basis.

Thus, for any $j \in \half \CZ$, there is a $(2 j + 1)$-dimensional irreducible representation labeled by $j$. These are spanned by the orthonormal basis $\ket{j,m}$ such that
```{math}
\brket{j,m}{j,m'} = \delta_{m,m'}
```
They are eigenstates of $J_z$ with eigenvalues $m\hbar$.

We can furthermore find the matrix elements of $J_{\pm}$. Using $J_+ = J_-^{\dagger}$, we compute
```{math}
\begin{align}
\bra{j,m}J_- J_+ \ket{j,m} & = \bra{j,m}({\vec J}^2 - J_z^2 - \hbar J_z)\ket{j,m}\\
& = \hbar^2(j-m)(j+m+1)
\end{align}
```
Thus, after changing the normalization of $\ket{j,m}$ by a phase, we can write
```{math}
J_+ \ket{j,m} = \hbar\sqrt{(j-m)(j+m+1)}\ket{j,m+1}
```
A similar argument yields:
```{math}
J_-\ket{j,m} = \hbar\sqrt{(j+m)(j-m+1)} \ket{j,m-1}
```

We denote these $(2j + 1)$-dimensional representations as $D_j$. These are sometimes called "spin-j representations".

Now not all of these representations are in fact representations of $SO(3)$, To see this, consider the fact that rotations by $2\pi$ abuot any axis should be the identity in $SO(3)$. COnsider rotations about ${\hat z}$. The correesponding operator is $U(2\pi) = e^{2\pi i J_z/\hbar}$. 

Now, acting on $\ket{j,m}$, we have $U(2\pi) \ket{j,m} = e^{-2\pi i m}$. If $m$ is an integer this is unity; if $m$ is half-integer, this is $-\ket{j,m}$. Since the ideneity element of the group should map to the identity operator in the representation of the rotation group, irreps with $j = \CZ + \half$ cannot be irreps of $SO(3)$. Thus the full set of irreps of $SO(3)$ are $D_{j \in \CZ}$. 

Hoever, $D_j$ are irreps of $SU(2)$ for *all* $j$.

We call all $D_j$ irreducible representations of the rotation group, even for an odd half-integer. As we will see there are particles which carry intrinsic angular momentum $j = \half$ or other half integers. Rotations act on the spin degrees of freedom.

Another more advanced point is that the rotations are part of the full set fo Lorentz transformations; starting from the full group of Lorentz transformations, rotations emerge as actions of $SU(2)$.

