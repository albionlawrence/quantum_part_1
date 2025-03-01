# Addition of Angular Momentum

In many cases we have multiple degrees of freedom each of which behave in a deifnite way under rotations. However, there is (typically) no physical principle that demands that angular momentum is conserved for each degree of freedom separately. It can be exchanged between particles, just as the total momentum of a multiparticle system is conserved, but is exchanged between particles, or between orbital and spin degrees of freedom (via spin-orbit coupling). 

In the case of total linear or orbital angular momentum in a multiparticle system in otehrwise empty (and thus translationally/rotationally invariant) space, one way to think about this is that while the physics of the entire system is invariant under translations/rotations of the entire system, for each individual particle it matters very much where the other particles are, and translations and rotations are broken at that level.

## General theory

Let us say we hve two degrees of freedom -- perhaps two particles -- described by the Hilbert space $D_{j_1}$ and $D_{j_2}$. The total Hilbert space is $D_{j_1}\otimes D_{j_2}$, with dimension $(2j_1 + 1)(2j_2 + 1)$. Our question is, how this transforms under the ttoal angular momentum 
```{math}
{\vec J}_{tot} = {\vec J}_1 \otimes {\bf 1} + {\bf 1}\otimes {\vec J}_2
```
in general we will drop the tensor product when describing operators, so that ${\vec J}_1\otimes {\bf 1} \to {\vec J}_1$ and so on.

In general, the representation is reducible (the exception being if one or both of $j_i$ are zero). A quick way to see this is to note that $J_{tot,z}$ commutes with $J_{i,z}$ (and ${J}_{1,z}$, $J_{2,z}$ commute with each other), so that we can diagonalize all of them. If we set $j = j_1 + j2$ there is one state with $m = j$,
```{math}
\ket{j_1 j_1}_1\ket{j_2,j_2}_2
```
where we are using the basis $\ket{j_i, m_i}_i$ of eigenstates of ${\vec J}_i^2$, $J_{i,z}$ for each $D_{j_i}$. However, there are two orthogonal states with $m_{tot} = j_1 + j_2 - 1$:
```{math}
\ket{j_1, j_1}_1\ket{j_2, j_2 - 1}_2 \ , {\rm and}\ \ket{j_1, j_1 - 1}_1\ket{j_2, j_2 - 1}
```

In fact, from this starting pojnt we can work out recursively how $D_{j_1}\otimes D_{j_2}$ decomposes. Since the maximum value of $m_{tot}$ is $j_1 + j_2$ and there is only one such state, $D_{j_1}\otimes D_{j_2}$ contains exactly one subspace transforming as the irrep $D_{j_1 + j_2}$. By acting wit $J_{tot,-}$ on this state we can find the state with $j = j_1 + j_2$, $m = j_1 + j_2 - 1$. The space of states with this value of $m$ is two-dimensional. The state in this space orthogonal to the one with $j = j_1 + j_2$ must therefore have $j = j_1 + j_2 - 1$ and there is only one subspace of  $D_{j_1}\otimes D_{j_2}$ with this value of $j$. We can cotinue this argument, stopping when we have found all irreps of the total angular momentum consistent with the dimensionality of  $D_{j_1}\otimes D_{j_2}$. We find that
```{math}
:label: addition_am_rule
D_{j_1}\otimes D_{j_2} = \oplus_{j = |j_1 -j_2|}^{j = j_1 + j_2} D_j
```

We write the basis of the left hand side as $\ket{j_1,m_1; j_2 m_2} = \ket{j_1, m_1}_1\ket{j_2,m_2}_2$, wchih I will call the "product basis". We write the basis of the right hand side as $\ket{j,m}$ (for which the minimum and maximum values of $j$ are understood), which I will call the "total angular momentum basis". The equation relating the bases is
```{math}
\ket{j,m} = \sum_{m_1,m_2} \ket{j_1,m_1; j_2 m_2}\brket{j_1,m_1; j_2,m_2}{j,m}
```
and a similar one expanding the product basis vectors in terms ot the total angular momentuim basis vectors, for which the coefficients are $\brket{j,m}{j_1,m_1;j_2,m_2} = \brket{j_1,m_1; j_2,m_2}{j,m}^*$. These matrix elements are called *Clebsch-Gordon coefficients*, and they can be calculated explicitly by a combination of ladder operators and orthogonalization. They cal also be looked up in tables.

