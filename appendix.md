# Appendix

## Notation

### Derivatives and partial derivatives

I will often write

```{math}
:label: part_der
\del_i \equiv \frac{\partial}{\partial x^i}
```

### Some useful tensors

1. The Kronecker delta function. If $I,J = i,\ldots,N$ are some indices then

```{math}
:label: kronecker
\delta^I_J = \begin{cases} 1 & I = J \\ 0 & I \neq J \end{cases}
```

2. The totally antisymmetric tensor

In $d$ dimensions, the tensor $\epsilon_{i_1,\ldots, i_d}$ is totally antisymmetric in the exchange of all indices. Thus the only nonvanishing components are ones for which $i_1,\ldots,i_d$ are a permutation of $1,2,\ldots,d$. We fix the tensor completely by edemanding that $\epsilon_{1,2,\ldots,d} = 1$.

### Einstein summation convention

The Einstein summation convention is that all repeated indices are summed over unless otherwise stated explicitly. Thus, for some $d$-dimensional vectors $V^i$, $W^i$ 

```{math}
:label: einstein_def
V^i W^i \equiv \sum_{j = 1}^d V^j W^j
```

Technically speaking I am being a little careless. In curved spaces (for example, on the sphere), there are geometrically distinct objects $V^i$, $V_i$, and I should only be summing over pairs of indices in which one is raised and one is lowered. In Euclidean space, however, there is a standard map which states that numerically, $V^i = V_i$, so I will ignore this issue for the time being.

(We can think of $V^i, W^i$ as elements of a vector space, and $V_i, W_i$ their dual vectors; we will discuss this language when we get to linear algebra).

Derivatives of expressions involving the Einstein summation convention often confuse people. For a general vector field $V^I(x)$, 
```{math}
 \frac{\del}{\del x^J} V^I W_I = W^I \del_J V^I + V^I \del_J W^I
```

Now if $V^I = W^I = x^I$, then $\del_J x^I = \delta^I_J$. You can convince yourselves that

```{math}
\delta^I_J V^I = V^J
```

and therefore,

```{math}
\del_J (x^I x^I) = 2 x^J
```

### More on the totally antisymmetric tensor

1. Contraction identities in $d$ dimensions
   A. $\epsilon_{i_1,\ldots,i_d}\epsilon^{i_1,\ldots,i_d} = d!$.
   B. In $d - 2$, $\epsilon_{ij} \epsilon^{ik} = \delta^k_j$.
   C. In $d = 3$, $\epsilon_{kmn}\epsilon^{k i j} = \delta^i_m \delta^j_n - \delta^i_n \delta^j_m$.
   D. In $d = 3$, $\epsilon_{ijk}\epsilon^{ijl} = 2\delta^l_k$.
   E. There are similar identities in higher dimensions, which we will leave aside for now.
   
2. Definition of cross product.

For general $d$, the cross product of two vectors $U^i V^i$ is a $d-2$-rank tensor:

```{math}
:label: d_cross_product
({\vec U} \times {\vec V})_{i_1,\ldots,i_{d-2}} = \epsilon_{i_1,\ldots,i_{d-2}, i_{d--1}, i_d} U^{i_{d-1}} V^{i_d}
```

For $d = 2$, this is a scalar (actuaklly a "pseudo-scalar"):

```{math}
:label: two_d_cross
({\vec U}\times {\vec V}) = \epsilon_{ij} U^i V^j = A^1 V^2 - U^2 V^1
```

For $d = 3$, 

```{math}
:label: three_d_cross
({\vec U}\times {\vec V})^i = \epsilon_{ijk} U^j V^k
```

Or alternatively,

```{math}
:label: three_d_cross_two
U^i V^j - U^j V^i = \epsilon_{ijk} ({\vec U}\times {\vec B})^k
```


