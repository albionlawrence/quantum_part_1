# The Axioms of Quantum Mechanics.

One can make a case that the best way to introduce quantum mechanics is to just jump right in. The rules are comparatively simple, if somewhat abstract. We will take that approach and then proceed to applying the rules to various examples. In this way we can build some intuition for how the rules work. 

A good reason for doing this is that the rules are very different from how we approach classical mechanics. Furthermore, they yield predictions that have withstood over a century of experimental tests. So perhaps we should just state what the rules are and get used to them. The infamous philosophivcal puzzles amount to: where do these rules come from? We will allude to these, and in coming lectures eliminate one class of possibilities.

I will state the rules in a somewhat different order and grouping as compared to Commins. (Also one of his rules can be derived as a consequence). It comes to the same in the end, and you should read both.

1. The space of physical states of a quantum system is a Hilbert space $\cH$. (COntrast with classical mechanics, for which the space of states is a *phase space* of positions and momenta). 

Some examples:
- For photons traveling with fixed direction and wavenumber, the space of photon polarizations is $\cH = \CC^2$.
- The spin states of neutrons, protons, and electrons are also described by $\cH = \CC^2$. Such particles are called "spin-$\half$" particles and there are many others! (Muons, tau leptons, neutrinos, quarks.)
- The states of a spinless, nonrelativistic particle in three dimensions is $\cH = L^2(\CR^3)$

2. Observable quantities are eigenvalues of (bounded) Hermitian operators. As a shorthand, we typically refer to the operators themselves as "observables", which I will do here. That is, for any quantity such as position, momentum, energy, polarization, or spin, there is an associated operator and the allowed results of a measurement are the eigenvalues of that operator. 

3. Given a state $\ket{\psi} \in \cH$, a measurement of an observable $A$ yields an eigenvalue $a$ with probability
```{math}
:label: born_rule
p(a) = \frac{\bra{\psi} \CP_a \ket{\psi}}{\brket{\psi}{\psi}}
```
This rule is sometimes called the *Born rule*. The resolution of the identity shown in {eq}`evector_resolution_identity` shows that these atre consistent probabilities:
```{math}
:label: sum_of_results
\sum_i p(a_i) = \sum_i \frac{\bra{\psi} \CP_{a_i} \ket{\psi}}{\brket{\psi}{\psi}} = \frac{\bra{\psi} \CP_{a_i}{\bf 1} \ket{\psi}}{\brket{\psi}{\psi}} = 1
```
For this reason, we often impose the requirement $\brket{\psi}{\psi} = 1$ on physical states. This amounts to scaling $\ket{\psi} \to \frac{1}{||\psi||}\ket{\psi}$. 

What do I mean by such a probability, in a practical sense? As some might know, there are two major interpretations of probability: the "Bayesian approach" in which the probability quantifies ones estimation of the likelihood of an event (eg, how much would you bet on $X$ happening?) and the "frequentist approach" in which the probability corresponds to the frequency that a given outcomes happens after repeated experiments. Practically it is this latter approach that one takes in testing a given prediction of probabilities. That is, one repeats an experiment $N$ times, and records the number of times $N(a)$ that a measurement yields result $a$. Then
```{math}
p(a) = \lim\limits_{N \to \infty} \frac{N(a)}{N}
```

The Born rule naturally yields a further result which Commins gives the status of an independent rule. Let us do a set of repeated experiments as above, in which we prepare a fixed state $\ket{\psi}$, measure some observable $A$, and ask what the *average* result is. For a finite number $N_{experiments}$ of experiments, we will denote this average as ${\overline A}$, which is:
```{math}
:label: operator_av
\begin{align}
{\overline A} & = \frac{1}{N_{experiments}} \sum_{experiments} a(experiment)\\
& = \frac{a N(a)}{N_{experiments}}
\end{align}
```
In the limit $N_{experiments} \to \infty$, we call ${\overline A}$ the *expectation values* of $A$, defnotes $\vev{A}$. This becomes (if we take $\brket{\psi}{\psi} = 1$)
```{math}
:label: operator_ev
\begin{align}
\vev{A} & = \lim\limits_{N_{experiments}\to\infty} \overline(A) \\
& = \sum_i p(a_i) a_i \\
& = \sum_i \bra{\psi} \CP_i \ket{\psi} a_i \\
& = \bra{\psi} \sum_i a_i \CP_i \ket{\psi}\\
& = \bra{\psi} A \ket{\psi}
\end{align}
```

