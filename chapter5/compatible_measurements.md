# Compatible and incompatible measurements

## Compatible measurements

We say that two measurments, corresponding to two operators $A, B$, are *compatible* if we can specify the values of both in an experiment. That is, it makes sense to say that a state has an eigenvalue $a$ of $A$ and an eigenvalue $b$ of $B$. Thus we must be able to diagonalize both in the same basis. As we showed, iin Chapter 3, this is possible if and only of $[A,B] = 0$.

In many cases the operators we study have degenerate spectra. In this case, the measurement of a given operator does not lead to a unique stateafter the wavefunction collapses. In this case we try to search for a *complete set of commuting observables* (CSCO); that is, operators $A_1,\ldots,A_k$ such that $[A_i,A_j] = 0$, and such that if we specify eigenvalues $A_1,\ldots,a_k$ of each of these, we uniquely specify the state.

In some cases this could be a single operator (eg, an operator without degeneracy). An example in which we need several is the nonrelativistic hydrogen atom. The energy levels are highly degenerate; we split them by considering eigenvlaues of the angular momentum operators ${\vec L}^2$, $L_z$, ${\vec S}^2$, $S_z$.

## Incompatible measurements and the uncertainty principle

Recall that we defined the variance of an observable in a given state by:
```{math}
:label: variance
(\Delta A)^2 = \bra{\psi} (A - \vev{A})^2\ket{\psi}
```
where $\vev{A} = \bra{\psi}A\ket{\psi}$ is the expectation value of the observable in taht state. $\vev{A}$ represents the average of the outcomes of measuring $A$ in a given state (where we prepare this idential state and measure $A$ in it many times).  $(\Delta A)^2$ is an estimate of the spread or *variancce* in measurements of $A$; a cartoon of this is shown here:

![Illustration of variance](Variance.pdf)

When is the variance zero? For a Hermitian operator t requires that 
```{math}
:label: variance_as_norm
\begin{align}
\bra{\psi} (A - \vev{A})^2\ket{\psi} & = \bra{\psi} (A - \vev{A})^{\dagger}(A - \vev{A})\ket{\psi} \\
& = ||(A - \vev{A})\ket{\psi}||^2
\end{align}
```
But the norm of a vector is zero if and only if the vector is zero, which means that $A\ket{\psi} = \vev{A}\ket{\psi}$, that is, $\ket{\psi}$ is an eigenvactor and $\vev{A}$ the associated eigenvalue. 

Now if we have two observables $A,B$, and they commute, then we can specify them both perfectly and it is possible for both of their variances to be zero. If they do not commute it is a different story.

Let us consider the general case $[A,B] = i C$ for $A,B,C$ Hermitian operators.
The *Uncertainty Principle* in this general case is state in the following theorem:
```{math}
:label: gen_uncertainty
\Delta A \Delta B \geq \half \vev{C}
```

*Proof*. If the system is in state $\ket{\psi}$, we can define
```{math}
:label: shifted_states
\begin{align}
\ket{f_A} & = (A - \vev{A})\ket{\psi}\\
\ket{f_B} & = (B - \vev{B})\ket{\psi}
\end{align}
```

