# Appendix

## Notation

### Derivatives and partial derivatives

- I will often write

```{math}
:label: part_der
\del_i \equiv \frac{\partial}{\partial x^i}
```

### Einstein summation convention

The Einstein summation convention is that all repeated indices are summed over unless otherwise stated explicitly. Thus, for some $d$-dimensional vector $V^i$, 

```{math}
V^i V^i \equiv \sum_{j = 1}^d V^j V^j
```

Technically speaking I am being a little careless. In curved spaces (for example, on the sphere), there are geometrically distinct objects $V^i$, $V_i$, and I should only be summing over pairs of indices in which one is raised and one is lowered. In Euclidean space, however, there is a standard map which states that numerically, $V^i = V_i$, so I will ignore this issue for the time being.

(We can think of $V^i$ as an element of a vector spave, and $V_i$ its dual vector; we will discuss this language when we get to linear algebra).
