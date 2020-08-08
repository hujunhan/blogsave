---
title: labuladong学习笔记
author: Junhan Hu
tags: [DS]
mathjax: true
categories:
- CS
- DS & Algorithm
date: 2020-07-13 21:30:00
---

## Why

我从一个礼拜左右前开始刷题，到目前刷了三十几道，感觉逐渐有点上手，但没有一个系统的框架。在刷一道二分法的题目时，看到了labuladong的笔记，感觉思路清晰，值得学习。之后还发现他总结了一系列的算法框架并写了文章，所以在这里记录下阅读时的收获

## 动态规划

目标：**求最值**。动态规划是运筹学中的最优化方法，在CS中应用较多

核心思想：**穷举**。把所有的可行答案穷举并找最值

难点：存在“重叠子问题”，直接暴力穷举效率低下。需要记**录下一些中间过程**节省计算量

方法：找到**最优子结构**，并列出正确的**状态转移方程**。

* 技巧：状态压缩，每次只记录必要的数据

## 回溯法

实际上是决策树的遍历过程，要考虑三个问题

1. 路径
2. 选择列表
3. 结束条件

```pseudocode
result = []
def backtrack(路径, 选择列表):
    if 满足结束条件:
        result.add(路径)
        return

    for 选择 in 选择列表:
        做选择
        backtrack(路径, 选择列表)
        撤销选择
```

在全排列问题中

1. 路径就是已经用掉的数字
2. 选择列表就是还剩下的数字
3. 结束条件就是列表为空

## 数组

数组主要就是考察插入、删除和搜索

为了节省内存空间，利用in-place操作可以达到$O(1)$的空间复杂度

* 为了实验in-place的操作，往往会使用**双指针**

## 链表

单向链表：遍历、插入、删除

双向链表：相比于单向链表，在插入和删除时要更加小心。但是在删除时会更加容易，不需要$O(N)$的时间复杂度去找到上一个结点

在知道**前一个**结点的情况下，链表的插入和删除都是非常快的

双指针技巧同样非常有用。相比数组更加容易出错

* 要多检查是否结点为空
* 多检查几遍确保循环能够正确结束
  * 多尝试一些边界条件




