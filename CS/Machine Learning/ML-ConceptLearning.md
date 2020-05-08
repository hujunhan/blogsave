---
title: ML:First Step
author: Junhan Hu
tags: [ml]
mathjax: true
categories:
- CS
- Machine Learning
date: 2019-1-16 11:50:00
---

## 1 Introduction

**How** machine can learn from data?

First of all, we need to understand human brain. And we can make the machine learning application work the same way as our brain did.

<!-- more -->

**Most** simple algorithms: **Find-S**

## 2 What is Concept Learning

> “The problem of searching through a predefined space of potential hypotheses for the hypothesis that best fits the training examples.”
>
> ​       — Tom Michell

Human learning: acquiring general concepts from past experiences.

Machine learning: find a hypothesis that best fits the training example.

Notaion:

* target concept $c$
* object $X$
* all hypothesis set $H$
* $c : X \to \{ 0,1 \}$

**\******What we should do is to find a hypothesis** $h ( x ) = c ( x ) \text { for all } x \text { in } X$

> Good hypothesis fit **large set** of training example well
>
> $\to$ the hypothesis fit **unobserved** example well

## 3 Find-S

### 3.1 Hypothesis Notations

1. $\varnothing$ :a hypothesis that **rejects all**
2. $< ? , ? , ? , ? >$ :**accepts all**
3. $< \text { true, false, } ? , ? >$ :**accepts some**

Total number of the possible hypothesis $N=(3*3*3*3)+1=82$

### 3.2 Specific to General

1. Start with the most specific hypothesis $\mathbf { h } \leftarrow < \boldsymbol { \varnothing } , \boldsymbol { \varnothing } , \boldsymbol { \varnothing } , \boldsymbol { \varnothing } >$
2. Pick up a sample
   1. if sample is **negative** $\to​$ unchanged
   2. if sample is **positive** $\to$ update current hypothesis
      * $<true,true,false,true> \and <true,true,false,false> \to <true,true,false,?>$
3. repetition of Step 2

### 3.3 Limitations

* No way to determine if result is consistent with the data
* Inconsistent sets will mislead the result
* No backtrack

## 4 Candidate-elimination

### 4.1 Chrarcters

Maintain 2 hypothesis

* $S_0$ most specific
* $G_0$ most general

### 4.2 Algorithm

Pick up a sample

* if sample is **negative** $\to$ specificalize $G_0$
* if sample is **positive**  $\to$  generalize $S_0$

### 4.3 Limitations

Low fault tolerance

## 5 Inductive Bias

Stronger the bias is, more powerful the generaliztion is.

indicate that: If there is no assumption, the learner can learn **nothing** but the **data**

Common biases:

* Maximum conditional independence
* Minimum cross-validation error
* Minimum description length :*Occam's razor*
* Minimum features