So see how this construction actually works, we start with the observation that $\brket{\brket{j_1,m_1; j_2,m_2}{j,m} = 1$. Next we compute
```{math}
\begin{align}
J_{tot,-} \ket{j_1 + j_2,j_1 + j_2} & \propto \ket{j_1 + j_2,j_1 + j_2 -1} \\
& = (J_{1,-} + J_{2,-})\ket{j_1 j_1; j_2 j_2} \\
& = \hbar \sqrt{2j_1} \ket{j_1 j_1 - 1; j_2 j_2} + \hbar \sqrt{2j_2} \ket{j_1 j_1; j_2 j_2 - 1}\\
\end{align}
```
Thus, normalizing the state,
```{math}
\ket{j_1 + j_2,j_1 + j_2 -1} = \frac{\sqrt{j_1} \ket{j_1 j_1 - 1; j_2 j_2} + \hbar \sqrt{j_2} \ket{j_1 j_1; j_2 j_2 - 1}}{\sqrt{j_1 + j_2}}
```
from which we can compute 
```{math}
\begin{align}
\brket{j_1,j_1 -1; j_2,j_2}{j_1 + j_1,j_1 + j_2 -1} & = \frac{\sqrt{j_1}}{\sqrt{j_1 + j_2}}\\
\brket{j_1,j_1; j_2,j_2 - 1}{j_1 + j_2 ,j_1 + j_2 -1} & =  \frac{\sqrt{j_2}}{\sqrt{j_1 + j_2}}
\end{align}
```
Next, the state $\ket{j_1 + j_2 - 1, j_1 + j_2 - 1}$ by finding the state with $m_{tot} = j_1 + j_2 - 1$ which is orthonormal to $\ket{j_1 + j_2, j_1 + j_2 - 1}$:
```{math}
\ket{j_1 + j_2 - 1, j_1 + j_2 - 1} = \frac{\sqrt{j_2} \ket{j_1,j_1 - 1; j_2,j_2} - \sqrt{j_1} \ket{j_1,j_1;j_2,j_2 -1}}{\sqrt{j_1 + j_2}}
```
from which we can construct additional Clbsch-Gordon coefficients
```{math}
\begin{align}
\brket{j_1,j_1 -1; j_2,j_2}{j_1 + j_1- 1,j_1 + j_2 -1} & = \frac{\sqrt{j_2}}{\sqrt{j_1 + j_2}}\\
\brket{j_1,j_1; j_2,j_2 - 1}{j_1 + j_2-1 ,j_1 + j_2 -1} & =  \frac{\sqrt{j_1}}{\sqrt{j_1 + j_2}}
\end{align}
```
and so on.

From here we will work out the simplest example; others are left as exercises.

## Two spin-$\half$ particles

This is the simplest non-trivial example. We can also make use of the fact that both spins are described by identical Hilbert spaces.

The rule {eq}`addition_am_rule`
gives us
```{math}
D_{\half}\otimes D_{\half} = D_1 \oplus D_0
```
We can compute the basis $\ket{j,m}$ using brute force following the discussion above, and I encourage you to do this to aid your overall understanding. Here I will take a different tack (that will not work for $D_{j_1}\otimes D_{j_2}$ when $j_1 \neq j_2$). We consider the exchange operator acting on the product basis as:
```{math}
\sigma\ :\ \ket{\half,m_1; \half,m_2} \to \ket{\half,m_2; \half,m_1}
```
This is unitary with eigenvalues $\pm 1$ (this follows form $\sigma^2 = 1$). It commutes with ${\vec J}_{tot}$ so we can simultaneously diagonalize ${\vec J}_{tot}^2, \sigma$.

Let us first consider $\sigma = -1$ states. A moment's thought reveals there is only one possible, which after imposing unit norm, is
```{math}
\ket{j = 0} = \frac{1}{\sqrt{2}}\left(\ket{\half,\half; \half,-\half} - \ket{\half,-\half;\half,\half}\right)
```
This $j = 0$ state is called the *spin singlet* state.

Next we consider $\sigma = 1$. The $m = \pm 1$ states are easy to dedice; the $m = 0$ state must have $\sigma = 1$ as well, which instanly yields the basis
```{math}
\begin{align}
\ket{1,1} & = \ket{\half,\half;\half,\half}\\
\ket{1,0} & = \frac{1}{\sqrt{2}}\left(\ket{\half,\half; \half,-\half} + \ket{\half,-\half;\half,\half}\right)\\
\ket{1,-1} & = \ket{\half,-\half; \half,-\half}
\end{align}
```
These are clled the *spin triplet* states. 

It is straightforward to work out the Clebsch-Gordon coefficients in this case. The nonvanishing coefficients are:
```{math}
\begin{align}
\brket{\half,\pm\half;\half,\mp\half}{0,0} & = \pm \frac{1}{\sqrt{2}}\\
\brket{\half,\half;\half,\half}{1,1} & = 1\\
\brket{\half,\pm\half;\half,\mp\half}{1,0} & = \frac{1}{\sqrt{2}}\\
\brket{\half,-\half;\half,-\half}{1,-1} & = 0
\end{align}
```


