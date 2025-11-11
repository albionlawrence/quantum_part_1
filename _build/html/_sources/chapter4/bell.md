# Local Realism vs. Quantum Mechanics

We close this chapter by working out a rewalization of John Bell's that we can *test* quantum mechanics against a while class of models which capture the demand that there be some underlying theory which is completely local and deterministic such taht probabilities truly capture our ignorance of some microscopic degrees of freedom. These are known as ``local hidden variable theories".

## Local realism and hidden variables for EPR states

It is easiest to define these with respect to an EPR experiment. Let us assume that we have two spin-$\half$ particles (or alternatively two photons emitted back to back in some definite direction), such that their combined spin (equivalently polarization) states are:
```{math}
:label: spin_zero
\ket{\psi} = \frac{1}{\sqrt{2}}\left(\ket{+,z}\ket{-,z} - \ket{-,z}\ket{+,z}\right)
```
Note by the way that for any unit vector $\hat{n}$, the state can be written as
```{math}
:label: spin_zero_two
\ket{\psi} = \frac{1}{\sqrt{2}}\left(\ket{+,{\hat n}}\ket{-,{\hat n}} - \ket{-,\hat{n}}\ket{+,{\hat n}}\right)
```
The minus sign between the two components is crucial here. You can showthis by brute force; when we discuss addition of anglar momentum, the point will be that the system has vanishing total (spin) angular momentum, so it is invariant under rotations.

As we discussed, if the two particles are separated such that the spin state remain described as above, measurments of one spin along a given axis are perfectly correlated wth measurements of the other spin along the same axis. Note however that if the two measurements are made along *orthogonal* axes there is no such correlation. Spin with definite sign along the $z$ axis will take values $\pm \frac{\hbar}{2}$ along the $x$ axis with $50-50$ probability.

The particular set of theories that we will test against quantum mechanics are *Locally realistic hidden variable* theories. Let's define each in term.

- *Local realism*. We demand that properties of a given particle, such as the outcomes of any measurement of the spin measured along any axis are *intrinsic* to the particle. In our EPR example, if we decide to measure particle 1 along the $z$ axis and particle 2 along the $x$ axis, we can label each particle by $\ket{z,\alpha; x,\beta}$, where $\alpha,\beta = \pm\frac{\hbar}{2}$. Thus the set of different two-particle states are $\ket{z,\alpha_1;x,\beta_1}\ket{z,\alpha_2;x,\beta_2}$, Here we have suppressed lables corresponding to possible measurements along other axes, and ewe have accepted that the measurement along any axis will always yield $\pm \frac{\hbar}{2}$.

- Now quantum mechanics tells us that the outcomes of measurements have a fundamentally probabilistic character. in distinction, *Hidden variable* theories, the probabilities are governed by unknown degrees of freedom to which we assign classical probabilities that reflect our ignorance of these degrees of freedom.

## Bell's ineqaulities

Our question is, can we reproduce the results of quantum mechanical measurement with these rules? Bell's insight was that you cannot.

As an example, we can consider the case that each particle is in one of the four following states with equal ($25\%$) probability:
```{math}
\begin{align}
\ket{z,+;x,-}_1\ket{z,-;x,+}_2\\
\ket{z,+;x,+}_1\ket{z,-;x,-}_2\\
\ket{z,-;x,+}_1\ket{z,+;x,-}_2\\
\ket{z,-;x,-}_1\ket{z,+;x,+}_2
\end{align}
```
As it happens, we can completely reproduce the results of quantum mechanics if we only make measurements along the $x$ or $z$ axis for each particle. In particular if both particles are measured along the same axis, the results will be correlated. But there is nothing fundamentally correlated about these states.

As it happens, this example is too simple. Consider instead a set of three axes along which we might make a measurement, as shown here:

![Possible axes for a measurement of spin](axes.jpeg)

