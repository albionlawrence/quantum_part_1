# First-order TDPT

![Sorry my kid is watching Star Wars 7-8-9 right now](fo.png)

Let us consider the transition amplitude between eigenstates of $H_0$ $\ket{i}$ and $\ket{f}$. At first order in perturbation theory, the transition amplitude is
```{math}
\begin{align}
{\tilde c}_{f} & = \bra{f}\left({\bf 1} - \frac{i\eps}{\hbar} \int_0^t dt' V_I(t')\right) \ket{i}\\
& = \delta_{fi} - \frac{i\eps}{\hbar} \int_0^t dt' \bra{f} V_I(t') \ket{i}\\
& = \delta_{fi} - \frac{i\eps}{\hbar} \int_0^t dt' \bra{f} e^{i H_0 t/\hbar} V(t) e^{- i H_0 t/\hbar} \ket{i} \\
& =  \delta_{fi} - \frac{i\eps}{\hbar} \int_0^t dt' e^{i (E_f - E_t) t/\hbar} \bra{f} V(t) \ket{i} \\
& =  \delta_{fi} - \frac{i\eps}{\hbar} \int_0^t dt' e^{i \omega_{fi} t} \bra{f} V(t) \ket{i}
\end{align}
```
Here $V(t)$ without the subscript refers to the Schroedinger picture operator, and $\omega_{fi} = \frac{E_f - E_i}{\hbar}$ has units of frequency.

At this point we need to know the time dependence of $V$ to go further. We will consider two cases: constant and harmonic time dependence. We will not in the end compute the precise matrix elements of $V$; in this sense we are after kinematic information, based on general facts about the time dependence of $V$ and the spectrum of $H_0$.

## Constant perturbations

If $V$ is constant, the integration is straightforward:
```{math}
{\tilde c}_{f} = \delta_{fi} - \frac{\eps}{\hbar\omega_{fi}} \left(e^{i\omega_{fi}} - 1\right) V_{fi}
```
where $V_{fi} = \bra{f} V \ket{i}$.

Let us first consider the case $f = i$. In this case, the denominator and the numerator of the second term vanish. Expanding the exponential in a power series in $\omega_{fi} t$, we keep the one nonvanishing term (after dividing by the denominator) to find:
```{math}
{\tilde c}_{ii}(t) = 1 - \frac{i\eps t}{\hbar} V_{ii}
```
Now
```{math}
	P_{ii} = |{\tilde c}_i|^2 = 1 + \frac{\eps^2 t^2}{\hbar^2} V_{ii}^2\ ,
```
and we can show that the second order correction will also give a $\cO(\eps^2)$ contribution to the probability, so we can say no more at this stage.

For $f \neq i$, we have
```{math}
:label: fo_coeff
{\tilde c}_f(t) = - \frac{\eps}{\hbar\omega_{fi}}  \left(e^{i\omega_{fi}} - 1\right) V_{fi}
```
Since there is no $\cO(1)$ term, the second order correction will give a $\cO(\eps^3)$ correction to the probability. At $\cO(\eps^2)$ in $P_{fi}$, the first order calculation {eq}`fo_coeff` is sufficient, and we have:
```{math}
:label: trans_prob
P_{f\neq i}(t) = \frac{\eps^2}{\hbar^2} \big| \frac{\sin^2 \left(\frac{\omega_{fi} t}{2}\right)}{\left(\frac{\omega_{fi}}{2}\right)^2}\big|^2 |V_{fi}|^2
```

If we have a discrete set of states separated by energy gaps $\Delta$ larger than the energy resolution $\delta$ of our detector, we can observe this sinusoidal behavior. However, this is not always the case. If we are studying, for example, the decay of a particle such as the classic beta decay process $n \to p + e + {\bar{\nu}}_e$, the final state is typically part of a continuum or near-continuum, due to all of the final possible momenta of the final decay products. In this case, in general $\delta \gg \Delta$, and we must sum over all final states in our detector. As we will see, this changes the time dependence of the transition probability and yields a constant transition rate.