The probabilistic nature of measurement is a big part of people's discomfort with quantum mechanics (cf Einstein's famous statement, "God does not play dice with the world"). Much of the work in searching for an interpretation of quantum mechanics comes from looking for an underlying deterministic framework that would yield such probabilities, perhaps via the existence of unobserved or "hidden" variables. The simple acceptance of this axiom and the following one as the true reality of the world is called the "Copenhagen interpretation". While I will present a powerful critique of/constraint on hidden variables theories shortly, I won't dwell much on this fascinating subject. The axioms have withstood the test of experiment and it is important to understand what is actually observed before diving into the philosophical side of the subject.

4. Immediately after a measurement corresponding to an observable $A$ yields the result $a$, the wavefunction "collapses" to the subspace of eigenvectors of $a$:
```{math}
:label: measurement_result
\ket{\psi} \to \frac{1}{\bra{\psi} \CP_a \ket{\psi}} \CP_a \ket{\psi}
```
This "collapse of the wavefunction" is the other mystery of quantum mechanics. How does this happen? For now we will take it as given, since this is what is actually seen in experiments.

My personal prejudice is that this is related to the fact that actual measurements involve coupling a large, complicated measuring device (well descvribed by classical physics) to a small quantum system. If I have time, we will model this process later once we have explored various quantum systems; it points to a plausible if very uncomfortable interpretation of the Born rule and collapse of teh wavefunction, known as the "Many Worlds Interpretation".

5. Absent external intervention through a measurement, the time evolution of an *isolated* quantum system is described by a unitary operator:
```{math}
:label: quantum_dynamics
\ket{\psi(t)} = U(t,t_0) \ket{\psi(t_0)}
```
where $t > t_0$ and $\ket{\psi(t)}$ is the quantum state of the system at time $t$. Unitarity means that $\brket{\psi(t)}{\psi(t)} = \brket{\psi(t_0)}{\psi(t_0)}$, so that $\ket{\psi(t)}$ continues to yield sensible probabilities. Note that what we mean by isolated actually takes osme careful work. For example, we will discuss the evolution of charged particles in an electromagnetic field, and take that filed to be described by some fixed background. In fact the field itself is a quantum system, and we cannot really treat the electron as isolated; one must specify the joint quantum evolution of the full system of field plus charged particle. Practically speaking we can ofetn ignore this issue and treat the electron as a quantum system whose dynamical evolution is specified by some particular operator $U(t,t_0)$. 

This rule implies a differential form of the dynamical equations which brings us a bit closer to what we are familiar with in classical mechanics. Given $\ket{\psi(t)}$, the state an infinitesimal time later is $\ket{\psi(t + \delta t)} = \ket{\psi(t)} + \delta t \frac{d}{dt} \ket{\psi(t)}$. Given the above evolution equations,
```{math}
\begin{align}
\frac{d}{dt} \ket{\psi(t)} & = \frac{d}{dt} U(t,t_0) \ket{\psi(0)}\\
& = \frac{d}{dt} U(t,t_0)U^{\dagger} U \ket{\psi(u)}\\
& = \frac{d}{dt} U U^{\dagger} \ket{\psi(t)}
\end{align}
```
Now since $U U^{\dagger} = {\bf 1}$, 
```{math}
:label: deriv_of_resolution
\frac{d}{dt} (U U^{\dagger}) = \frac{dU}{dt} U^{\dagger} + U \frac{d U^{\dagger}}{dt} = 0
```
or 
```{math}
\frac{dU}{dt} U^{\dagger} = - U \frac{d U^{\dagger}}{dt}
```
Now using $(AB)^{\dagger} = B^{\dagger} A^{\dagger}$, we know that 
```{math}
\left(\frac{dU}{dt} U^{\dagger}\right)^{\dagger} = U \frac{d U^{\dagger}}{dt} = - \frac{d U}{d t} U^{\dagger}
```
where the last equality comes from {eq}`deriv_of_resolution`. If we define
```{math}
:label: ham_def
H(t) = i \hbar \frac{d U}{dt} U^{\dagger}
```
with $\hbar$ having units of $(\text{energy}\times\text{time})$, then $H$ is a Hermitian operator with units of energy, and the system satisfies the *time-dependent Schroedinger equation* 
```{math}
:label: TDSE
i\hbar \frac{d}{dt} \ket{\psi(t)} = H(t) \ket{\psi(t)}
```
We will identify $H$ with the observable corresponding to the energy of the system. I will simply assert at this point that in situations in which classical mechanics can be expected to apply (the "classical limit"), this identification will be consistent with the expected classical dynamics.


