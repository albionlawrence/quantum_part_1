# Particles on a line

Here I am going to build up particles on a continuous line by starting wth partciles hopping between sites on a lattice. This latter picture is important for understanding electrons in a metal (especially in the "tight binding" approximation, in which they are strongly bound to the atomic sites and couple to adjacent sites only very weaky). Also, dealing with subtleties in a continuous theory by discretizing it is a time-honored method in theoretical physics.

## Particles on a lattice

### Position basis

We will start by considering particles on a circle with radius $R$ (meaning that $x equiv x + 2\pi R$). We will model this with $N$ discrete points that the particle can live on. Let the particles be spaced by an distance $\epsilon$, so that $N\epsilon = 2\pi R$. We can build a Hilbert space for a particle on this 1d lattice by stating that the state $\ket{k}$ corresponds to a particle at site $k\in \{0,\ldots, N-1\}$. We can define these are orthonormal states so that $\brket{k}{l} = \delta_{kl}$. Finallly, we can extend these dinces so that $k + N$ is the same as site $k$ (this is reminding us that the particle lines on a circle).

With this, the Hilbert space is $\CC^N$. A general state can be written as
```{math}
:label: lattice_state
\ket{\psi} = \sum_k \psi_k \ket{k} \equiv \sum_k \psi(x_k) \ket{x_k}
```
where on the far right hand side we have relabeled the states by defining
$x_k \equiv \epsilon k$. Here $\psi(x_k)$ is a complex function on the lattice, which we can call a *wave function*. 


The dual vector is
```{math}
:label: lattice_dual
\bra{\psi} = \sum_k \bra{x_k} \psi^*(x_k)
```
and the inner product can be written as
```{math}
:label: lattice_ip
\brket{\chi}{\psi} = \sum_{k,l} \bra{x_k} \chi^*(x_k) \psi(x_l) \ket{x_l} = \sum_k \chi^*(x_k) \psi(x_k)
```
where in the last equality we used $\brket{x_k}{x_l} = \delta_{kl}$. This means that if $\brket{\psi}{\psi} = 1$, 
```{math}
:label: norm_condition
\sum_k |\psi(x_k)|^2 = 1
```

### Dual Fourier/momentum basis

We can also write the following basis for $\CC^N$:
```{math}
:label: momentum_lattice
\ket{\phi_m} = \frac{1}{\sqrt{N}} \sum{k = 0}^{N-1} e^{\frac{2\pi i m k}{N}} \ket{x_k}
= \frac{1}{\sqrt{N}} \sum{k = 0}^{N-1} e^{\frac{i m x_k}{R}} \ket{x_k}
```
where $m \in \{0,2,\ldots N-1\}$. This is of the form {eq}`lattice_state` with $\psi(x_k) = \frac{1}{\sqrt{N}} e^{i m x_k/R} \equiv \phi_m(x_k)$. In other words, the wavefunction is a pure oscillating exponential.

The states $\ket{\phi_m}$ are orthonormal. Using {eq}`lattice_ip`
```{math}
:label: mom_ortho
\brket{phi_m}{\phi_n} = \frac{1}{N} \sum_k e^{2\pi i (n-m)k/N} = \delta_{m,n}
```
The last equality can be argued for as follows. If $n = m$, it is clear that the answer is $1$. If $n\neq m$, we can use the identity
```{math}
\sum_{k = 0}^{N-1} x^k = \frac{1 - x^N}{1 - x}
```
where $x = e^{2\pi i (n-m)/N}$.
Since $x^N = 1$, and the denominator is nonvanishing for $x \neq 1$, this sum vanishes, proving {eq}`mom_ortho`. 

