---
title: MIT EECS 导论课 1
author: Junhan Hu
tags: [cs]
mathjax: true
date: 2020-03-17 17:09:00
---

# 导论

## 1 学习目标

MIT EECS的导论课, 以Robotics为切入点进行普及性的教育, 课程主要分为四个专题

* 软件工程
* 信号与系统
* 电子电路
* 概率与规划

整个课程的目的是让学生能够appreciate工程中的抽象和设计, 能够理解数学模型的重要性, 并利用建模来解决问题, 并给学生一些实验课程来体验四个专题中的内容

<!-- more -->

> 我觉得对于刚入学的本科生来说这一门非常好的课程, 让学生了解到专业中真正重要的东西和所要解决问题的本质, 可能任何一个工科的学生都可以学习一下. 我大一时没有意识去主动接触这些优秀的, 真正为学生着想的公开课, 真是非常可惜. 虽然其中一些能力也在实践或者课程中慢慢学到了, 但我相信一个优秀的导论课程会让整个大学时期都少点迷茫, 多点实践.

## 2 模块化, 抽象与建模

为什么要抽象和模块化? 这在数学\工程\计算机中都有很多应用

1. 因为要处理的东西很复杂
2. 人处理复杂性的能力较弱
3. 分而治之

想象一个例子: 要造一个轮式机器人, 运动到离灯泡一定距离时停止移动. 这其中就会用到光敏电阻来检测到灯泡的距离, 但是课中不会介绍光敏电阻背后的物理原理, 这其实就是一种抽象了. 在抽象和模块化的过程中, 我们要考虑一些其他的问题

### 抽象层级

作为工程师, 很重要的一个工作是将一系列所拥有的组件进行标准化然后进行构建系统. 标准化的好处是提高效率(作为人的理解效率和作为生产的制造效率), 标准化之后可能的**设计空间**就变小了. 这些能更快理解一个系统, 更好地构建一个系统. 层级越高, 设计越简单, 但是设计空间也就越小

### 模型

建模的最困难之处在于要决定对哪些属性建模, 忽略哪些属性. 

另一个难点在于确定模型是否是确定性的, 还是要把模型设成概率型的.

模型大致可以分为以下几种

* 分析模型: 已经给定了一个系统, 我们要做的就是分析这个系统, 计算理论上的结果

* 合成模型: 描述输入输出, 让计算机在可能的空间中搜寻这个系统

* **内部模型(internal model): 内部有个模型, 也会根据外部环境来更新内部的环境. 类似于SLAM**

  > 对于机器人来说, 我觉得第三种应该是最重要的, 因为机器人所在的环境是真实地比较多变的, 机器人的大部分工作都是在处理不定性的问题, 所以

## 3 嵌入式编程系统

不同的模型与抽象适合不同的任务, 这里主要介绍的是与外部环境交互的软件系统的不同策略

主要的交互就是3步

1. 感知环境
2. **计算所要做的工作**
3. 做出改变

### 驱动方式

主要存在以下几种驱动方式

* 序列化的, 步骤都已经事先定义好了
* 事件驱动, 利用回调函数来完成工作