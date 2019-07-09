---
title: ML:Evaluating Hypotheses
author: Junhan Hu
tags: [ml,hide]
mathjax: true
categories:
- CS
- Machine Learning
date: 2019-1-16 20:19:00
---

## 1 Error!

There are two types of error:

* *true error*: $\operatorname { error } _ { \mathcal { D } } ( h ) \equiv \operatorname { Pr } _ { x \in \mathcal { D } } [ f ( x ) \neq h ( x ) ]$ 
  * $D$ for distribution
* *sample error*: $error_s( h ) \equiv \frac { 1 } { n } \sum _ { x \in S } \delta ( f ( x ) \neq h ( x ) )$ 
  * $\delta ( f ( x ) \neq h ( x ) )=1$ if $f ( x ) \neq h ( x )$ 

How well dose *sample error* **estimate**  *true error*？

We can check

* Bias
* Variance

## 2 Estimators

1. Choose sample $S$ of size $n$ according to $D$
2. measure $error_s(h)$ 
3. $\to$ *sample error* is an **unbiased estimator** for *true error*

e.g. with approximately $95\%$ probability, *true error* lie in 
$$
\operatorname { error } _ { S } ( h ) \pm 1.96\sqrt \frac { \text { errors } ( h ) \left( 1 - e r r o r _ { S } ( h ) \right) } { n }
$$
