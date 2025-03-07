# Time-dependent perturbation theory

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
\ket{n^{(1)}} = \sum_{m\neq n} \frac{\ket{m^{(0)}} \bra{m^{(0)}} H_1 \ket{n^{(0)}}}{E_m^0 - E_n^0}
```
