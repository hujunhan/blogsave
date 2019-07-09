---
title: Robotics-Force Control
author: Junhan Hu
tags: [control,robotics]
mathjax: true
categories:
- Robotics
- Introduction to Robotics Notes
date: 2019-1-1
---

## 1 Introduction

Mere position control is not suffice is contact is made between end-effector and environment.

So introduce **hybrid position/force controller** to solve the problem. This method is one formalism through which industrial robots might someday be controlled in order to perform tasks requiring force control.

<!-- more -->

## 2 Application of Robots to Assembly Tasks

* Spot welding

* Spray painting

* Pick and place operations

* Future: assembly-line tasks, force is extremely important.

  Currently, the dexterity of manipulators remains **quite low** and limit their appplication in the automated assembly area.

If we can **measure and control contact forces** generated at the hand, we  can **imporove the performance without** using bigger, heavier, and more expensive manipulator.

## Basic Idea

Every manipulation task can be broken down into **subtasks** that are defined by a particular **contact situation** occurring between the manipulator end-effector (or tool) and the work environment. 

With each subtask, we can associate a set of **constrains**

* mechanical
* geometric