To get some intuition for this basis, let us rewrite $\ket{\psi} = \sum_k \psi(x_k) \ket{k}$. Since $\ket{\phi_m}$ is a complete basis, we have the following resolution of the identity:
```{math}
{\bf 1} = \sum_{m=0}^{N-1} \ket{\phi_m}\bra{\phi_m}
```
Thus
```{math}
\ket{\psi} = \sum_k \psi(x_k) \sum_m \ket{\phi_m}\brket{\phi_m}{k}
```
But 
```{math}
\brket{\phi_m}{k} = \frac{1}{\sqrt{N}} e^{-2\pi i m k/N}\ .
```
Thus, 
```{math}
\ket{\psi} = \sum_m \left(\frac{1}{\sqrt{N}}\sum_k \psi(x_k) e^{-2\pi i m k/N}\right)\ket{\phi_m}
```
Now 
```{math}
:label: discrete_ft
{\tilde \psi}(m) = \frac{1}{\sqrt{N}} \sum_k \psi(x_k) e^{-2\pi m k/N}
```
is simply the discrete Fourier transform of $\psi(x_k)$, and we have
```{math}
\ket{\psi} = \sum_m {\tilde\psi}(m) \ket{\phi_m}
```
That is, the coefficients of the expansion in the basis $\ket{phi_m}$ are the Fourier coefficients for $\psi(x_k)$. Note that {eq}`discrete_ft` can be reversed:
```{math}
:label: discrete_ift
\psi(x_k) = \frac{1}{\sqrt{N}} \sum_m {\tilde\psi}(m) e^{2\pi i m k/N}
```

### Operators

There are two operators of interest here. The first is the *position operator*, which can be defined as
```{math}
:label: po_def
{\hat x} \ket{x_k} = x_k \ket{x_k}
```
That is, the position states are eigenstates of ${\hat x}$. It is clear that ${\hat x}\ket{\psi} = \ket{x\psi}$, *so long as we take $\psi$ to be a function on the lattice $x_k \in \{0,\eps,\ldots (N-1) \eps = 2\pi R - \eps\}$. We thus have to be a little careful here. So far $\psi(x_k)$ is just a collection of numbers. We have stated that $k = N$ can be identified with $k = 0$. However for ${\hat x}$ to be well-defined, it must give the same answer acting on $\ket{0}$, $\ket{x_N = 2\pi R}$. 

Now if we measure ${\hat x}$, the possible eigenvalues are $x_k$. We can ask the question, if we measure the position of the particle, with what probability will we find the result $x_k$? The corresponding projection opeator is $\CP = \ket{x_k}\bra{x_k}$, so the probability $p(x_k)$ is:
```{math}
p(x_k) = \bra{\psi}\CP\ket{\psi} = |\brket{x_k}{\psi}|^2 = |\psi(x_k)|^2
```
we call $\psi(x_k)$ the *amplitude*; its absolute value squared is the probability for the particle to reside at $x_k$.

Another operator is the one for which $\ket{\phi_m}$  are eigenstates with eigenvalues $\propto m$. Anticipating an eventual answer, we define the operator ${\hat p}$ such that
```{math}
{\hat p} \ket{\phi_m} = \frac{\hbar m}{R} \ket{\phi_m} \equiv p_m \ket{\phi_m}
```
Note that $\hbar m/R$ has the dimensions of momentum. We will see over time that this identification makes sense. We call $m/R$ the *wavenumber* of the particlein the state $\ket{\phi_m}$, and we call $2\pi(R/m) = \lambda_m$ the *wavelength*. To see why, we can write
```{math}
\phi_m(x_k) = \frac{1}{\sqrt{N}} e^{2\pi i m x_k/(\eps N)} = e^{i m x_k/R}
= e^{i p_m x_k/\hbar}
```
It is clear that this function is periodic in $x_k$ with period $2\pi R/m = \lambda_m$.

This relationship between wavelength and momentum goes back to de Broglie; even before the development of wave mechanics {\it a la}\ Schroedinger, he proposed that electrons had wave-like properties and one could assign a wavelength equal to $\lambda = 2\pi \hbar/p$, which we call the *de Broglie wavelength*. In our treatment the association of a particular state $\ket{\phi_m}$ of a particle with a wavelength is somewhat natural; the question for us will be, why we might associate its inverse, properly scaled, with a momentum. For now we will assert it, supported by the dimension of this quantity. We will show that when we consider particle dynamics, our definition yields something that behaves as a momentum should.

