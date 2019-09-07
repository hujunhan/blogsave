---
title: First Step to Optimization
author: Junhan Hu
tags: [model]
mathjax: true
categories:
- Math
- Modeling
date: 2019-09-07 15:52:00
---

## Overview

### What is an optimization problem

Goal: Find the *best* solution to a problem out of a large set of possible solutions

Elements:

* objective: the goal, the value you want to optimize

  We need to define a function to calculates the value

* constrains: the restrictions on the set of possible solution

## Linear Optimization

Computing the best solution to a problem modeled as a set of linear relationships

These problems often arise in engineering disciplines

<!-- more -->

### Example

Goal: minimize $3x+4y$ with following constrains

| *x* + 2*y* |  ≤   |  14  |
| :--------: | :--: | :--: |
| 3*x* – *y* |  ≥   |  0   |
| *x* – *y*  |  ≤   |  2   |

## Constraint Optimization

Identifying feasible solutions out of a large set of candidates, where problem can be  modeled in terms of **arbitrary constrains**

This optimization **focus on the constraints and variable**s rather than the objective function. It just want to find out a **feasible solution**, not a optimal solution

### Example 1 Employee Scheduling

Problem: employee scheduling

Background: create weekly schedules for their employees. 

> e.g.  a company runs three 8-hour shifts per day and assigns three of its four employees to different shifts each day, while giving the fourth the day off
>
> possible schedules: $4!=24$
>
> possible schedules in a week: $24^7$
>
> So we need to narrow down the solution space 

## Routing

Find efficient paths for transporting items through a complex network. 

The network usually represented by a graph like the one below

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/opti-routing.png)

There are mainly 2 types of routing problem:

* node-routing: the goal is to visit the node

* arc-routing: the goal is to visit the arc

e.g.1 Google Map’s Street view: Google need to construct the shortest route for the team to reduce the travel length. This is a **arc-routing problem**

e.g.2 A company needs to deliver packages to various locations using a fleet of vehicles. Each arc has a weight, the problem is to find a set of paths that **include every destination while minimizing the total cost**. This is a node-routing problem

TODO: ADD MORE DETAILS

## Pack

The goal is to find the best way to pack a set of items of given sizes into containers with fixed capacities

There are mainly 2 packing problems:

* Knapack problems

  multiple containers (called knapack), items have *values* as well as *sizes*,

  goal: maximize the total value

* bin packing

  multiple containers (called bin) with equal capacity. 

  goal: minimizing the number of bins

##  Assignment Problem

A group of workers  has to perform a set of tasks. For each worker and task, there is a fixed cost for that worker to perform the task. The goal is to minimize the total cost.

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/opti-assi.png)

And there will be a cost matrix 

## Scheduling 

### The Job Shop Problem

Multiple jobs are processed on several machines. Each job consists of a sequence of tasks, which must be performed in a given order, and each task must be processed on a specific machine.

Several constraints :

* No task for a job can be started until the previous task for that job is completed.
* A machine can only work on one task one time
* A task, once started, must run to completion

For each task, it can be labeled by a pair of numbers $(m,p)$ where $m$ is the number of the machine that the task must processed and $p$ is the processing time of the task

e.g. in a factory, there are 3 jobs

* job 0 = [(0, 3), (1, 2), (2, 2)]
* job 1 = [(0, 2), (2, 1), (1, 4)]
* job 2 = [(1, 4), (2, 3)]

and the  solution can be illustrate like this 

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/opti-jsp.png)