Next, let us examine the ratio $\sin^2(\omega t/2)/(\omega^2/2)$. As $\omega \to 0$, this grows as $t^2$. For large $t$, there is a central peak with its first zero at $\omega = 2\pi/t$ and subsequent zeros at $\omega = 2n\pi/t$ where $n$ is any integer. Thus the central peak has height $t^2$ and width $1/t$, so integrations over this peak will scale as $t$. The subsequent peaks are order $1/\omega\sim 2n \pi/t$ in height and order $2\pi/t$ in width and contribute little at large $t$. The dominant transitions will be near $E_f \sim E_i$. In the example of particle decay this is as expected; energy is conserved and the final decay product haas the same energy as the initial decay product, up to the uncertainty due to observations over a finite time. The observed transition probability is thus
```{math}
:label: inclusive_prob
P_{i \to \{f\}} \sim \frac{\eps^2}{\hbar^2} \int_{E_i - \delta/2}^{E_i + \delta/2} \rho(E_f) dE_f \big| \frac{\sin^2 \left(\frac{\omega_{fi} t}{2}\right)}{\left(\frac{\omega_{fi}}{2}\right)^2}\big|^2 |V_{fi}|^2
```
The factor of $\rho(E_f)$ needs special mention. In the case that the spectrum is discrete,
```{math}
\rho(E) = \sum_n \delta(E - E_n)
```
where $E_n$ are the energies of the final states. This has dimensions of inverse energy. As the final states become finely spaced, we can approximate $\rho(E)$ as a continuous function: $\rho(E) dE$ is then the number of states between $E, E + dE$,

Now, we assume that $\rho(E)$ and $V_{ni}$ are smoothly varying as a function of the final states. Thus, they are essentially constant within the central peak of the integrand of {eq}`inclusive_prob`, and we can pull them out of the integral. Furthermore, since the first ratio in the integrand dies off rapidly with $E/\hbar$, we can extend the range of the integral to $[-\infty,\infty]$ to good approximation. The resulting integral is now doable analytically, and we have
```{math}
P_{i\to \{f\}} = \frac{2\pi t\eps^2}{\hbar} \rho(E_f) |V_{fi}|^2
```
where $E_f = E_i$. This grows linearly with $t$; at some point it ceases to be small, and we expect perturbation theory to break down. However, the transition *rate* is constant and small:
```{math}
:label: fermi_gr
\Gamma_{i\to \{f\}} = \frac{d P_{i\to \{f\}}}{dt} = \frac{2\pi\eps^2}{\hbar} \rho(E_f) |V_{fi}|^2
```
This formula is known as *Fermi's Golden Rule*; all of the kinematics are contained in the prefactor and the density of states, once this is known a measurement will yield $|V_{ni}|^2$ (assuming that is the object for which we have a theory we wish to test).

We should always be careful with this rule because it is based on a set of assumptions:

1. The detector energy resolution $\delta$ is large compared to the energy gap $\Delta$ between states.
2. The time $t$ is long enough that energy is conserved within the detector resolution. 
3. The time $t$ is *short* enough that the energy uncertainty is larger than the level spacing.

In fact, items (2) and (3) imply (1), and can be encapsulated as:
```{math}
\delta \gg \frac{2\pi \hbar}{t} \gg \Delta
```

### Example: radioactive decay

Let us consider the process 
```{math}
(nucleus) \to (nucleus)' + (light\ particle)
```
where the nuclei are heavy and initially stationary, and the final decay momentum is small enough that the final state of the nucleus can also be considered as stationary. In this situation we ignore momentum conservation, and assume that the kinetic energy of the final product is equal to the difference of the rest masses of the initial and final states:
```{math}
\frac{\hbar^2 {\vec k}^2}{2 m_{lp}} = m_{nu}c^2 - m_{nu'}c^2 - m_{lp} c^2 \ll m_{nu} c^2\ , m_{nu'} c^2
```
where $m_{lp}$ is the mass of the light particle, and $m_{nu}, m_{nu'}$ are the masses of the initial and final nuclei. We are assuming of course that $m_{lp} \ll m_{mu}, m_{nu'}$.

