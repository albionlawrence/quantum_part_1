# Two-state systems as phonomenological models

Here we are going to consider the low-energy dynamics of generally complicated systems. While we have not gone into length in talking about time-dependent probes yet, you can intuit that interacting with a given system will generally involve adding or subtracting energy. For example, usually an experiment is a time-dependent process, so right there you know that energy will not be conserved. But by the energy-time uncertainty principle, if you interact sufficiently slowly, the energy input will not be large. Thus, if the systems starts in the ground state or first excited state, and the energy input is small compared to the energy difference between the first and second excited state, you can assume that before and after the experiment is done, it will remain in some superposition of teh ground state and first excited state. The Hilbert space is thus quite simple, and the Hamiltonian will be parameterized by just a few numbers (the entries of a $2\times 2$ Hermitian matrix) which one can fit to experiments, in the case that first--principles calculations are too hard.

## Double-well potential

The first system we will examine is one that we could in principle solve exactly. Consider the following double-well potential for a 1d particle with mass $m$:
```{math}
V(x) = \begin{cases} \infty & x \leq - L - \frac{a}{2} \\ 0 & - L - \frac{a}{2} < x < - \frac{a}{2} \\ V_0 > 0 & - \frac{a}{2} \leq x \leq \frac{a}{2} \\ 0 & \frac{a}{2} < x < \frac{a}{2} + L \\ \infty & x > L + \frac{a}{2} \end{cases}
```
Thus $L$ is the width of each well, and $a$ the width of the barrier.

### Warmup: Infinite barrier

To get some intuition for this we will start with the $V_0 \to \infty$ case. In this case, we take $\cH_{L,R}$ to be the Hilbert space for the particle in the left or right wells, and $\cH_{\infty} = \cH_{L} \oplus \cH_{R}$. The particle can sit in either the left well or the right well, and the Hamiltonian is diagonal. The wavefunctions and eigenenergies are:
```{math}
:label: isw_eigen
\begin{align}
\psi^L_n & = \begin{cases} \sqrt{\frac{2}{L}} \sin \left(\frac{\pi n (x + L + \frac{a}{2})}{L}\right) & - L - \frac{a}{2} < x < - \frac{a}{2} \\ 0 & {\rm otherwise} \end{cases} \\
& E^L_n = \frac{\hbar^2\pi^2 n^2}{2m L^2} \\
\psi^R_n & = \begin{cases} \sqrt{\frac{2}{L}} \sin \left(\frac{\pi n (x - \frac{a}{2})}{L}\right) & L + \frac{a}{2} > x > \frac{a}{2} \\ 0 & {\rm otherwise} \end{cases} \\
& E^R_n = \frac{\hbar^2\pi^2 n^2}{2m L^2} \\
\end{align}
```
So each energy level is doubly degenerate, as the energy levels for the particle localized in the left or the right well are the same (since the wells have the same width and boundary conditions).  Note that we can write these wavefunctions as
```{math}
\psi^{A = L,R}_n(x) = \brket{x}{n;\ A}
```
where $A$ is an index labeling the wells. 

In this case, parity is a clear symmetry of the theory. As we have already discussed, we can re-arrange the energy spectrum in terms of parity eigenstates:
```{math}
\ket{n,\pm} = \frac{1}{\sqrt{2}} \left(\ket{n; L} \pm \ket{mn,R}\right)
```

### Large but finite barrier

If we let $V_0$ be finite, the degeneracy is split as is generically the case in 1d problems. But as you might expect, the higher the barrier the smaller the splitting. In practice the splitting is very small: one can make a hand-waving argument that it scales like 
```{math}
\Delta E = \frac{\hbar}{\tau} \propto \frac{\hbar v}{L} e^{- \frac{a}{\hbar}\sqrt{2 m V_0}} = \frac{\pi \hbar^2}{m L^2} e^{- \frac{a}{\hbar}\sqrt{2mV_0}}
```
The prefactor is based on a classical velocity $v$ such that $\half m v^2 = E$ and we have used the ground state energy for $E$; $L/v$ is proportional to the rate the particle his the barrier as is bounces back and forth in the well. The exponential prefactor can be calculated exactly or via the WKB approximation which we will discuss later. The important point is that it governs the splitting and becomes *very* small as we increase $a$ or $V_0$.  Our attitude will be to just assume based on intuition that the splitting is small, and that if we make $V_0$ big enough then $\Delta E \ll E^A_2 - E^A_1$. As $V_0 \to \infty$ we get the doubly degenerate spectrum above. For $V_0$ sufficiently large and finite, the spectrum should be as shown in the figure below. 
