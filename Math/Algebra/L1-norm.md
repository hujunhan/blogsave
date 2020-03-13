---
title: Why L1 Norm is Great
author: Junhan Hu
tags: [algebra,math]
mathjax: true
categories:
- Math
- Algebra
date: 2020-3-11 23:55:00
---

## Application

### Loss Function

$$
\min _{\omega}\left\|y-\omega^{T} x\right\|_{1}
$$

### Regularization

$$
\min _{x} f(x)+\|x\|_{1}
$$

## Advantage

We can consider a easy **2D** case, and show why L1 norm is better than L2 norm 

### Loss Function

![img](https://qph.fs.quoracdn.net/main-qimg-ed279c02762abdb8c5fa3db3f200b823.webp)

L2 norm would strengthen the **error**

### Regularization

![img](https://qph.fs.quoracdn.net/main-qimg-2c59dd58f22ace702f43499147ed8641.webp)

The minimum is always located at one of the **corners** (**Red**)

* A corner is described as having **1 non-zero** coordinate with the **remaining coordinates being zero**

  So L1 norm would lead to better sparisity