If the interactions that cause this decay are rotationally invariant, we expect that the particles can be emitted in any direction. A detector places far from the initial nucleus will have an angular resolution
```{math}
\Delta\Omega = \sin\theta \Delta\Theta\Delta\phi
```
where the detector is placed at $(\theta,\phi)$ in spherical coordinates, and $\Delta\theta, \Delta\phi$ are the resolution in each direction. $\Delta\Omega$ is known as a *solid angle*, equal to the area covered by the detector resolution divided by the distance $r^2$ from the origin. Now Fermi's Golden Rule gives the decay rate as a function of $\rho(E_f)$ and $|V_{ni}|^2$. The latter depends on the details of the relevant nuclear forces; we will take this as a thing we wish to measure to either test a theory or provide insight towards the formulation of a theory. To extract this from a decay rate, we need to know $\rho$. 

Now, thefinal states are labeled by the wavenumber (or momentum) of the light particle, within the approximations we are using here. We can start by assuming the system is in a bvery large box with sides of length $L$ and volume ${\cal V} = L^3$, so that the wavenumber is ${\vec k} = \frac{2\pi {\vec n}}{L}$. One can count the number of states within a box in wavenumber space with size $d{\vec k}$, located at ${\vec k}$; this is a standard textbook calculation or you can do it yourself. The result is:
```{math}
\frac{number\ of\ states}{unit\ volume} = \frac{d^3 k}{(2\pi)^3} = \frac{k^2 dk d\Omega}{(2\pi)^3}
```
In the latter equality we have considered the case of a region ir the range $k, k + dk$ subtended by solid angle $d\Omega = \sin\theta d\theta d\phi$, written in spherical coordinates in $k$ space. To convert this to $\rho(E)$ we wane to know the number of states per unit energy. Now we have
```{math}
k = \sqrt{\frac{2m E_f}{\hbar^2}} ; dk = \sqrt{\frac{m}{2\hbar^2 E_f}} dE_f
```
Thus,
```{math}
\frac{number\ of\ states}{unit\ volume} = \frac{\sqrt{2 m^3 E_f}}{(2\pi \hbar)^3} dE d\Omega
```
To find $\rho = \frac{number\ of\ states}{dE}$, we integrate this over the volume, to find:
```{math}
\rho(E_f = m_{nu}c^2 - m_{nu'} c^2 - m_{lp} c^2) = \frac{{\cal V}^3 \sqrt{2 m^3}}{(2\pi \hbar)^3} \sqrt{ m_{nu}c^2 - m_{nu'} c^2 - m_{lp} c^2}d\Omega
```

Now, using Fermi's Golden Rule, the transition rate per unit volume per unit solid angle is:
```{math}
\frac{d\Gamma}{d\Omega} = \frac{{\cal V} (2m^3)^{1/2}\eps^2}{(2\pi)^2 \hbar^4} \sqrt{ m_{nu}c^2 - m_{nu'} c^2 - m_{lp} c^2} |V_{fi}|^2
```
In general the matrix element $V_{ni}$ will scale as ${\cal V}^{-1/2}$, due to the standard normalization of the plane wave states of the light particle, so that this expression is independent of the volume.

## Harmonic perturbation

Another standard setup is to drive the system with a perturbation varying with definite frequency:
```{math}
V(t) = e^{\eta t} \left(A e^{i\omega t} + A^{\dagger} e^{-i\omega t}\right)
```
here we have added the growing exponential because we will assume that we start the driving as $t \to -\infty$ and turn on the interaction very slowly. This will simplfy some of the mathematics but is also not always a terrible approximation.

We are going to make use of teh notation $A_{fi} = \bra{f}A\ket{i}$, $A^{\dagger}_{fi} = \bra{f}A^{\dagger}\ket{i}$. We should be careful to note that $A^{\dagger}_{fi} = (A_{if})^*$. 

