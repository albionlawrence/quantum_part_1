# Identical Particles

## Generalities

We start with the Hilbert space of $N$ particles each of which are described by the same degrees of freedom. The Hilbert space is the $N$-fold tensor product of the one-particle Hilbert space $\cH$:
```{math}
\cH_N = \cH \otimes \cH \otimes\ldots \cH \equiv \cH^{\otimes N}
```

Now we consider the action of the permutation group $S_N$ on this space. Recall that a permutation $\sigma \in S_N$ shuffles 
```{math}
	\sigma: (1,2,3,\ldots,N) \to (\sigma(1),\sigma(2),\ldots,\sigma(N))
```
Thus, for example, $S_3$ consists of the six permutations
```{math}
\begin{array}
\sigma_1 : & (1,2,3) & \to (1,2,3) \\
\sigma_2 : & &  \to (2,3,1) \\
\sigma_3 : & & \to (3,1,2) \\
\sigma_4 : & & \to (1,3,2) \\
\sigma_5 : & & \to (3,2,1) \\ 
\sigma_6 : & & \to (2,1,3)
\end{array}
```
Note that we are including the identity here. For a state
```{math}
\ket{\psi} = \sum_{1_1,\ldots,i_N} c_{i_1,\ldots,i_N}\ket{\psi_{i_1}}\ldots\ket{\psi_{i_N}} \in \cH_N
```
a given permutation acts as
```{math}
\sigma: \ket{\psi} \to  \sum_{1_1,\ldots,i_N} c_{i_1,\ldots,i_N}\ket{\psi_{i_\sigma(1)}}\ldots\ket{\psi_{i_\sigma(N)}}
```
which makes sense because each factor of $cH_N$ is the identical Hilbert space $\cH$. This is a linear operator if we take 
```{math}
\sigma: a \ket{\psi} + b \ket{\chi} \to a \sigma(\ket{\psi}) + b \sigma(\ket{\chi})
```

For $N \geq 3$, $S_N$ is a complicated, non-Abelian group with $N!$ elements and a number of multidimensional irreps. The detailed structure of the group and its irreps is a mathematically interesting and important exercise that we will sadly forgo (this is an application of *Young Tableaux*: see for example {cite:p}`landau1991quantum`, {cite:p}`georgi1999lie`). We will simply note the following two facts. The first is that *any* element of $S_N$ can be written as a sequence of pairwise permutations
```{math}
\sigma_{ij}: (1,\ldots,i,\ldots,j,\ldots,N) \to  (1,\ldots,j,\ldots,i,\ldots,N)
```
We can furthermore classify such permutations as "even" or "odd" depending on the number of such pairwise permutations. Thus, in the $S_3$ example above, $\sigma_{1,2,3}$ (the cyclic permutations) are even while $\sigma_{4,5,6}$ are odd.

Let $(-1)^{\sigma} = +1$ for even permutations and $-1$ for odd permutations. Two one-dimensional irreps are the totally symmetric wavefunctions
```{math}
:label: symm_rep
\ket{\psi} = \sum_{\sigma\in S_N} \ket{\psi_{\sigma(1)}}\ket{\psi_{\sigma(2)}}\ldots \ket{\psi_{\sigma(N)}}
```
and the totally antisymmetric wavefunctions
```{math}
:label: as_rep
\ket{\psi} = \sum_{\sigma\in S_N} (-1)^{\sigma} \ket{\psi_{\sigma(1)}}\ket{\psi_{\sigma(2)}}\ldots \ket{\psi_{\sigma(N)}}
```
Note that, crucially, in the second case, $\ket{\psi} \neq 0$ only if $\ket{\psi_i} \neq \ket{\psi_j}$ for *all* $i \neq j$.

Now consider the system $\cH_N$ with a Hamiltonian $H$ that is symmetric under permutations: that is, for and $\sigma \in \cH$, $[\sigma, H] = 0$. 

It is a nontrivial result of relativistic quantum field theory known as the *spin-statistics theorem* (but first conjectured by Pauli) that for any set of identivcal particles, the Hilbert space consists of either the subset of $cH_N$ consisting of totally symmetric or totally antisymmetric wavefunctions, and that this is correlated with the spin of the particle. More precisely:

1. For particles with *integer spin* $j = 0,1,2,\ldots$, the Hilbert space $\cH \subset \cH_N$ for $N$ particles is the set of totally symmetric wavefunctions. Such particles are known as *bosons*.

2. For particles with *half-integer spin* $j = \half, \frac{3}{2}, \frac{5}{2},\ldots$, the Hilbert space $\cH \subset \cH_N$ is the subset of totally antisymmetric wavefunctions. Such particles are known as *fermions*.

I have made this statement for three dimensions, and it persists in higher dimensions. In $d = 1,2$ the rotation group is trivial and Abelian, respectively, and the quantization of spin is no longer obvious or necessary. For $d = 2$ this leads to the important phenomenon of *fractional statistics*, important for the Fractional Quantum Hall Effect.

Note that in the standard model of particle physics, the bosonic particles consiste of the "force carriers" -- the photon, the W and Z bosons, and the gluons -- as well as the Higgs boson (which mixes with teh W and Z bosons). The *matter* particles -- electrons, quarks, and neutrinos -- all have spin-$\half$. The neutrons and protons are bound states which themselves have spin-$\half$, and can thus be treated as fermions.

