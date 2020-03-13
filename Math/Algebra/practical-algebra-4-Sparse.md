---
title: Practical Linear Algebra -- Sparse Matrices
author: Junhan Hu
tags: [algebra,math,python]
mathjax: true
categories:
- Math
- Algebra
date: 2020-3-13 19:16:00 
---

## Introduction

*In practice, most large matrices are sparse — almost all entries are zeros.*

e.g. web link, word occurrence

Problem

* **Space**: require a lot of memory
* **Time**: a waste of time since most of the operations involve zero

### When

In practice, we will get a sparse matrix since we choose specific **encoding schemes**

* one-hot encoding, binary vectors, in recommender system, computer vision
* count encoding, frequency, in NLP
* TF-IDF, normalized frequency

### Solution

Use an alternate data structure: only store data of non-zero values

* **Old** data structure: Row and Column index mapped to a value
* **New** data structure: Compressed Sparse Row. Represent matrix using 3 one-dimensional arrays
  * row
  * colunm
  * value                                                                      