## Continuum limit

### Particles on a circle

Let us next consider the limit $\eps\to 0$, $N \to \infty$, $\eps N = 2\pi R$ fixed. (We will consider $R \to\infty$ later). Starting with $\eps$ finite but very small, we can write inner products as
```{math}
:label: inner_limit
\begin{align}
\brket{\chi}{\psi} & = \sum_k \chi^*(x_k) \psi(x_k) \\ 
& = \eps \sum_k \frac{1}{\sqrt{\eps}} \chi^*(x_k) \frac{1}{\sqrt{\eps}} \psi(x_k)\\
& \xrightarrow[\eps\to 0]{} \int_0^{2\pi R} dx \chi^*(x) \psi(x)
\end{align}
```
where we have rescaled the wavefunctions 
```{math}
:label: wf_rescaling
\frac{1}{\sqrt{\eps}} \psi(x) \xrightarrow[\eps\to 0]{} \psi(x)
```
Note that the rescaled wavefunctions have dimensions of $1/\sqrt{length}$. Under this rescaling, the probability that a particle can be found at position $x$ becomes:
```{math}
|\psi(x_k)|^2 = \eps \big| \frac{1}{\sqrt{\eps}} \psi(x_k)\big|^2 \to \eps |\psi(x)|^2 \equiv dx |\psi(x)|^2
```
Under this rescaling, $dx|\psi(x)|^2$ is dimensionless and can be interpreted as a probability -- more specifically, the probability for the particle to be within an interval $dx$ of the position $x$. The quantity $|\psi(x)|^2$ has dimensions of $1/(length)$, and so can be considered as a (one-dimensional) probability density. 

