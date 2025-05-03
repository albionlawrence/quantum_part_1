# TDPT systematics: the Dyson series

Let us focus on the TDSE in the interaction picture. You can convince yourself that if $V_S(t)$ is a Hermitian operator, so is $V_I(t)$. Now the TDSE in the interaction picture
```{math}
:label: ip_tdse
i\hbar \partial_t\ket{\psi(t)}_I = \eps V_I(t) \ket{\psi(t)}_I
```
is formally the same as the full TDSE with $\ket{\psi(t)}_S \to \ket{\psi(t)}_I$, $H \to V_I$. Thus $\ket{\psi(t)}_I$ also undergoes unitary time evolution with U_I(t,t_0) = e^{i H_0 t/\hbar} U_S(t,0)$. We can construct it directly from this, or by writing $\ket{\psi(t)}_I = U_I(t,0) \ket{\psi(0)}$ and inserting this into {eq}`ip_tdse` to find:
```{math}
i\hbar \del_t U_I(t,0) = \eps V_I(t) U_I(t,0)
```

We can solve this formally by noting that $U_I(0,0) = {\bf 1}$:
```{math}
:label: recursive_unitary
U_I(t) = {\bf 1} - \frac{i}{\hbar}\int_0^t dt' \eps V_I(t') U_I(t')
```
where I have suppressed the dependence on the initial time. This may not seem useful, but since we are eventuall looking for a power series in $\eps$ we can solve this equation recursively. That is, plug the LHS of {eq}`recursive_unitary` into the RHS, so that
```{math}
U_I(t) = {\bf 1} - \frac{i\eps}{\hbar} \int_0^t dt' V_I(t') + \left(\frac{-i \eps}{\hbar}\right)^2 \int_0^t dt' \int_0^{t'} dt'' V_I(t') V_I(t'') U_I(t'') + \ldots
```
Clearly we can continue this trend and write the *Dyson series*
```{math}
U_I(t) = \sum_{n = 0}^{\infty} \left(\frac{-i \eps}{\hbar}\right)^n \int_0^t dt_1 \int_0^{t_1} dt_2 \ldots \int_0^{t_{n-1}} dt_N V_I(t_1) V_I(t_2)\ldots V_I(t_n)
```
Note that the products of $V_I(t)$ are arranged in descending order of the time variable in their argument. With some work, one can convince oneself that this can be written as
```{math}
U_I(t) = \sum_{n = 0}^{\infty} \left(\frac{-i \eps}{\hbar}\right)^n \frac{1]{n!}\int_0^t dt_1 \ldots \int_0^t dt_n T[V_I(t_1) V_I(t_2)\ldots V_I(t_n)]
```
where $T$ is the *time ordering operator*. That is, given a set of times $t_{i = 1,\ldots, n}$, and a permutation $\sigma \in S_n$ such that 
```{math}
t_{\sigma(1)} \geq t_{\sigma(2)} \geq \cdots \geq t_{\sigma(n)}
```
Then
```{math}
T[V_I(t_1)\ldots V_I(t_n)] = V_I(t_{\sigma(1)})V_I(t_{\sigma(2)}) \ldots V_I(t_{\sigma(n)})
```
The integration region is now redundant (because before applying the $T$ operator it is over all time orderings), which is taken care of by the factor of $1/n!$. We can write this expression more elegantly as
```{math}
U(t) = T \left[ \exp\left( - \frac{i\eps}{\hbar}\int_0^t dt' V_I(t')\right)\right]
```