We demand that for any case that the measurements of the two spins are both taken along the same axis, the results corralated as they are in the quantum case {eq}`spin_zero_two`. The probabilities for each of the 8 possible outcomes of a measurement of each particle along any of the axes $a,b,c$ are captures in the following table:

![Bell probability table](bell_probs.jpeg)

Now we can put some bounds on these classical probabilities. Positivity or probabilities means that
```{math}
:label: be_one
p_3 + p_4 \leq p_3 + p_4 + p_2 + p_7 = (p_2 + p_4) + (p_3 + p_7)
```
Now we can relate these sums to various outcomes:
```{math}
:label: joint_prob
\begin{align}
p_3 + p_4 & = p({\hat a}_1\cdot{\vec S}_1 = \frac{\hbar}{2}; {\hat b}_2\cdot{\vec S}_2 = \frac{\hbar}{2})\\
p_2 + p_4 & =  p({\hat a}_1\cdot{\vec S}_1 = \frac{\hbar}{2}; {\hat c}_2\cdot{\vec S}_2 = \frac{\hbar}{2})\\
p_3 + p_7 & =  p({\hat c}_1\cdot{\vec S}_1 = \frac{\hbar}{2}; {\hat b}_2\cdot{\vec S}_2 = \frac{\hbar}{2})
\end{align}
```
The probabilities on the RHS are *joint probabilities*, not *conditional probabilities*. With this in mind, in the first line, cases 3 and 4 are the only two cases with ${\hat a}_1\cdot{\vec S}_1 = \frac{\hbar}{2},  {\hat b}_2\cdot{\vec S}_2$, and similarly for the next two cases. Now {eq}`be_one` combined with {eq}`joint_prob` leads to *Bell's inequality*
```{math}
:label: bell_ineq
p(a_1 = +,b_2 = +) \leq p(a_1 = +,c_2 = +) + p(c_1 = +, b_2 = +)
```
where we have taken ${\hat a}_1 \cdot {\vec S}_1 = \frac{\hbar}{2} \to a_1 = +$ and so on.

What does quantum mechanics predict? Let us consider the state {eq}`spin_zero_two`. Bu convention the person measuring the first spin is called "Alice" and the person measuring the second spin is called "Bob". Alice will measure the spin along axis ${\hat n}_A$ and Bob will measure the spin along axis ${\hat n}_B$. Let the angle between these axes be $\psi$ (eg {\hat n}_A \cdot{\hat n}_B = \cos\psi$). Then with some work, you can show that the *conditional probability* for Bob measuring spin-up *given* that Alice measures her spin as up is
```{math}
p({\hat n}_B\cdot{\vec\sigma} = +1|{\hat n}_A\cdot{\vec\sigma} = +1) = \sin^2 \frac{\psi}{2}
```
Since we can choose the axis in {eq}`spin_zero_two` and get the same state, we can choose it to be ${\hat n}_A$. Thus, Alice has a $50\%$ chance of measuring the spin as ${\hat n}_A \cdot{\vec\sigma} = +1$, so the *joint probability* of ALice and Bob both measuring the spins as up is:
```{math}
:label: qm_conditional
p({\hat n}_A\cdot{\vec\sigma} = +1,{\hat n}_B\cdot{\vec\sigma} = +1) = \half \sin^2 \frac{\psi}{2}
```

Now let us consider the axes displayed in the picture. They are all coplanar, and the angle between ${\hat a}$ and ${\hat c}$ is $\theta$; between ${\hat b}$ and ${\hat c}$ is $\theta$; and between ${\hat a}$ and ${\hat b}$ is $2\theta$. We further demand that 0 < \theta < \frac{\pi}{2}$: note that this is a *strict* inequality.

![Test of Bell inequalities](bell_test.jpeg)