The position eigenstates are problematic in this limit. We would like to replace them with states labeled by the continuous variable $x$. However, rewriting the state
```{math}
:label: continuum_state
\begin{align}
\ket{\psi} & = \sum_k \psi(x_k)\ket{x_k}\\
& = \eps \sum_k \frac{1}{\sqrt{\eps}} \psi(x_k) \frac{1}{\sqrt{\eps}} \ket{x_k}\\
& \xrightarrow[\eps \to 0]{} \int_0^{2\pi R} dx \psi(x) \ket{x}
\end{align}
```
where we define 
```{math}
:label: contin_pos_eigen
\frac{1}{\sqrt{\eps}} \ket{x_k} \xrightarrow[\eps\to 0]{} \ket{x}
```
Now the position states (I will be careful for now not to call them eigenstates) $\ket{x}$ does not, strictly speaking, exist; it is not a vector in the Hilbert space. In particular it is clear that the norm is $1/\eps \to \infty$. The inner product in this limit is
```{math}
:label: pos_eigen_ip
\frac{1}{\sqrt{\eps}} \bra{x_k} \frac{1}{\sqrt{\eps}} \ket{x_l} = \frac{1}{\eps} \delta_{kl} \xrightarrow[\eps \to 0]{} \brket{x}{x'} = \delta(x - x')
```
where $\delta(x - x')$ is the Dirac delta function. Recall that $\delta(x)$ vanishes for $x\neq 0$, is infinite at $x = 0$, and satisfies the constraint
```{math}
:label: ddf_norm
\int_{-L}^L dx\delta(x) = 1
```
for any finite positive $L$. This matches the fact that $\eps \sum \to \int dx$. so that
```{math}
\eps \sum_{k=1}^N \frac{\delta_{kl}}{\eps} = 1 \to \int_0^{2\pi R} dx \delta(x - x')
```

Although the position states are not actually states in the Hilbert space, we can with some care use them consistently. The essential point is that using the above rules, if we define our state as
```{math}
\ket{\psi} = \int_0^{2\pi R} dx \psi(x) \ket{x}
```
then using {eq}`pos_eigen_ip`
```{math}
:label: continuous_norm
\brket{\chi}{\psi} = \int dx dy \chi^*(x) \brket{x}{y} \psi(y) = \int dx \chi^*(x) \psi(y)
```
and in particular,
```{math}
:label: cont_norm_two
\brket{\psi}{\psi} = \int_0^{2\pi R} dx |\psi(x)|^2
```
So in the continuum limit, the Hilbert space becomes the space of integrable functions on the circle $\psi(x + 2\pi R) = \psi(x)$. The wavefunctions can be extracted from the states via the formula 
```{math}
\psi(x) = \brket{x}{\psi}
```

For finite $R$, the momentum basis is, however, still well-defined. Using the limits above,
```{math}
:label: cont_mom_basis
\ket{\phi_m} = \frac{1}{\sqrt{N}} e^{\frac{2\pi i m k}{N}} \ket{k} \xrightarrow[\eps\to 0]{} \frac{1}{\sqrt{2\pi R}} \int_0^{2\pi R} dx e^{i m x/R}\ket{x}
```
The corresponding wavefunction is
```{math}
\phi_m(x) = \frac{1}{\sqrt{2\pi R}} e^{i m x/R} \equiv \frac{1}{\sqrt{2\pi R}} e^{i p_m x/\hbar}
```
Now we have taken $m \in \{0,\ldots,N-1\}$. As $N\to \infty$ it appears that $m$ can become infinitely large and always positive. On the other hand, sin $m$ always appears in exponentials, we can equivalently write $m = N - k$ and $m = -k$. Thus, it makes just as much sense to let $m \in \{-\frac{N}{2} +1,\ldots \frac{N}{2}\}$ if $N$ is even, or $m \in \{-\frac{N-1}{2},\ldots,
\frac{N-1}{2}\}$. In the limit $N \to \infty$, the states $\ket{\phi_m}$ give a resolution of the identity
```{math}
{\bf 1} = \sum_m \ket{\phi_m}\bra{\phi_m}
```
We can thus write
```{math}
:label: dual_reps
\begin{align}
\ket{\psi} & = \int_0^{2\pi R} dx \psi(x) \ket{x} \\
& = \sum_{m = - \infty}^{\infty} \int_0^{2\pi R} dx \psi(x) \ket{\phi_m}\brket{\phi_m}{x}\\
& = \sum_{m = -\infty}^{\infty} \int_0^{2\pi R} dx \frac{1}{\sqrt{2\pi R}} e^{-i m x/R} \psi(x) \ket{m}\\
& \equiv \sum_m {\tilde \psi}(m) \ket{m}
\end{align}
```
where 
```{math}
{\tilde \psi}(p) = \frac{1}{\sqrt{2\pi R}} \int_0^{2\pi R} dx e^{-i m x/R} \psi(x)
```
is the Fourier transform of $\psi(x)$.

I have been careful not to call $\ket{x}$ position eigenstates. It is tempting to say that we have an operator ${\hat x}$ such that ${\hat x}\ket{x} = x\ket{x}$. This would meanthat ${\hat x}\ket{\psi} = \ket{x\psi}$. But if $\psi(x)$ is a periodic function, $x\psi$ is not. Thus our putative operator $x$ takes us out of the Hilbert space; it is not well defined. Nonetheless, it does make sense to ask whether the particle is or is not in a given position, or at least, in a given interval. We can define a projection operator by its action on wavefunctions:
```{math}
:label: position_projection
\CP_{x_0,\delta}\psi(x) = 
\begin{cases} 0 & \text{if}\ x < x_0 - \frac{\delta}{2}\\
\psi(x) & \text{if}\ x_0 - \frac{\delta}{2} < x < x_0 + \frac{\delta}{2}\\
0 & \text{if}\ x > x_0 + \frac{\delta}{2}
\end{cases}
```
It is clear that this is a projection operator: $\CP_{x_0,\delta}^2 = \CP_{x_0,\delta}$. We can also show that it is Hermitian by showing that
```{math}
\bra{\chi}\CP_{x_0,\delta} \ket{\psi} & = \brket{\chi}{\CP_{x_0,\delta}\psi}\\ & = \brket{\CP_{x_0,\delta}\chi}{\psi} = \bra{\chi} \CP^{\dagger}_{x_0,\delta} \ket{\psi}
```
This operator will jhave as eigenstates any wavefunction whose support is contained inetirely in the interval $[x_0 - \frac{\delta}{2}, x_0 + \frac{\delta_2}]$, for which it will have eigenvalue $1$. We can thus state that the probability ta particle in a state $\ket{\psi}$ is in this interval is
```{math}
\bra{\psi}\CP_{x_0,\delta}\ket{\psi} = \int_{x_0 - \frac{\delta}{2}}^{x_0 + \frac{\delta}{2}} dx |\psi(x)|^2
```
This is consistent with the discussion above in which we found $|\psi(x)|^2$ should be identified as a probability density.

We can tie this back to the statement that every observable has a spectral representation in terms of its eignevalues, by approximating $x$ via:
```{math}
{\hat x} \sim \sum_{n = - \infty}^{\infty} (n\eps} \PP_{n\eps,\eps} \xrightarrow[\eps \to 0]{} \int d\CP_{\lambda} \lambda
```
For now I offer the last limit as a sort of shorthand. This can be precisely defined, and the fact that we can wrepresent even unbounded operators ${\hat x},{\hat p}$ as such an integral is known as the *Spectral Theorem*.

On the flip side, the momentum operator defined by 
```{math} 
{\hat p}\ket{\phi_m} = \frac{\hbar m}{R} \ket{\phi_m}
```
is well defined. Here we will take $m \in \mathbb{Z}$. This acts in an interesting way on $\ket{\psi}$:
```{math}
\begin{align}
{\hat p}\ket{\psi} & = \sum_p p {\tilde \psi}(p) \ket{p} \\
& = \sum_p \int_0^{2\pi R} \frac{1}{\sqrt{2\pi R}} p e^{- i p x/\hbar} \psi(x)\ket{p}\\
& = \sum_p \int_0^{2\pi R}dx  \frac{1}{\sqrt{2\pi R}} \left(i\hbar \frac{\del}{\del x} e^{-i p x/\hbar}\right) \psi(x) \ket{p}\\
& = \sum+p \int_0^{2\pi R} dx \frac{1}{\sqrt{2\pi R}} e^{-ipx/\hbar} \frac{\hbar}{i} \frac{\del}{\del x}\psi(x) \ket{p}\\
& = \int dx_0^{2\pi r}  \frac{\hbar}{i} \frac{\del}{\del x}\psi(x) \ket{x}
\end{align}
```
where in the second to last line we integrated by parts to move the derivative acting on the exponential to one acting on $\psi$. In short, 
```{math}
:label: mom_def
{\hat p}\ket{\psi} = \ket{\frac{\hbar}{i} \frac{\del}{\del x} \psi}
```

### Particles on a line

Finally, we can take $R \to \infty$. This means the circle should move to the real line. Since the wavefunctions started as periodic, we can define the period as $[-\pi R,\pi R]$ before taking the limit. The resulting Hilbert space is equivalent to the space of functions that are integrable on this line; that is, the space of square-integrable functions, or $L^2(\CR)$. 

In this limit, the eigenstates of ${\hat p}$ also become ill-defined. The allowed values of momenta are $p = \frac{\hbar m}{R}$ for $m \in \CZ$. The momentum becomes continuous. One could try to stick with the eigenstates $\ket{\phi_m}$ and consider them as an orthogonal set, but as we will see, it is $p$ which is the physical variable. 

Returning to {eq}`dual_reps`, we can rewrite the third line as
```{math}
\ket{\psi} = \frac{\hbar}{R} \sum_m \int_{-\pi R}^{\pi R} dx \frac{1}{\sqrt{2\pi \hbar}} e^{- i p x/\hbar}\psi(x) \sqrt{\frac{R}{\hbar}} \ket{\phi_m}
```
If we take $R \to \infty$, $\frac{\hbar}{R} \sum_m \to \int_{-\infty}^{\infty} dp$. If we take $\lim_{R\to\infty} \sqrt{\frac{R}{\hbar}} \ket{\phi_m} \to \ket{p}$, then we can show that
```{math}
\begin{align}
\ket{\psi} & = \int_{-\infty}^{\infty} dp \int_{-\infty}^{\infty} dx \frac{e^{-i p x/\hbar}}{\sqrt{2\pi \hbar}} \psi(x) \ket{p}\\
& \equiv \int dp {\tilde\psi}(p)\ket{p}
\end{align}
```
and
```{math}
\brket{p}{q} = \delta(p - q)
```
where
```{math}
:label: ft_on_line
{\tilde \psi}(p) = \int_{-\infty}^{\infty} dx \frac{e^{-i p x/\hbar}}{\sqrt{2\pi \hbar}} = \brket{p}{\psi}
```
is the Fourier transform of the wavefunction. Note that for consistency, using ${\bf 1} = \int dx \ket{x}\bra{x}$, we can show that
```{math}
{\tilde \psi}(p) = \brket{p}{\psi} = \int dx \brket{p}{x}\brket{x}{\psi}
```
This is consistent with {eq}`ft_on_line` if 
```{math}
\brket{p}{x} = \frac{1}{\sqrt{2\pi \hbar}} e^{-i p x/\hbar}
```
In other words, the momentum eigenstates are purely oscillating exponential.
They are no longer normalizable. Nonetheless, we can define our states in terms of them, as with our position eiegnstates. A given function $\psi(x)$ can be represented in terms of its Fourier transform, and this Fourier transform can be written as the coefficient of $\ket{p}$ in an expansion of $\ket{psi}$ in momentum eigenstates. Inner products can also be written in either basis:
```{math}
\brket{\chi}{\psi} = \int dx \chi^*(x)\psi(x) = \int dp {\tilde \chi}^*(p){\tilde\psi}(p)
```

Since the functions we care about are no longer periodic, we can define both position and momentum operators ${\hat x}, {\hat p}$ such that $\hat{x}\ket{x} = x\ket{x}$, ${\hat p}\ket{p} = p \ket{p}$. Acting on more general states,
```{math}
\begin{align}
{\hat x}\ket{\psi} & = \ket{x\psi}\\
{\hat p}\ket{\psi} & = \ket{\frac{\hbar}{i}\frac{\del\psi}{\del x}}
\end{align}
```
While the periodicity issues no longer pertain, both of these operators can take a state out of the Hilbert space. If $\psi(x)$ dies off as $1/|x|$ for $x\to\infty$, for example, it will in general be square-integrable, but $x\psi(x)$ will not be. Similarly, if $\psi(x)$ is discontinuous, $\frac{\del \psi(x)}{\del x}$ will be infinite at the discontinuity, proportional to a delta function, and will not be square integrable. More precisely, these are not *bounded operators*. 

However, if we care careful about the questions we ask, we can get sensible answers. In particular, no realistic measurement of either $x,p$ will be made with perfect resolution. We saw the solution for asking for the probability that $x$ lies in some interval. The same will apply to measurements of $p$. $|{\tilde\psi}(p)|^2$ will be a probability density in momentum space. The probability to find a particle in a range of momenta $[p_1,p_2]$ will be
```{math}
p = \int_{p_1}^{p_2} dp |{\tilde\psi}(p)|^2
```
We have waved our hands a little in relating this, and the prior probability of finding the particle in a spatial region, to the original Born rule. In that case, pperators $A$ whose eigenstates form a discrete set could be represented as a sum over projection operators $\CP_a$ projecting onto subspaces of eigenstates of the operator with eigenvalue $a$. There is a more general *spectral theorem* that encompasses unbounded operators with continuous eigenvalues. The upshot gives us the probabilities we have discussed above for finding the particle in a finite range in position or momentum space.
