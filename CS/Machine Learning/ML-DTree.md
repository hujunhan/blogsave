---
title: ML:Decision Tree
author: Junhan Hu
tags: [ml]
mathjax: true
categories:
- CS
- Machine Learning
date: 2019-1-16 13:47:00
---

## 1 Introduction

### 1.1 What is a Decision Tree?

A tree shaped  supervised learning algorithm

![decision-tree](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/decision-tree.png)

<!-- more -->

Problem setting:

* Set of possible instances $X$ 
  * each instance $x$ in $X$  is a feature vector $x = < x _ { 1 } , x _ { 2 } \ldots x _ { n } >$ 
* Unknown target function $f : X \rightarrow Y$ 
* Set of function hypotheses $H = \{ h | h : X \rightarrow Y \}$ 

Input:

* Training examples $\left\{ < x ^ { ( i ) } , y ^ { ( i ) } > \right\}$ 

Output:

* Hypothesis $h \in H$ that best approximates target function $f$

### 1.2 How it works?

The tree divide the data into many categories make biggest **entropy**. That means the tree will try to get the **maximum information gain** from the dataset.

## 2 How to Split a Node

In other word, how to split a node into 2 or more sub-nodes.

There are multiple methods can be used：

1. Information gain

   * Based on  entropy and information theory.

   * Used by *ID3* *C4.*5 *C5.0* 

   * Entropy $\mathrm { H } ( T ) = \mathrm { I } _ { E } \left( p _ { 1 } , p _ { 2 } , \ldots , p _ { J } \right) = - \sum _ { i = 1 } ^ { J } p _ { i } \log _ { 2 } p _ { i }$ 

     Note: $\sum p_i=1$ which means if $p_i=p_j$ ,$H(T)$ is biggest $1 $ (equal probablity, most chaos)

   * Information Gain
     $$
     I G ( T , a ) = H ( T ) -  \mathrm { H } ( T | a )\\
     =- \sum _ { i = 1 } ^ { J } p _ { i } \log _ { 2 } p _ { i } - \sum _ { a } p ( a ) \sum _ { i = 1 } ^ { J } - \operatorname { Pr } ( i | a ) \log _ { 2 } \operatorname { Pr } ( i | a )
     $$

2. Gini impurity

   *  A measure of impurity, lower $\to$ better

   * Used by *CART* (classification and regression tree) for **classification** 

   * Calculation
     $$
     \mathrm { I } _ { G } ( p )= 1 - \sum _ { i = 1 } ^ { J } p _ { i } ^ { 2 }
     $$

3. Variance reduction

   * Used by *CART* (classification and regression tree) for **regression** 



## 3 Overfitting

How to avoid?

* Stop growing when data split not statistically **significant**

  * easy to understand
  * hard to decide what is significant

* Grow full tree, then post-prune

  * useful in practice
  * Reduced-Error Pruning
    1. Create a tree that classifies **training set**
    2. Evaluate impact on *validation set* of purning each possible node
    3. Greedily remove the impact most slightly 

  