Now, by the Schwarz inequality,
```{math}
\begin{align}
& |\brket{f_B}{f_A}|  \leq ||\ket{f_A}||\ ||\ket{f_B}||\\
& \Rightarrow  |\brket{f_B}{f_A}|^2 \leq \brket{f_A}{f_A}\brket{f_B}{f_B}\\
& \Rightarrow |\brket{f_B}{f_A}|^2 \leq (\Delta A)^2 (\Delta B)^2
\end{align}
```
Now we need to show that the left hand side of this last inequality is an upper bound on $\frac{1}{4}\vev{C}^2$.
```{math}
\begin{align}
|\brket{f_A}{f_B}|^2 & = (\text{Im} \brket{f_A}{f_B})^2 +  (\text{Re} \brket{f_A}{f_B})^2 \\
& = (\text{Im}(\bra{\psi}(A - \vev{A})(B - \vev{B})\ket{\psi}))^2 +  (\text{Re}(\bra{\psi}(A - \vev{A})(B - \vev{B})\ket{\psi}))^2\\
& = (\frac{1}{2i}(\bra{\psi}(A - \vev{A})(B - \vev{B})\ket{\psi} - \bra{\psi}(B - \vev{B})(A - \vev{A})\ket{\psi}))^2\\
& \ \ + (\half((\bra{\psi}(A - \vev{A})(B - \vev{B})\ket{\psi} + \bra{\psi}(B - \vev{B})(A - \vev{A})\ket{\psi})))^2\\
& = \left(\frac{1}{2i}\bra{\psi}[A,B]\ket{\psi}\right)^2 + \left(\half\bra{\psi}\{A,B\}\ket{\psi} - \vev{A}\vev{B}\right)^2\\
& \geq \frac{1}{4} \vev{C}^2
\end{align}
```

When is this inequality saturated? Looking closely at the proof above, his would require
```{math}
|\brket{f_B}{f_A}|^2 = \brket{f_A}{f_A}\brket{f_B}{f_B} = \frac{1}{4} \vev{C}^2 + (\text{Re}\brket{f_B}{f_A})^2 = \frac{1}{4}\vev{C}^2
```
By the Schwarz inequality, this means that $\ket{f_A} = \beta \ket{f_B}$. If we then demand that $(\text{Re}\brket{f_B}{f_A})^2 = 0$ as required above, this means that $\beta$ is pure imaginary, $\beta = i \lambda$ for $\lambda$ real. 

### Example: spin-half

As a simple example, consider measuring $S_x, S_y$ in a spin-$\half$ system. Here $[S_x,S_y] = i \hbar S_z$. Now if the state is $\ket{+,x}$ you can show that $(\Delta S_x)^2 = 0$, $(\Delta S_y)^2 = \frac{\hbar^2}{4}$, $\vev{S_z} = 0$. On the other hand, if we choose $\ket{\psi} = \ket{+,z}$, $(\Delta S_x)^2 = (\Delta S_y)^2 = \frac{\hbar^2}{4}$, and $\vev{Sz} = \frac{\hbar}{2}$. Here the inequality is in fact saturated, which it does not in general have to be.

### Example: particle on a line

The classic example is the psotion-momentum uncertainty principle. As we have shown, $[{\hat x},{\hat p}] = i\hbar$. The *Heisenberg Uncertainty Principle* is:
```{math}
(\Delta x)(\Delta p) \geq \frac{\hbar}{2}
```
in other words, tehre is *no* circumstance in which we can sepcify both $x, p$ with infinte precision. Of we specify $x$ with complete precision, then $\Delta p$ must be infinite. (And thus the kinetci energy would have to be infinite, which is why one could never actually prepare such a state!). Similarly, if we psecify $p$ with infinite precision, $x$ has infinite variance, as is make clear from the associated wavefunction
```{math}
\brket{x}{p} = \frac{1}{\sqrt{2\pi \hbar}} e^{i p x/\hbar}
```

An interesting question is, what state *saturates* the uncertainty? We need
```{math}
({\hat p} - \vev{p})\ket{\psi} = i\lambda({\hat x} - \vev{x})\ket{\psi}
```
wheer $\ket{\psi}$ is specified by the wavefunction $\psi(x)$. Given what we know about the action of ${\hat p}, {\hat x}$ on this wavefunction, we can write this as a differential equation
```{math}
\frac{\hbar}{i} \frac{\del}{\del x} \psi - \vev{p}\psi =  i \lambda(x - \vev{x})\psi
```
This is a differential equation we can solve; the solution is
```{math}
\psi(x) = A e^{i\vev{p}x/\hbar} e^{-\frac{\lambda}{2\hbar}(x - \vev{x})^2}
```
Thsi is a Gaussian wavepacket modulated by a sinusoid. The width of the wavpacket is proportional to $\sqrt{\frac{\hbar}{\lambda}}$. 
