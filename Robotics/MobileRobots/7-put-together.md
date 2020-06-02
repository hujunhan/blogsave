---
title: Put All Together
author: Junhan Hu
tags:
  - robotics
  - control
mathjax: true
date: 2020-05-20 01:30:00
---

## Abstractions and Approximations

We have made some assumptions so far

* Dynamics, $\dot x=u$, **NOT even close to being reasonable!**
* Sensors, we can measure distance and angle

Recall teh unicycle model, we want to our system behave like $\dot x=u $

How? A Layered Architercture

* Navigation system can be decoupled along 3 levels of abstraction:
  * Strategic Level: Where should the goal points be (Not in this course)
    * Dijkstra, A\*, D\*, RRT…
  * Operational Level: which direction to move (go-to-goal and avoid-obstacles)
  * Tactical Level: How to make the robot move in those direction (control design)

## Transforming the Unicycle

The unicycle model
$$
\begin{array}{l}
\dot{x}=v \cos \phi \\
\dot{y}=v \sin \phi \\
\dot{\phi}=\omega
\end{array}
$$
What if we ignored the orientation and picked a different point on the robot as the point we care about

And now the $u_1,u_2$ would directly related to $v$ and $w$

Before: Use a Planner and Tracker

After: Use a Planner and Transformer and DO NOT need a PID controller for lower control

---

Can this method applied to other kind of robots? **YES**

Car-Like robots, Segway robot, Fixed-Wing aircraft, Underwater glider

Common: all the robots involves POSE:

* Position
* Heading

Almost everything with pose is almost a unicycle

## Further

Nonlinear system, Optimal Control minimize some specific cost

Machine Learning. good for optimal control

Perception and Mapping

High-Level AI

## Conclusion

Punchline

1. We need a **model**, it should be rich enough to be relevant yet simple enough to be useful
2. **Feedback** control should be used to guarantee stability, tracking and robustness
3. **Architectures**: plan for simple systems, execute on the real system

