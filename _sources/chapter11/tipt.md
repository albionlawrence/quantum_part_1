# Time-independent perturbation theory

The basic setup is simple. We consider Hamiltonians of the form
```{math}
H = H_0 + \eps H_1
```
where $\eps \ll 1$. Here we are assuming that the matrix elements of $H_1$ are of the same order or smaller than those of $H_0$. We wish to solve the time-independent Schroedinger equation $H \ket{\psi} = E \ket{\psi}$ when the solutions for $H_0$ are known. We will also assume that the spectra of $H_0$ are discrete. States in the regime with continuous spectra require a different treatment via scattering theory.

Since the eigenvalues and eigenvectors $\ket{n}$, $E_n$ should be those of $H_0$ as $\eps \to 0$, we make the following assumptions about the true eigenvalues and eigenvectors.
```{math}
\begin{align}
E & = E^{(0)}_n + \eps E^{(1)}_n + \eps^2 E^{(2)}_n + \ldots\\
\ket{n} & = \ket{n^{(0)}} + \eps \ket{n^{(1)}} + \eps^2 \ket{n^{(2)}} + \ldots 
\end{align}
```
where $H_0 \ket{n^{(0)}} = E^{(0)}_n$, and the eigenvectors are taken to be orthonormal. We then write
```{math}
:label: tise_expansion
H\ket{n} & = (H_0 + \eps H_1) \left( \ket{n^{(0)}} + \eps \ket{n^{(1)}} + \eps^2 \ket{n^{(2)}} + \ldots\right)\\
&= E\ket{n}\\
& = \left( E^{(0)}_n + \eps E^{(1)}_n + \eps^2 E^{(2)}_n + \ldots\right)\left(\ket{n^{(0)}} + \eps \ket{n^{(1)}} + \eps^2 \ket{n^{(2)}} + \ldots\right)
```
We then demand that this equation be solved order by order in $\eps$. The solution at order $\eps^n$ is known as $n$th order perturbation theory.

## First order perturbation theory (non-degenerate)

