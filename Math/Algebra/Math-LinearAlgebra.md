---
title: Linear Algebra for Robotics
author: Junhan Hu
tags: [algebra,math,robotics]
mathjax: true
categories:
- Math
- Algebra
date: 2019-1-8 14:58:00
---

## Vectors

$$
\boldsymbol { v } = \left( v _ { x } , v _ { y } , v _ { z } \right)
$$

* length of a vector

  * p-norm: $\| v \| _ { p } = \left( \sum _ { i = 1 } ^ { n } \left| v _ { i } \right| ^ { p } \right) ^ { 1 / p }$
  * Euclidean length: $p=2$ 

  <!-- more -->

* operation

  * dot product
    $$
    \boldsymbol { a } \cdot \boldsymbol { b } = \boldsymbol { b } \cdot \boldsymbol { a } = \boldsymbol { a } ^ { T } \boldsymbol { b } = \boldsymbol { b } ^ { T } \boldsymbol { a } = \sum _ { i = 1 } ^ { n } a _ { i } b _ { i } = \| a \| _ { 2 } \| b \| _ { 2 } \cos \theta
    $$

  * cross product 
    $$
    \boldsymbol { a } \times \boldsymbol { b } = - \boldsymbol { b } \times \boldsymbol { a } = \operatorname { det } \left( \begin{array} { l l l } { \hat { \boldsymbol { x } } } & { \hat { \boldsymbol { y } } } & { \hat { z } } \\ { a _ { 1 } } & { a _ { 2 } } & { a _ { 3 } } \\ { b _ { 1 } } & { b _ { 1 } } & { b _ { 3 } } \end{array} \right) = [ a ] _ { \mathbf { x } } \boldsymbol { b } = \| a \| _ { 2 } \| b \| _ { 2 } \sin \theta \hat { \boldsymbol { n } }
    $$





## Matrices

$$
A = \left( \begin{array} { c c c c } { a _ { 1,1 } } & { a _ { 1,2 } } & { \cdots } & { a _ { 1 , n } } \\ { a _ { 2,1 } } & { a _ { 2,2 } } & { \cdots } & { a _ { 2 , n } } \\ { \vdots } & { \vdots } & { \ddots } & { } \\ { a _ { m , 1 } } & { a _ { n , 2 } } & { \cdots } & { a _ { m , n } } \end{array} \right) , A \in \mathbb { R } ^ { m \times n }
$$

### Square Matrices

* Inverse $A A ^ { - 1 } = A ^ { - 1 } A = I _ { n \times n }$

* symmetric $A = A ^ { T }$

* skew-symmetric  $A = - A ^ { T }$ 
  $$
  S = [ v ] _ { \times } = \left( \begin{array} { c c c } { 0 } & { - v _ { z } } & { v _ { y } } \\ { v _ { z } } & { 0 } & { - v _ { x } } \\ { - v _ { y } } & { v _ { x } } & { 0 } \end{array} \right)
  $$

* orthogonal: $A ^ { - 1 } = A ^ { T }$ 

  * The product of two orthogonal matrices of the same size is also an orthogonal matrix
  * Group $O(n)$
    * deteminant $=+1 \to SO(n)$ 

* normal: $A ^ { T } A = A A ^ { T }$

  *  can be diagonalized by an orthogonal matrix
  * All **symmetric**, **skew-symmetric** and **orthogonal** matrices are normal matrices

* determinant: factor by which the transformation changes changes volumes in an n-dimensional space;

  * equal to the product of the eigenvalues: $\operatorname { det } ( A ) = \prod _ { i = 1 } ^ { n } \lambda _ { i }$ 

* trace: $\operatorname { tr } ( A ) = \sum _ { i = 1 } ^ { n } A _ { i i } = \sum _ { i = 1 } ^ { n } \lambda _ { i }$ 

  * sum of the diagonal elements
  * sum of the eigenvalues

### Nonsquare Matrices