## Some consequences

This fact has far-reaching consequences for the structure of quantum matter. A particularly important consequence for fermions is the *Pauli exclusion principle*. That is, if in the state {ref}`as_rep` $\ket{\psi_i} = \ket{\psi_j}$ for any $i \neq j$, the wavefunction vanishes. Thus, no two particles can occupy the same one-particle state. Now atoms are made up of fermionic constituents, and most matter we observe is made up of atoms or these constituents, the Pauli exclusion principle is key to the stability of matter, the behavior of metals (with fermionic charge carriers), the structure of white dwarves and neutron stars (in the former one can consider the nuclei and electrons separately; in the latter the bulk of the star consists entirely of neutrons, though there is some speculation that the core of the star is made up of mode exotic matter that involves strange quarks). The Pauli principle helps stabilize these stars against gravitational collapse into a black hole. 

Before moving on we mention some simple examples. First, let us consider the simplest case ot two spin-$\half$ particles. If spin is their *only* quantum number, the Hilbert space $\cH_{\half}\otimes\cH_{\half}  = \cH_{j = 1} \oplus \cH_{j = 0}$. Now in this presentation $\cH_{j = 1}$ consists of states symmetric under the action of $S_2$, while $\cH_{j = 0}$ consists of states that are totally antisymmetric under the action of $S_2$. The Pauli exclusion principle means that in this case, the state must lie in the $\cH_{j = 0}$ subspace.

If we include additional quantum numbers we have a different story. For example, assume the particles move in space and can have one of the two spatial wavefunctions $\ket{\psi_{i = 1,2}}$. A basis of one-particle states is then $\ket{\half,\pm\half}\ket{\psi_i}$. Then we are allowed the following states of the two-particler Hilbert space:
```{math}
\frac{1}{\sqrt{2}} \ket{j = 1, m}\left(\ket{\psi_1}\ket{\psi_2} - \ket{\psi_2}\ket{\psi_1}\right)
```
and
```{math}
\frac{1}{\sqrt{2}} \ket{j = 0}\left(\ket{\psi_1}\ket{\psi_2} + \ket{\psi_2}\ket{\psi_1}\right)
```
More generally, if our identical particles come with some quantum number -- the eigenvalue of some linear operator -- such that each particle has a distinct quantum number, we can think of these quantum numbers as labels; if the associated quantum numbers are conserved under the Hamiltonian, the labels do not change and we can consider the particles as *distinguishable*; if we keep these labels fixed and distinct, there is no restriction on the remaining quantum numbers in that we can have a situation where when we measure two particles with distinct labels, the spin, wavefunction, and so on can be completely correlated with these labels and can be identical so long as the labels are distinct. 

Let us consider the situation in which we have $N$ noninteracting identical particles. That is, the Hamiltonian is $H = H\otimes{\bf 1}\cdots \otimes {\bf 1} + {\bf 1}\otimes H \cdots \otimes {\bf 1} + \ldots {\bf 1}\otimes{\bf 1} \cdots \otimes H$. This clearly commutes with permutations. How consider the orthonormal energy eigenbasis $\ket{E_{n = 1,2,3,\ldots}}$ of the one-particle Hilbert space $\cH$, such that $E_1 \leq E_2 \leq E_3,\ldots$. If the state $\ket{E_0}$ is non-degenerate, the ground state for bosons is clearly
```{math}
\ket{0_{bose}} = \ket{E_1}\ldots\ket{E_1}
```
(if the particles have additional degrees of freedom such as spin which are conserved quantities, then this ground state will be degenerate). The total energy is then $N E_1$.

For fermions, if there are no degeneracies, 
```{math}
\ket{0_{fermi}} = \sum_{\sigma\in S_N} (-1)^{\sigma} \ket{E_{\sigma(1)}}\cdots\ket{E_{\sigma(N)}}
```
The total energy here is $\sum_{k = 1}^N E_k$. Note that if the energy level $E_N$ is degenerate, the Fermi gas will have degeneracies. As an example, assume that the single particles have spin-$\half$ *and* that the Hamiltonian commutes with rotations. The one-particle Hamiltonian is thus degenerate. Let us say that each energy eigenstate has only the two-fold degeneracy corresponding to the state of the spin. For an even total number $N = 2M$ of such particles, the ground state is nondegenerate and has energy $E_0 = 2 \sum_{k = 1}^M E_k$. If we have an odd number of particles $N = 2M + 1$, the system has a two-fold degeneracy corresponding to one particle having energy $E_{M + 1}$ and either spin state. The total energy is $E_0 = 2 \sum_{k = 1}^M E_k + E_{M + 1}$. In these cases, the largest singkle-particle energy in the ground state is known as the *Fermi energy*. Typically, the lowest-lyig excitations consists of exciting the most energetic single particle to a state just higher than the Fermi energy. for example, consider an even number $2M$ of spin-$\half$ fermions confined to one dimension and living in a potential well with potential energy $V = \half m \omega^2 x^2$. The ground state is nondegenerate with energy 
```{math}
E_0 = 2 \hbar\omega \sum_{k = 1}^M (k - \half) = \hbar \omega M^2
```
The first excited state has a two-fold degeneracy, with energy $E = \hbar \omega (M^2 + 1)$ (you should think about why this is true).