The dynamics of the system are completely specified by $H(t)$, or equivalently by $U(t)$; given $\ket{\psi(t_0)}$, we know $\ket{\psi(t)}$ for all future times. In this sense quantum dynamics is *completely deterministic and causal*. It is only the introduction of the measurement hypothesis which introduces any nondeterminism into the theory. Again, we might relax even about this if we recall that a measuring device is a complicated object with over $10^{23}$ atoms well described by classical mechanics, and before we really become concerned about the axioms we should understand whether measurement can be well modeled via unitary quantum dynamics. But again, for now we can just accept that the axioms have served us well for over a century, providing a foundation on which modern physics, chemistry, and engineering (atomic, nuclear, and particle physics, "hard" condensed matter physics, superfluids, modern electronics, materials science, and so on and so on.)

Two more comments. 

A. Since we often in practice measure expectation values of operators, 
```{math}
:label: ev_time
\vev{A}(t) = \bra{\psi(t_0)} U^{\dagger}(t,t_0) A U(t,t_0) \ket{\psi}
```
we can adopt an equivalent formalism known as the *Heisenberg picture* in which the states do not evolve, but 
```{math}
A_H = U^{\dagger}(t,t_0) A U(t,t_0)
```
We sometimes denote the original operator as the *Schroedinger picture* $A_S$ and $\ket{\psi(t)}$ as the state in the Schroedinger picture. If $A_S(t)$ itself has some time dependence (eg you are measuring polarization along some axis which is changing with time because the photon is moving through a bent fiber optic cable or some such), then we can write
```{math}
:label: heisenberg_evolution
\begin{align}
\frac{d A_H}{dt} & = \frac{d U^{\dagger}}{dt} A_S U + U^{\dagger} \frac{\del A_S}{\del t} U + U^{\dagger} A_S \frac{dU}{dt}\\
& = \frac{d U^{\dagger}}{dt} U U^{\dagger} A_S U + U^{\dagger} A_S U U^{\dagger} \frac{dU}{dt} + U^{\dagger} \frac{\del A_S}{\del t} U\\
& = \frac{i}{i\hbar} [A_H(t),H(t)] + \left(\frac{\del A_S}{\del t}\right)_H
\end{align}
```
where the second line comes from $U U^{\dagger} = {\bf 1}$, and the last line takes a little algebra using our definition of $H$ above. We usually write this as the *Heisenberg equation of motion*, 
```{math}
:label: heisenberg_eom
i \hbar \frac{d A_H}{dt} = [A_H, H] + \left(\frac{\del A_S}{\del t}\right)_H
```
This should remind you of the classical Hamilton's equations in Poisson bracket form, $\frac{d}{dt} A = \{A,H\} + \frac{\del A}{\del t}$. This form of the equations of motion are sometimes computationally useful.

B. Note that {eq}`ham_def` means that we can equivalently specify $U$ or $H$. Hiven $H$ we can write a differential equation for $U$, 
```{math}
\frac{d U}{dt} = \frac{1}{i\hbar} H(t) U(t,t_0)
```
Since we know $U(t_0,t_0) = {\bf 1}$ we have a first order differential equation with a known initial condition. In the case that $H(t) = H$, there is a clear solution:
```{math}
U(t,t_0) = e^{- \frac{i}{\hbar} H (t - t_0)}
```
Similarly, if $[H(t), H(t')] = 0$ for all $t,t'$, a little works shows that
```{math}
U(t,t_0) = e^{- \frac{i}{\hbar} \int_{t_0}^t dt' H(t')}
```
If $[H(t), H(t')] \neq 0$ at any time between $t_0$ and $t$ the situation is more complicated. We can show that the correct expression is
```{math}
U(t,t_0) = T \exp\left( - \frac{i}{\hbar} \int_{t_0}^t dt' H(t')\right)
```
The "operator" T is the *time ordering operator*. What we do is expand the exponential out in a power series of its argument. We get a set of expressions of the form
```{math}
T [H(t_1) H(t_2)\ldots H(t_n)] \equiv H(t_{\sigma_1}) H(t_{\sigma_2}) \ldots H(t_{\sigma_n})
```
where $\sigma_k$ is a reordering of $1,\ldots, n$ such that 
```{math}
t_{\sigma_1} \geq t_{\sigma_2} \geq \ldots t_{\sigma_{n-1}} \geq t_{\sigma_n}
```
You should show for yourself that this is a correct solution; it will not benefit us to write it out here.