This setup violates the Bell inequalities. Let us assume the e=inequalities are true. Using {eq}`qm_conditional` and inserting them into {eq}`bell_ineq` given the experimental setup shown, the inequalities would mean
```{math}
\sin^2\theta \leq \sin^2\frac{\theta}{2} + \sin^2\frac{|theta}{2} = 1 - \cos\theta
```
where we have used a half angle identity. Using $\sin^2\theta = 1 - \cos^2\theta$, the above inequality would requitre that $\cos^2\theta > \cos\theta$. But given our bounds on $\theta$, $0 < \cos\theta < 1$, so this inequality cannot be satisfied.

It is clear that each of these probabilities can be measured, in separate experiments in which the axes are fixed. One can then test the predictions of quantum mechanics. They have been borne out in variants of this experiment. However, the test is essentially a probabilistic one. If we were going to be sticklers we could say that the community of quantum physicists have gotten supremely unlucky and the apparent violations are a matter of bad luck or Trisolarians interfering with the hidden variables or something. We will turn now to a definitive test of quantum mechanics vs. locally realistic hidden variables.

## The Greenberger-Horne-Zeilinger (GHZ) experiment

The experiment we have involves three spin-$\half$ particles observed by three observers Alice, Bob and Charlotte. The full state of the system is the entangled state:
```{math}
:label: ghz_state
\ket{\psi} = \frac{1}{\sqrt{2}}\left(\ket{z,+}_A\ket{z,+}_B\ket{z,+}_C - 
\ket{z,-}_A\ket{z,-}_B\ket{z,-}_C\right)
```
Now the following three observables commute (so that they can be simultaneously diagonalized, and therefore simultaneously measured):
```{math}
\begin{align}
\Sigma_1 & = \sigma^A_x\sigma^B_y\sigma^C_y\\
\Sigma_2 & = \sigma^A_y\sigma^B_x\sigma^C_y\\
\Sigma_3 & = \sigma^A_y\sigma^B_y\sigma^C_x
\end{align}
```
Note to measure each of these requires each of Alice, Bob, and Charlotte agreeing to measure along a specified axis. You can show that $\Sigma_i ket{\psi} = \ket{\psi}$, that is, $\ket{\psi}$ is an eigenstate for all of these operators. Finally, the following observable commutes with the first three:
```{math}
\sigma_4 = \sigma^A_x\sigma^B_x\sigma^C_x
```
but $\Sigma_4\ket{\psi} = - \ket{\psi}$. Note that if we successfully prepare the GHZ state 

Can this be realized in a locally realistic hidden variable theory? This happens if for every particle $A,B,C$ we can specify the results of experiments $\epsilon_{\mu\in (A,B,C), i \in (x,y)} = \pm 1$, with the probabilities for each of the $2^6$ possibilities defining the probability ensemble.

Without knowing anything about the ensemble, however, we can show that a lcoally realistic hidden variable cannot reproduce the GHZ experiment applied to {eq}`ghz_state`. If they did, then the states must satisfy
```{math}
\begin{align}
\eps_{A,x}\eps_{B,y}\eps_{C,y} & = 1\\
\eps_{A,y}\eps_{B,x}\eps_{C,y} & = 1\\
\eps_{A,y}\eps_{B,y}\eps_{C,x} & = 1
\end{align}
```
However this is incompatible with $\eps_{A,x}\eps_{B,x}\eps_{C,x} = -1$. Multiply the three equations above together. We can write
```{math}
\begin{align}
\eps_{A,x}\eps_{B,x}\eps_{C,x} & = \eps_{A,x}\eps_{A,y}^2 \eps_{B,x}\eps_{B,y}^2\eps_{C,x}\eps_{C,y}^2 \\
& = (\eps_{A,x}\eps_{B,y}\eps_{C,y}) (\eps_{A,y}\eps_{B,x}\eps_{C,y}) (\eps_{A,y}\eps_{B,y}\eps_{C,x}) = 1^3 \neq -1
\end{align}
```
Thus a one-shot measurement of $\Sigma_{1,2,3,4}$ on the state $\ket{\psi}$ can rule out locally realistic hidden variable theories. 
