---
title: Data-PCA
author: Junhan Hu
tags: [data]
mathjax: true
categories:
- CS
- Data
date: 2019-3-8 19:41:00
---

## 1 Introduction

Principal component analysis (PCA) is a common tool for data analysis

* Goal: reduce complex data set to a **lower dimension**
* Math tool: singular value decomposition (**SVD**)

<!-- more -->

### 1.1 intuition

Many problem in real world can be expressed by **a small number of variables**. But we don't know that, we just collect **so many data** and have no ideal how to deal with **hundreds of variables**. Also, there will be noise in our data, which makes the problem even more complicated.

PCA is to solve this problem by *identify the **most meaningful** basis to re-express the data.* Then we can delete the less important basis( variable)

### 1.2 A little math

* $\mathbf{X}$ : the original data set $\rightarrow$ how to re-express $\mathbf{X}$
  * row : variable ;
  * column : measurements
* $\mathbf{Y}$ : transformed data set $\rightarrow$ how $\mathbf{Y}$ should look like  $\rightarrow$ $\mathrm{C}_{\mathrm{Y}}$
* $\mathbf{P}​$ : transformation
* $\sigma_{\mathrm{ab}}^{2}​$ : covariance o f A and B
  * $\sigma_{\mathrm{ab}}^{2} \equiv \frac{1}{n} \mathbf{a b}^{T}$ , $\mathbf{a}=\left[a_{1} a_{2} \ldots a_{n}\right]$  ,$\mathbf{b}=\left[b_{1} b_{2} \ldots b_{n}\right]$
* $\mathbf{C}_{\mathbf{X}} \equiv \frac{1}{n} \mathbf{X} \mathbf{X}^{T}$ : covariance matrix of $\mathbf{X}$, the covariance value reflect the noise and redundancy in the measurement
  * large off-diagonal terms correspond to high redundancy

**Assumption 1**: *bigger variance, more information*
**Assumption 2**: If the covariance of 2 variable is big, one of them should be deleted.
**Assumption 3**: the principal components are orthogonal

### 1.3 Goal in math

Find a  transformation $\mathbf{P}​$( an orthonormal matrix) to make $\mathrm{C}_{\mathrm{Y}}​$

* A diagonal matrix, means $\mathbf{Y}​$ is **decorrelated**
* diagonal terms **decrease** from the top-left, means $\mathbf{Y}​$ is rank-ordered

## 2. Math Solution for PCA

### 2.1 Eigenvector Decomposition

1. Rewriting $\mathrm{C}_{\mathrm{Y}}$
   $$
   \begin{aligned} \mathbf{C}_{Y} &=\frac{1}{n} \mathbf{Y} \mathbf{Y}^{T} \\ &=\frac{1}{n}(\mathbf{P X})(\mathbf{P X})^{T} \\ &=\frac{1}{n} \mathbf{P} \mathbf{X} \mathbf{X}^{T} \mathbf{P}^{T} \\ &=\mathbf{P}\left(\frac{1}{n} \mathbf{X} \mathbf{X}^{T}\right) \mathbf{P}^{T}\\&=\mathbf{P} \mathbf{C}_{\mathbf{X}} \mathbf{P}^{T} \end{aligned}
   $$

2. Notice that $\mathrm{C}_{\mathrm{X}}$ is a symmetric matrix, and can be diagonalized.

   $$
   \mathrm{C}_{\mathrm{X}}=\mathbf{E D E}^{T}
   $$

   * $\mathbf{D}​$ is a diagonal matrix
   * $\mathbf{E}$ is a matrix of eigenvectors of $\mathrm{C}_{\mathrm{X}}​$

3. **Trick**: select $\mathbf{P}$ to be a matrix of eigenvectors of $\mathrm{C}_{\mathrm{X}}​$
   $$
   \begin{aligned} \mathbf{C}_{\mathbf{Y}} &=\mathbf{P} \mathbf{C}_{\mathbf{X}} \mathbf{P}^{T} \\ &=\mathbf{P}\left(\mathbf{E}^{T} \mathbf{D E}\right) \mathbf{P}^{T} \\ &=\mathbf{P}\left(\mathbf{P}^{T} \mathbf{D P}\right) \mathbf{P}^{T} \\ &=\left(\mathbf{P} \mathbf{P}^{T}\right) \mathbf{D}\left(\mathbf{P} \mathbf{P}^{T}\right) \\ &=\left(\mathbf{P} \mathbf{P}^{-1}\right) \mathbf{D}\left(\mathbf{P} \mathbf{P}^{-1}\right)\\ &=\mathbf{D} \end{aligned}
   $$

### 2.2 Singular Value Decomposition

SVD is a more general method of understanding *change of basis*

1. Let $\mathbf{X}$ be an arbitrary $n\times m$ matrix, and $\mathbf{X}^{T} \mathbf{X}$ be a  rank *r* , square, symmetric $m\times m$ matrix.
   * define $\left\{\hat{\mathbf{v}}_{1}, \hat{\mathbf{v}}_{2}, \ldots, \hat{\mathbf{v}}_{r}\right\}$ be the eigenvectors of $\mathbf{X}^{T} \mathbf{X}$ with associated with eighenvalues $\left\{\lambda_{1}, \lambda_{2}, \ldots, \lambda_{r}\right\}​$
   * define $\sigma_{i} \equiv \sqrt{\lambda_{i}}$ are positive real and termed the *singular value*
   * define $\left\{\hat{\mathbf{u}}_{1}, \mathbf{\hat { u }}_{2}, \ldots, \hat{\mathbf{u}}_{r}\right\}$ where $\hat{\mathbf{u}}_{\mathbf{i}} \equiv \frac{1}{\sigma_{\mathbf{i}}} \mathbf{X} \hat{\mathbf{v}}_{\mathbf{i}}$ (scaler version SVD)