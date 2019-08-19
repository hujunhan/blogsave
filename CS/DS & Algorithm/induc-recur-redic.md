---
title: 算法设计——推导、递归、规约
author: Junhan Hu
tags: [DS]
mathjax: true
categories:
- CS
- DS & Algorithm
date: 2019-08-12 15:47:00
---

## Overview

### 规约

对问题进行转化，将未知的问题转化为能够解决的问题，其中设计对问题的输入输出的转换

### 推导

类似于数学归纳法，我们要证明某个命题是正确的，先证明基础情况，然后证明命题的递推可以正常工作

### 递归

一个函数调用自身，要确保的是对于基础情况（不递归的情况）可以正常工作

<!-- more -->

## 三者之间的关系

* 推导和递归相对应
  * 推导是$n-1\to n$ 递归是$n\to n-1$
  * 这意味着这两者可以相互转化，通常情况下非递归的方式要好一些，因为运行速度更快，而且没有用栈去实现，避免了溢出
* 推导和递归都属于规约
  * 都是将一个问题变成另一个只是规模减小的相同问题

## 例子

### 排序

目的是对排序问题进行reduce

* reduce成两个规模为原来一半的问题，得到了归并排序
* 每次reduce一个元素，得到了插入排序
* 找到某个元素，放在位置k上，得到了快排

### 名人问题

从一系列有依赖关系的集合中找到那个依赖关系最开始元素，比如多线程环境下的线程依赖

目的也是进行reduce

* 每次reduce一个人，暴力求解

  ```python
  def naive_celeb(G):
      n = len(G)
      for u in range(n):  # For every candidate...
          for v in range(n):  # For everyone else...
              if u == v: continue  # Same person? Skip.
              if G[u][v]: break  # Candidate knows other
              if not G[v][u]: break  # Other doesn't know candidate
          	else:
              	return u  # No breaks? Celebrity!
      return None  # Couldn't find anyone
  ```

* 问题也可以理解为找一个非名人(u)，也就是找到一个人(u)，他要么认识其他某个人(v)，要么某个人(v)不认识他

  ```python
  def celeb(G):
      n = len(G)
      u, v = 0, 1  # The first two
      for c in range(2, n + 1):  # Others to check
          if G[u][v]:
              u = c  # u knows v? Replace u
          else:
              v = c  # Otherwise, replace v
      if u == n:
          c = v  # u was replaced last; use v
      else:
          c = u  # Otherwise, u is a candidate
      for v in range(n):  # For everyone else...
          if c == v: continue  # Same person? Skip.
          if G[c][v]: break  # Candidate knows other
          if not G[v][c]: break  # Other doesn't know candidate
      else:
          return c  # No breaks? Celebrity!
      return None  # Couldn't find anyone
  ```

### 拓扑排序

Linux系统中软件的安装，检测依赖

* 递归，每次去掉一个节点，解决剩下的拓扑排序，在将去掉的节点插入合适的位置

  ```python
  def naive_topsort(G, S=None):
      if S is None: S = set(G)  # Default: All nodes
      if len(S) == 1: return list(S)  # Base case, single node
      v = S.pop()  # Reduction: Remove a node
      seq = naive_topsort(G, S)  # Recursion (assumption), n-1
      min_i = 0
      for i, u in enumerate(seq):
          if v in G[u]: min_i = i + 1  # After all dependencies
      seq.insert(min_i, v)
      return seq
  
  G = {'a': set('bf'), 'b': set('cdf'),'c': set('d'), 'd': set('ef'), 'e': set('f'), 'f': set()}
  print naive_topsort(G) # ['a', 'b', 'c', 'd', 'e', 'f']
  ```

* 规约，每次从图中删除一个入度为0的节点

  ```python
  def topsort(G):
      count = dict((u, 0) for u in G)  # The in-degree for each node
      for u in G:
          for v in G[u]:
              count[v] += 1  # Count every in-edge
      Q = [u for u in G if count[u] == 0]  # Valid initial nodes
      S = []  # The result
      while Q:  # While we have start nodes...
          u = Q.pop()  # Pick one
          S.append(u)  # Use it as first of the rest
          for v in G[u]:
              count[v] -= 1  # "Uncount" its out-edges
              if count[v] == 0:  # New valid start nodes?
                  Q.append(v)  # Deal with them next
      return S
  ```

## 如何解决一个问题

1. 首先要搞明白你要解决的问题

   * 输入输出，将问题抽象为熟悉的结构

2. 寻找一个规约方式

   将问题转化成另一个能够解决的问题，通过reduce一个元素

3. 有没有其他的重要的假设条件

