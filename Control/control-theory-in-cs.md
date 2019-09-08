---
title: Control Theory and Application in CS
author: Hu Junhan
tags:
  - control
published: true
categories:
  - Control
date: 2019-09-08 15:23:00
---

## Introduction

Control theory provides a **systetmatic approach** to design feedback loops that are stable and settle quickly to their steady state values.

In many computing systems, control theory is used widely in problem such as adjusting scheduling priorites, memory allocations, and network bandwith allocation and flow control and TCP/IP

## Control Theoty Fundamentals

> The magic of feedback: create a system that perform well from components that perform poorly.
>
> ​																																							— Karl Astrom

<!-- more -->

### Notions

Because we are talking about computer system, so the time is discrete. Here are some symbols

* time: $k$
* reference input: $r(k)$, the desired value of measured output
* control error: $e(k)$, the difference between reference input and the measured output
* control output $u(k)$, the output of controller. **This is a parameter in the target system** 
* disturbance input $d(k)$, any changes that affects the way in which the $u(k)$  influences the measured output
* measured output $y(k)$
* noise input $n(k)$ changes the measured output produced by the target system

### Purpose

* regulatory control: ensure the measured output is close to the reference input
* disturbance rejection
* optimization: obtain the best value of the measured output

### Good Properties

**SASO**

* stable
* accurate
* short settling time
* no overshoot

## Example 1 IBM Lotus Domino Server

Goal: Control *RIS* in the server

1. Model how *MaxUsers* (output of the controller) affects *RIS*

   Construct the model by applying **least squares regression** to the data obtained from off-line experiments **data**. And the resulting model is
   $$
   y(k)=0.43 y(k-1)+0.47 u(k-1)
   $$
   Then use Z-transform to get the transfer function
   $$
   G(z)=\frac{0.47}{z-0.43}
   $$

2. Construct a controller, we want to the whole system’s transfer function has following properties:

   * the pole of transfer function close to 0
   * the stead state gain to be 1