The $\eps^0$ terms cancel by supposition. At $\cO(\eps)$, the terms are:
```{math}
H_1 \ket{n^{(0)}} + H_0 \ket{n^{(1)}} = E^1_n \ket{n^{(0)}} + E^0_n \ket{n^{(1)}}
```
We first take the inner product of this equation with $\bra{n^{(0)}$, and find
```{math}
\bra{n^{(0)}}H_1\ket{n^{(0)}} + E^0_n \brket{n^{(0)}}{n^{(1)}} = E^1_n + E^0_n \brket{n^{(0)}}{n^{(1)}}
```
or
```{math}
:label: first_order_E_correction
E^1_n = \bra{n^{(0)}}H_1\ket{n^{(0)}}
```

Next, we take the inner product with $\bra{m^{(0)}}$ for $m \neq n$. Then we have
```{math}
\bra{m^{(0)}} H_1 \ket{n^{(0)}} + E^0_m \brket{m^{(0)}}{n^{(0)}} = E^0_n \brket{m^{(0)}}{n^{(1)}}
```
or
```{math}
 \brket{m^{(0)}}{n^{(1)}} = \frac{\bra{m^{(0)}} H_1 \ket{n^{(0)}}}{E^0_m - E^0_n}
```
We can see that this fails if $E^0_n$ is a degenerate eigenvalue, as there will be terms in the above expression with vanishing denominator. We will turn to this case later, and instead assume that there is no degeneracy. The techniques we explore here are called *non-degenerate perturbation theory*. 

Now $\ket{m^{(0)}}$ is a complete basis in the Hilbert space, as $H_0$ is a Hermitian operator. To find $\ket{n^{(1)}}$, we will need to know $\brket{n^{(0)}}{n^{(1)}}$. I will demand that $\brket{n^{(0)}}{n} = 1$, which is not yet the standard normalization. We can rescale $\ket{n}$ after our calculation, but computig its norm and then dividing $\ket{n}$ by it. The upshot is that since $\brket{n^{(0)}}{n^{(0)}} = 1$, and $\ket{n} = \ket{n^{(0)}} + \ldots$, all corrections to $\ket{n^{(0)}}$ will be orthogonal to $\ket{n^{(0)}}$. 

Given this, and that $\sum_n \ket{n^{(0)}}\bra{n^{(0)}} = 1$, we have
```{math}
:label: fo_state
\ket{n^{(1)}} = \sum_{m\neq n} \frac{\ket{m^{(0)}} \bra{m^{(0)}} H_1 \ket{n^{(0)}}}{E_n^0 - E_m^0}
```
Note that at this order the norm of the state only differs from $1$ by a factor of $\cO(\eps^2)$; we will need to go to second order in corrections to $\ket{k}$ to compute the norm, and to see what is needed to properly normalize the state. 

### Example: anharmonic oscillator

The classic example is the anharmonic quantum oscillator:
```{math}
H = \frac{p^2}{2m} + \half m \omega^2 x^2 + \frac{\lambda}{4!} x^4
```
We will do perturbation series with the parameter $\lambda$. You should be objecting that this isn't quite right. $\lambda$ has dimensions of $(energy)/(length)^4$. As a dimensionful paraneter one cannot technically call it "small". But we can combine this with the parameters of the unperturbed Hamiltonian to make a small parameter. For example, we know that we have a length scale 
```{math}
L = \sqrt{\frac{\hbar}{m\omega}} 
```
and an energy scale ${\cal E} = \hbar\omega$. So by dimensional analysis, the combination
```{math}
\eps = \frac{\lambda L^4}{{\cal E}} = \frac{\hbar \lambda}{m^2\omega^3}
```
is a likely perturbation parameter. We will see that this does in fact control the correction terms in perturbation theory.

The correction to the energy $E^{(0)}_k = \hbar\omega(k + \half)$ in this case is taken from {eq}`first_order_E_correction`:
```{math}
\begin{align}
E^{(1)}_k & = \bra{k^{(0)}} \lambda x^4 \ket{k^{(0)}}\\
& = \lambda L^4  \bra{k^{(0)}}(a + a^{\dagger})^4 \ket{k^{(0)}}\\
& = \lambda L^4 (6 k^2 + 6k + 3)
\end{align}
```
Now for $k \sim {\cal O}(1)$, the ratio of this to the energy gap $\hbar \omega$ is $\sim k^2 \eps$, confirming our point above. furthermore, note that once $k^2 \sim 1/\eps$, this correction is no longer small. This is a general feature of perturbation theory; it only works for low energies.

Similarly the first order correction to the state {eq}`fo_state` gives:
```{math}
\begin{align}
\ket{k^{(1)}} & = \sum_{\ell \neq k} \frac{\lambda L^4 \ket{\ell^{(0)}} (a + a^{\dagger})^4\ket{k^{(0)}}}{\hbar\omega (k-\ell)}\\
& = \eps  \sum_{\ell \neq k} \frac{\ket{\ell^{(0)}} (a + a^{\dagger})^4\ket{k^{(0)}}}{k - \ell}
\end{align}
```
We can see again how the dimensionless parameter $\eps$ appears. The numerator is straightforward but tedious to evaluate. $(a + a^{\dagger})^4$ clearly connects the level $k$ to the levels in the range $\ell \in \{k-4, k-2,k+2,k+4\}$ (you should think about why $k - 1, k-3$ do not appear). So the ratio will scale with $k^2$, and again if $\eps k^2 \sim \cO(1)$, perturbation theory will start to break down.

## Second order perturbation theory

It is worth going out one more order so that you can see how things develop and how complicated they get. Also, it is often the case that corrections to the energy vanishes at first order. For example, let us say that we perturbed the harmonic oscillator by $-\alpha x$. (In fact this is exactly solvable; but we can still do perturbatiob theory and I'm trying to make a point. By the way, what might you worry about if the perturbation was by $g x^3$?). The first order energy shift $\bra{k^{(0)} x \ket{k^{(0)} = 0$ because the states have definite parity but $x$ has odd parity. Thus $x\ket{k}$, $ket{k$ have opposite parity, and so zero overlap.

The $\cO(\eps^2)$ terms in {eq}`tise_expansion` are:
```{math}
H_0 \ket{n^{(2)}} + H_1 \ket{n^{(1)}} = E_n^{(0)} \ket{n^{(2)}} + E_n^{(1)}\ket{n^{(1)}} + E_n^{(2)} \ket{n^{(0)}}
```
Taking the inner product with $\bra{n^{(0)}}$, the first terms on each side cancel off of each other. The second term on the RHS canishes by our normalization convention. Thus, we find
```{math}
:label: second_order_energy
\begin{align}
E_n^{(2)} & = \bra{n^{(0)}} H_1 \ket{n^{(1)}}\\
& = \sum_{\ell \neq k} \frac{\bra{n^{(0)}} H_1 \ket{\ell^{(0)}} \bra{\ell^{(0)}} H_1 \ket{n^{(0)}}}{E_n^0 - E_m^0}\\
& = \sum_{\ell \neq k} \frac{| \bra{\ell^{(0)}} H_1 \ket{n^{(0)}}|^2}{E_n^0 - E_m^0}
\end{align}
```

We can similarly work out the second order correction to the state, again assuming that it is orthoginal to the zeroth order correction:
```{math}
:label: so_state
\begin{align}
\ket{n^{(2)}} & = \sum_{\ell,m\neq n} \frac{\ket{m^{(0)}}\bra{m^{(0)}} H_1 \ket{\ell^{(0)}}\bra{\ell^{(0)}} H_1 \ket{n^{(0)}}}{(E_n^{(0)} - E_m^{(0)})(E_n^{(0)} - E_{\ell}^0)}\\
& \qquad\qquad -\sum_{m\neq n} \frac{\bra{m^{(0)}}\ket{m^{(0)}}\bra{m^{(0)}} H_1 \ket{n^{(0)}} \bra{n^{(0)}} H_1 \ket{n^{(0)}}}{(E_n^0 - E_m^0)^2}
\end{align}
```

Now let us work out the normalization of this state. We define
```{math}
\begin{align}
\frac{1}{Z} & = \brket{n}{n} \\
& = \brket{n^{(0)}}{n^{(0)}} + \eps^2 \brket{n^{(1)}}{n^{(1)}}\\
& = 1 + \eps^2 \sum_{m \neq n} \frac{|\bra{m^{(0)}}H_1 \ket{n^{(0)}}|^2}{(E_n^0 - E_m^0)^2} + \cO(\eps^3)
\end{align}
```
Note that the overlap of the zeroth and second order correction does not appear, by our normalization assumption. Note that at this order, we can write
```{math}
Z \sim 1 -  \eps^2 \sum_{m \neq n} \frac{|\bra{m^{(0)}}H_1 \ket{n^{(0)}}|^2}{(E_n^0 - E_m^0)^2}
```
so that the following state has unit norm
```{math} 
\sqrt{Z} \ket{n}
```
where both terms are understood to go to $\cO(\eps^2)$.

There is a nice expression for $Z$ in this case. Note that to $\cO(\eps^2)$,
```{math}
\begin{align}
\frac{\del E_n}{\del E_n^0} & = \frac{\del}{\del E_n^0}\left(E_n^0 + \eps \bra{n^{(1)}} H_1 \ket{n^{(1)}} + \eps^2 \sum_{m\neq n}\frac{|\bra{m^{(0)}}H_1 \ket{n^{(0)}}|^2}{(E_n^0 - E_m^0)}\right)\\
& = 1 - \eps^2 \sum_{m\neq n}\frac{|\bra{m^{(0)}}H_1 \ket{n^{(0)}}|^2}{(E_n^0 - E_m^0)^2} \\ 
& \sim Z
\end{align}
```
In fact, the formula
```{math}
Z = \frac{\del E_n}{\del E_n^0}
```
holds to all orders in $\eps$.

### Example: the quadratic Stark effect

A more nontrivial example is the response of the hydrogen atom to al electric field, for which $H_0$ is the usual Coulomb Hamiltonian, and $H_1 = - e E z$, corresponding to a charged particle in a constant electric field ${\vec E} = E {\hat z}$. Can you give an estimate of the dimensionless parameter that controls the size of teh corrections?
