# Quantization of the electromagnetic field

A proof of the spin-statistics theorem is beyond what we can do in this course -- it is typically not taught even in a standard QFT course, though one usually sees some additional arguments for it. However, the statistics emerge naturally from the quantization of *fields*. This is something I think everybody needs to see, so I will close by quantizing the electromagnetic field. It is not quite the simplest example, but it leads to some important applications.

Another way to approach this subject (particularly for massive particles) is called *second quantization*. It is equivalent to field quantization, but the starting point is to *assume* single-particle states, built multiparticle states as in the last section, and then assume that the full Hilbert space has the structure
```{math}
\cO = \cH_{no\ particles} \oplus \cH_{1\ particle} \oplus \cH_{2\ particles} \oplus \cdots
```
One can then include interaction terms which allow for changes in the number of particles through absorbption and decay. This is called "second quantization" because it is built on the "first-quantized" Hilbert space of single particles. This is often a useful starting point, but we will work a different way that makes clear that we can get all of this from standard quantization applied to a *field*.

## The classical electromagnetic field

Recall that we can write the electromagnetic field in terms of a vector and scalar potential:
```{math}
\begin{align}
{\vec E} & = {\vec\nabla} \phi + \frac{1}{c} \frac{\del}{\del t} {\vec A}\\
{\vec B} & = {\vec\nabla}\times{\vec A}
\end{align}
```
This form automatically yields half of Maxwell's equations:
```{math}
:label: bianchi_ident
\begin{align}
{\vec\nabla}\cdot {\vec B} & = 0\\
\frac{1}{c} \frac{\del}{\del t} {\vec B} - {\vec\nabla} \times{\vec E} & = 0
\end{align}
```

The other two of Maxwell's equations follow from the Euler-Lagrange equations associated to the following action:
```{math}
\begin{align}
S & = \frac{1}{8\pi} \int dt \int d^3 x \left[{\vec E}^2 - {\vec B}^2\right]\\
& =  \frac{1}{8\pi} \int dt \int d^3 x \left[\left( {\vec\nabla} \phi + \frac{1}{c} \frac{\del}{\del t} {\vec A}\right)^2 - ({\vec\nabla}\times{\vec A})^2\right]\\
& = \int dt L\\
& = \int dt d^3 x {\cal L}
\end{align}
```
The important point is that to get the equations of motion (the remaining two Maxwell equations), we demand stationarity under variations of $\phi, {\vec A}$: clearly directly varying ${\vec E}, {\vec B}$ would just yield trivial equations!
Nore here that the Lagrangian $L$ is the spatial integral $\int d^3 x {\cal L}$ of the {\it Lagrangian density} ${\cal L}$. We can think of this as a collection of variables $\phi({\vec x}, t)$, ${\vec A}({\vec x}, t)$, one for each point in space. 

We thus write $\phi = \phi_{cl} + \eps\delta\phi$, ${\vec A} = {\vec A}_{cl} + \eps \delta{\vec A}$; expand 
```{math}
\begin{align}
S & = S_{cl}[\phi_{cl},{\vec A}_{cl} + \eps \int dt d^3 x \left[ \delta\phi \delta_{\phi} S + \delta A^i \cdot\delta_i S\right] + \cO(\eps^2)\\
& = S_{cl} + \eps S_1 + \cO(\eps^2)
\end{align}
```
and demand $\delta_{\phi}S = \delta_i S = 0$ to get equations for $\phi_{cl}, A^i_{cl}$. 

At first order,
```{math}
\begin{align}
S_1 & = \frac{1}{4\pi}\int dt d^3 x {\vec\nabla}\delta\phi\cdot\left({\vec \nabla} + \frac{1}{c}\frac{\del}{\del t} {\vec A}\right)\\
& = - \frac{1}{4\pi} \int dt d^3 x \delta\phi {\vec\nabla}\cdot{\vec E} + {\rm boundary\ terms}
\end{align}
```
We will assume that the fields vanish at infinity so that the boundary terms vanish. The result is Gauss' law without matter:
```{math}
{\vec \nabla} \cdot{\vec E} = 0
```
We can do a similar calculation for the coefficient of $\delta A^i$: the result is Faraday's law in the absence of currents:
```{math}
{\vec\nabla}\times{\vec B} - \frac{1}{c} \frac{\del {\vec E}}{\del t} = 0
```
Note that when we couple to matter, these two equations get modified with source terms proportional to the charge density and current, respectively. The equations {ref}`bianchi_ident` are, in this formalism, mathematical identities. The situation changes in the presence of magnetic charges, eg magnetic monopoles and the associated currents. These have not been observed (well, one might have been seen once), and are not required by the Standard Model of particle physics. Certain "beyond-the-standard-model" theories have them; in these electromagnetism is embedded in something much more complex. In the presence of such monopoles, one cannot globally write the electric and magnetic fields in terms of a scalar and vector potential; it is fair to say that a proper Lagrangian treatment that includes both kinds of chanrges remains an open problem.