Now for transitions to states orthogonal to the initial state, we have
```{math}
\begin{align}
{\tilde c}_f(t) & = - \frac{i\eps}{\hbar} \int_{-\infty}^t dt' \left(e^{i (\omega_{fi} + \omega - i\eta) t'} A_{fi} + e^{i (\omega_{fi} - \omega - i\eta) t'} A^{\dagger}_{fi}\right)\\ 
& = - \frac{\eps}{\hbar} \left[ \frac{e^{i(\omega_{fi} + \omega - i\eta)t}}{\omega_{ni} + \omega - i\eta} A_{fi} +   \frac{e^{i(\omega_{fi} - \omega - i\eta)t}}{\omega_{ni} - \omega - i\eta} A^{\dagger}_{fi}\right]
\end{align}
```
Squaring this to get the probability, we find:
```{math}
\begin{align}
P_{i\to\{f\}} & = |{\tilde c}_f|^2 \\
& = \frac{\eps^2}{\hbar^2} \left\{ \frac{|A_{fi}|^2 e^{2\eta t}}{(\omega + \omega_{fi})^2 + \eta^2} +  \frac{|A^{\dagger}_{fi}|^2 e^{2\eta t}}{(\omega - \omega_{fi})^2 + \eta^2} \right.\\
& \qquad \left. \frac{A_{fi}^2 e^{2i\omega t + 2\eta t}}{(\omega + \omega_{fi} - i\eta)(\omega - \omega_{fi} - i\eta)} + c.c. \right\}
\end{align}
```
Now the terms in the second line oscillate with requency $2\omega$. If we assume that the temporal resolution of the detector is of order $n$ periods of this oscillation, then we should integrate the final probability over the resolution time; the oscillating terms will vanish. Once again, we always need to be careful about ourt assumptions as regards the physical setup of and capabilities of our experiment!

We are left with integrating the first two terms over this resolution time. IN fact we will integrate the decay rate:
```{math}
{\bar\Gamma} = \frac{\omega}{2\pi n} \int_0^{2\pi n/\omega} dt' \frac{dP_{i\to\{n\}}}{dt}
```
Now
```{math}
\frac{d}{dt} \frac{e^{2\eta t}}{(\omega + \omega_{fi})^2 + \eta^2} =  \frac{2\eta e^{2\eta t}}{(\omega + \omega_{fi})^2 + \eta^2}
```
As $\eta \to 0$, 
```{math}
\lim_{\eta \to 0} \frac{2\eta}{w^2 + \eta^2} = \pi \delta(w)
```
Thus,
```{math}
{\bar\Gamma} = \frac{2\pi \eps^2}{\hbar^2}\left[|A_{ni}|^2 \delta(\omega + \omega_{ni}) + |A^{\dagger}_{ni}|^2 \delta(\omega - \omega_{ni})\right]
```
Writing the delta functions in terms of energies,
```{math}
\delta(\omega \pm \omega_{ni}) = \hbar \delta(E \pm (E_n - E_i))
```
where $\hbar\omega = E$. Finally, if we make a transition into a continuum of final states, we sum over all such final states. If furthermore the energy uncertainty is large compared to the level spacing and the detector resolution is larger still, the same assumptions apply as before; we replace the sum over final states with an integral, and the delta function is replaced by the density of states. We are left with two decat rates, depending on whether the final state has higher energy than the initial state (absorption of energy) or smaller energy (emission of energy):
```{math}
\begin{align}
{\bar\Gamma}^{abs}_{i\to\{n\}} & = \frac{2\pi \eps^2}{\hbar} |A_{ni}|^2 \rho(E_f)\big|_{E_f = E_i + \hbar\omega} \\
{\bar\Gamma}^{em}_{i\to\{n\}} & = \frac{2\pi \eps^2}{\hbar} |A^{\dagger}_{ni}|^2 \rho(E_f)\big|_{E_f = E_i - \hbar\omega}
\end{align}
```

As a final note, note that $|A^{\dagger}_{ni}|^2 = |A_{in}|^2$. This means that
```{math}
\frac{emission\ rate\ i \to n}{\rho(E_n)} = \frac{absorption\ rate\ n\to i}{\rho(E_i)}
```
This is a statement of *detailed balance* and is a result of the Hermiticity of the Hamiltonian. It is important in situations such as atoms in a bath of electromagnetic radiation, thermal equilibrium. 
