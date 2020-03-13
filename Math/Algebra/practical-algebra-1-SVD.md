---
title: Practical Linear Algebra -- NFM & SVD
author: Junhan Hu
tags: [algebra,math,python]
mathjax: true
categories:
- Math
- Algebra
date: 2020-3-10 21:29:00 
---

## Motivation

We want to decompose a matrix using an outer **product of two vectors** 

## SVD Singular Value Decomposition

### Motivation

we except the topics to be **orthogonal**, so it can express most information

### Idea

![img](https://nbviewer.jupyter.org/github/fastai/numerical-linear-algebra/blob/master/nbs/images/svd_fb.png)

<!-- more -->

### Application

* recommendation
* calculate pseudoinverse
* data compression
* PCA

## NMF Non-negative Matrix Factorization

### Motivation

It’s hard to explain face image while using PCA since there is **negative** value

So this method avoid negative value

Benefits: fast and easy to use

### Idea

Deprecate orthogonal idea, another idea: constrain them to be non-negative

Goal: Do decomposition
$$
V \approx W H
$$
Approach: add **penalty** to punish negative elements, that means the result will be just a **approximation**, and **not-unique**

Using SGD(Stochastic Gradient Descent), add 

### Application

* Face decomposition
* bioinformatics
* Topic modeling

## Faster SVD

### Motivation

* Normal SVD is pretty **slow**, we need to speed it up
* Data are often **missing** or **inaccurate**
* Take advantage if **GPUs**

We are just interested in the **largest** singular values

So introduce randomized algorithms that 

- more stable
- needed matrix-vector products can be done in parallel
- performance guaranteed

### Idea

Use a smaller matrix

1. Before: calculate SVD of $A(m\times n)$

2. Basic **Math**: **Johnson-Lindenstrauss Lemma**

   > a small set of points in a high-dimensional space can be embedded into a space of much lower dimension in such a way that distances between the points are nearly preserved.

3. After: calculate SCD of $B(m,r)=AQ\space,\space r<<n$

### Computation

1. Find an approximation $Q$ to the **range** of $A$, here range means linear combination.

   That means $Q$ has similar column space with $A$ but fewer columns
   $$
   A\approx Q Q^tA
   $$
   
2. Construct $B=Q^TA$, which is small

3. Compute the SVD of $B=S \Sigma V^{T}$

4. Since $A\approx Q Q^T A=QB=QS \Sigma V^{T}$

   if we set $U=QS$, we can get 
   $$
   A\approx U\Sigma V^T
   $$

5. Done!

But how do we get $Q$ in step 1?

1. Take a bunch of random vector $w_i$ and form a matrix $W$, in this way ,$AW$ represent the space that column of $A$ can **span**.
2. Calculate $AW=QR$, where $Q$ form an orthonormal basis for $Aw$