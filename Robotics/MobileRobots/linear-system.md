---
title: Linear System
author: Junhan Hu
tags:
  - robotics
  - control
mathjax: true
date: 2020-4-21 
---

## Simple Robot

We need a more systematic way in discussion

Give a point mass on a line whose acceleration is directly controlled:

Translate the physics model into state space form, 3 steps

1. Pick the state variables 
2. High order to low order
3. Put these in terms of state, input and output

$$
\dot{x}=\left[\begin{array}{c}
\dot{x}_{1} \\
\dot{x}_{2}
\end{array}\right]=\left[\begin{array}{c}
x_{2} \\
u
\end{array}\right]=\left[\begin{array}{cc}
0 & 1 \\
0 & 0
\end{array}\right]\left[\begin{array}{c}
x_{1} \\
x_{2}
\end{array}\right]+\left[\begin{array}{c}
0 \\
1
\end{array}\right] u
$$

$$
y=p=x_1=[1 \space0]x
$$

Write in a more **general** form
$$
\begin{aligned}
&\dot{x}=A x+B u\\
&y=C x
\end{aligned}
$$
Here, $A$ is given by physics. What we can design is $B$ (how we control the system) and $C$ (how we sensor the system)  

<!-- more -->

## State-Space Models & Linearization     

We need know how the system works, then we can model it using physics

But sometimes the system is non-linear, so we need linearization`
$$
\dot{x}=f(x, u), \quad y=h(x)
$$

1. Find a operating point
2. Taylor expansion

$$
 \dot{\delta} x=f\left(x_{o}+\delta x, u_{o}+\delta u\right)
=f\left(x_{o}, u_{o}\right)+\frac{\partial f}{\partial x}\left(x_{o}, u_{o}\right) \delta x+\frac{\partial f}{\partial u}\left(x_{o}, u_{o}\right) \delta u+ H.O.T
$$

$H.O.T$ for high order terms  

> Sometimes the linearization do not give reasonable models

## Solving ODE

$$
e^{A t}=\sum_{k=0}^{\infty} \frac{A^{k} t^{k}}{k !}
$$

The State Transition Matrix
$$
e^{A\left(t-t_{0}\right)}=\Phi\left(t, t_{0}\right)
$$
If we do not apply a control system, then $\dot x=Ax$, then
$$
 x(t)=\Phi(t, \tau) x(\tau)
$$
If we have the controlled system: $\dot x=Ax+Bu$, then 
$$
x(t)=\Phi\left(t, t_{0}\right) x\left(t_{0}\right)+\int_{t_{0}}^{t} \Phi(t, \tau) B u(\tau) d \tau
$$
We can verify the answers by checking the initial point and derivation

Why so care about the solution? 

Because we can write the $y$
$$
y=Cx
$$

## Stability

$$
\dot{x}=A x \Rightarrow x(t)=e^{A t} x(0)
$$

By calculating the eigenvalue of $A$

When all eigenvalue of $A$ is negative:
$$
\operatorname{Re}(\lambda)<0, \forall \lambda \in \operatorname{eig}(A)
$$

## Design Feedback Control

How?  Recall the control system
$$
\begin{aligned}&\dot{x}=A x+B u\\&y=C x\end{aligned}
$$
Let $u$ related with $y$, say $u=-Ky$, than, the $A$ matrix changes!
$$
\dot x=Ax-BKCx=(A-BKC)x
$$
Make sure that $Re(eig(A-BKC))<0$

## Example

### Modeling

For **Physics**
$$
m \ddot{f}=\alpha \dot{f}+\beta f+c p
$$
For **Human**

1. Pick the state variables 
2. High order to low order
3. Put these in terms of state, input and output

For **Math**

1. $x=\left[\begin{array}{c}
   f \\
   \dot{f}
   \end{array}\right] \quad u=p \quad y=f$
2. $\begin{aligned}
   &\dot{f}=\dot{x}_{\hat{1}}=x_{2}\\
   &\ddot{f}=\dot{x}_{2}=\frac{1}{m}\left(\alpha x_{2}+\beta x_{1}+c u\right)
   \end{aligned}$
3. $\dot{x}=\left[\begin{array}{l}
   \dot{x}_{1} \\
   \dot{x}_{2}
   \end{array}\right]=\left[\begin{array}{l}
   x_{2} \\
   \frac{1}{m}\left(\alpha x_{2}+\beta x_{1}+c u\right)
   \end{array}\right]$

For **Control**
$$
\begin{array}{l}
x=\left[\begin{array}{c}
f \\
\dot{f}
\end{array}\right] \quad u=p \quad y=f \\
(A, B, C)=\left(\left[\begin{array}{cc}
0 & 1 \\
\frac{\beta}{m} & \frac{\alpha}{m}
\end{array}\right],\left[\begin{array}{c}
0 \\
\frac{c}{m}
\end{array}\right],\left[\begin{array}{cc}
1 & 0
\end{array}\right]\right)
\end{array}
$$

### Linearization

For physics
$$
\ddot{z}=\ell z^{2}+\gamma \dot{z}+c \tau \quad x=\left[\begin{array}{c}
z \\
\dot{z}
\end{array}\right] \quad u=\tau
$$
If we want to linearize the system around $x=0$ (**important**!)
$$
\begin{array}{c}
A=\left[\begin{array}{cc}
\frac{\partial f_{1}}{\partial x_{1}} & \frac{\partial f_{1}}{\partial x_{2}} \\
\frac{\partial f_{2}}{\partial x_{1}} & \frac{\partial f_{2}}{\partial x_{2}}
\end{array}\right]_{x=(0,0)}=\left[\begin{array}{cc}
0 & 1 \\
2 \ell x_{1} & \gamma
\end{array}\right]_{x=(0,0)}=\left[\begin{array}{cc}
0 & 1 \\
0 & \gamma
\end{array}\right] \\
B=\left[\begin{array}{c}
\frac{\partial f_{1}}{\partial u} \\
\frac{\partial f_{2}}{\partial u}
\end{array}\right]_{x=(0,0)}=\left[\begin{array}{c}
0 \\
c
\end{array}\right]_{x=(0,0)}=\left[\begin{array}{c}
0 \\
c
\end{array}\right]
\end{array}
$$
