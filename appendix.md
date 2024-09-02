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

### Einstein summation convention

The Einstein summation convention is that all repeated indices are summed over unless otherwise stated explicitly. Thus, for some $d$-dimensional vectors $V^i$, $W^i$ 

```{math}
:label: einstein_def
V^i W^i \equiv \sum_{j = 1}^d V^j W^j
```

Technically speaking I am being a little careless. In curved spaces (for example, on the sphere), there are geometrically distinct objects $V^i$, $V_i$, and I should only be summing over pairs of indices in which one is raised and one is lowered. In Euclidean space, however, there is a standard map which states that numerically, $V^i = V_i$, so I will ignore this issue for the time being.

(We can think of $V^i, W^i$ as elements of a vector space, and $V_i, W_i$ their dual vectors; we will discuss this language when we get to linear algebra).

Derivatives of expressions involving the Einstein summation convention often confuse people. For a venerak vector field $V^I(x)$, 
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


