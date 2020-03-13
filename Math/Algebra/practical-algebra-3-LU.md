---
title: Practical Linear Algebra -- LU Factorization
author: Junhan Hu
tags: [algebra,math,python]
mathjax: true
categories:
- Math
- Algebra
date: 2020-3-12 00:22:00 
---

## Motivation

While implementing *Randomized SVD*, we used LU factorization, that is factors a matrix into the product of a **lower triangular** matrix and an **upper triangular** matrix.
$$
A=LU
$$
Why LU is useful?

We can solve $Ax=b$ problem faster

1. find $A=LU$
2. solve $Ly=b$
3. solve $Ux=y$

## Calculation

$$
A=\left(\begin{array}{cccc}
1 & -2 & -2 & -3 \\
3 & -9 & 0 & -9 \\
-1 & 2 & 4 & 7 \\
-3 & -6 & 26 & 2
\end{array}\right)
$$

Using **Gaussian Elimination**, after Gaussian Elimination, we will get a **upper triangular matrix**, so we can regard the **combination of eliminiation operation** is a **lower triangular matrix** that is $L_{m-1} \ldots L_{2} L_{1} A=U$
$$
L U=\left[\begin{array}{cccc}
1 & 0 & 0 & 0 \\
3 & 1 & 0 & 0 \\
-1 & 0 & 1 & 0 \\
-3 & 4 & -2 & 1
\end{array}\right] \cdot\left[\begin{array}{cccc}
1 & -2 & -2 & -3 \\
0 & -3 & 6 & 0 \\
0 & 0 & 2 & 4 \\
0 & 0 & 0 & 1
\end{array}\right]
$$

### Partial Pivoting

Note: LU factorization is stable, but not *backward* stable
$$
A=\left[\begin{array}{cc}
10^{-20} & 1 \\
1 & 1
\end{array}\right]
$$

```python
L1, U1 = GaussianElimination(A)
L2, U2 = LU(A)
np.allclose(L1, L2)
#true
np.allclose(U1, U2)
#true
np.allclose(A, L2 @ U2)
#false...means not backward stable
```

we can get more stable answer by switching the order of the rows
$$
A=\left[\begin{array}{cc}
1 & 1 \\
10^{-20} & 1
\end{array}\right]
$$
How? **Multiplying by a permutation matrix P**
$$
\left[\begin{array}{ll}
0 & 1 \\
1 & 0
\end{array}\right] \cdot\left[\begin{array}{cc}
10^{-20} & 1 \\
1 & 1
\end{array}\right]=\left[\begin{array}{cc}
1 & 1 \\
10^{-20} & 1
\end{array}\right]\\
PA=A'
$$
At each step, choose the largest value in column k, and move that row to be row k.

