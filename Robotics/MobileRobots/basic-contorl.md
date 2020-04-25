---
title: Basic Control Theory
author: Junhan Hu
tags:
  - robotics
  - control
mathjax: true
date: 2020-4-5 
---

## About the Course

what’s in this course

* control theory

  * mathematical play a important role

* robot models

* mobility **controllers**

  * How to do, not why to do (Not a AI course)

  > great! I have learned planning in the school so I can focus on the control theory that boost the overall performance

* application

<!-- more -->

## What is control theory

system: something that changes over time

control: influence that change

---

Building blocks

* State: $x$ representation of what the system is currently doing 
* Dynamics
* Reference $r$ what we want the system to do 
* output: $y$ measurement of system
* input: $u$ control signal
* Feedback: mapping from output to input

## Model

model is the approximation the real system.

Why model is **important**? because we need to **design** control theory

How we design control system, there are some objectives

* **stability** BIBO bounded in bounded out
* **tracking** 
* **robustness**: model are not perfect, so we need to tolerant parameter
* disturbance rejection
* optimality: how to do the thing best 

In implementation, everything is **discrete**/sampled (Taylor series )
$$
x_{k+1}=x_k+\delta t\dot x_k
$$

## Cruise-Controllers

Make a car drive a desired speed $r$

Physics: Newton’s Second Law
$$
F=ma
$$

State: velocity $x$, and we should measure velocity as well

input: gas/brake $u$ 
$$
F=cu
$$
where $c$ is a electro-mechanical transmission coefficient
$$
cu=m\dot x
$$
simple model has big power

---

The expected properties of the control signal:

* small $e$ error gives small $u$ control signal
* $u$ should NOT be jerky, so the performance would be smooth
* $u$ should NOT depend on exact $c$ and $m$, so this will be a robust control model

### Control Design

we got car model $\dot x=\frac{c}{m}u$

we want $x\to r \space$ as $t\to \infin$

* Attempt 1: Bang-Bang Control
  * Nope, turns out bumpy ride and burns out **actuators**
  * Problem: **over-reacts to small errors**
* Attempt 2: P control $u=ke$
  * Nope, has steady error
  * Problem: not **tracking**
* Attempt 3:  $u=ke+\gamma\frac{m}{c}x$
  * Nope, yet cancel the steady error
  * Problem:  **not robust**
* Attempt 4: PI controller, even, **PID controller**

## PID Controller

Widely used controller
$$
u(t)=k_{P} e(t)+k_{I} \int_{0}^{t} e(\tau) d \tau+k_{D} \frac{d e(t)}{d t}
$$
3 knobs we can tune $k_P, k_I,k_D$

* P: contributes to stability,medium-rate responsiveness
* I: tracking and disturbance rejection, slow-rate responsiveness
  * may cause **oscillation**
* D: Fast-rate responsiveness. Sensitive to noise

## Implementation

First, translate into something implementable

* find the sample time $\Delta t$
* integral： $E_{new}=E_{old}+\Delta te$

```pseudocode
read e;
e_dot=e-old_e;
E=E+e;
u=kP*e+kD*e_dot+kI*E;
old_e=e;
```

## Example: Quadrotor Altitude Control

$$
\ddot x=cu-g
\\u=PID
$$

## Programming Assignments: Week 1

Why assignments worth my time

* opportunity to apply the equation
* learn Matlab

