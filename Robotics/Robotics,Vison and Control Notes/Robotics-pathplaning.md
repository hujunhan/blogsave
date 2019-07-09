---
title: Robotics-Path Planning
author: Junhan Hu
tags: [robotics,path,planning]
mathjax: true
categories:
- Robotics
- Robotics,Vison and Control Notes
date: 2019-3-12
---

## Compare Obstacle Avoidance Algorithm

### 1 Bug algorithms

![bug-algorithm](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/bug-algorithm.png)

* Simple
* Non optimal
* May be trapped in maze structures

<!-- more -->

### 2 Potential Field

|                     Attractive Potential                     |                     Repulsive Potential                      |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| ![attractive-potential](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/attractive-potential.png) | ![repulsive-potential](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/repulsive-potential.png) |

Combine Attractive Potential and Repulsive Potential

![combine](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/combine-att-rep.png)

* Good for static and completely known environment

* Bad: may lead to a **local minimum** point

  ![local-minimum](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/local-minimum.png)

### 3 D*

> D* is an extension of the A* algorithm for finding **minimum cost paths** through a graph

* Support incremental **replanning**

### 4 Roadmap methods

