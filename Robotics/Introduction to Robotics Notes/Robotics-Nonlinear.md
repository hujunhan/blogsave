---
title: Robotics-Nonlinear Control
author: Junhan Hu
tags: [control,robotics]
mathjax: true
categories:
- Robotics
- Introduction to Robotics Notes
date: 2019-1-1
---

## 1 Introduction

In linear control, we modeled the manipulator by $n$ independent second-order differential equations.

In this chapter, we will base our controller design on the $n \times 1$ vector differential equation

<!-- more -->

## 2 Nonlinear

1. local linearization

   When nonlinearities are not severe, **local linearization** can be used in the **neighborhood** of an operating point. 

   But, manipulator move among regions so **widely separated** that no linearization valid for all regions can be found.

2. moving linearization

   move the operating point with the manipulator as it
   moves, always linearizing about the desired position of the manipulator

3. deal with the nonlinear directly

   the poles of the system will "move", so we can not select fixed gains. Instead, the gains are also time-varying so it will keep the system critically damped

4. Example: nonlinear spring

   open loop equation: $m \ddot { x } + b \dot { x } + q x ^ { 3 } = f$

   servo portion:  $f ^ { \prime } = \ddot { x } _ { d } + k _ { v } \dot { e } + k _ { p } e$

   model-based portion: **changed**

   ​	$\begin{array} { l } { \alpha = m } \\ { \beta = b \dot { x } + q x ^ { 3 } } \end{array}$



##3 Control problem  for Manipulators

For manipulator, the model is complicated
$$
\tau = M ( \Theta ) \ddot { \Theta } + V ( \Theta , \dot { \Theta } ) + G ( \Theta )
$$
where $\Theta $ is the position of all the joints.

If we add friction to the model, we get 
$$
\tau = M ( \Theta ) \ddot { \Theta } + V ( \Theta , \dot { \Theta } ) + G ( \Theta ) + F ( \Theta , \dot { \Theta } )
$$
where we can use our partitioned controller again:
$$
\tau = \alpha \tau ^ { \prime } + \beta
$$
and we choose 
$$
\begin{aligned} \alpha & = M ( \Theta ) \\ \beta & = V ( \Theta , \dot { \Theta } ) + G ( \Theta ) + F ( \Theta , \dot { \Theta } ) \end{aligned}
$$
servo law: $\tau ^ { \prime } = \ddot { \Theta } _ { d } + K _ { v } \dot { E } + K _ { p } E$ where $E = \Theta _ { d } - \Theta$

finally we get 
$$
\ddot { E } + K _ { v } \dot { E } + K _ { p } E = 0
$$
This solve the problem in theory, but not in practice because

1. computer do it by **discrete** nature
2. **inaccuracy** in manipulator model

## 4 Current industrial-robot Control System

Parameters may be inaccurate. So model-based control law maybe **doesn't make sense**

For economic reasons, error driven is more usual.

* individual-joint PID control

  *average* gain are chosen

  $\tau ^ { \prime } = \ddot { \Theta } _ { d } + K _ { v } \dot { E } + K _ { p } E + K _ { i } \int Edt$

## 5 Lyapunov Stability Analysis

A analytically way to evluate stability but **not** the performance.

 