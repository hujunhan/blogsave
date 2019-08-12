---
title: Brachistochrone Curve
author: Junhan Hu
tags: [math]
mathjax: true
categories:
- Math
- Physics
date: 2019-08-12 18:28:00
---

## 问题描述

最速降线或捷线问题是历史上第一个出现的变分法问题，也是变分法发展的一个标志。此问题是1696年约翰·伯努利在写给他哥哥雅克布·伯努利的一封公开信中提出的。问题的提法是：设A和B是铅直平面上不在同一铅直线上的两点，在所有连接A和B的平面曲线中，求出一条曲线，使仅受重力作用且初速度为零的质点从A点到B点沿这条曲线运动时所需时间最短

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/Brachistochrone.gif)

## 物理学角度的求解

1. 由于能量守恒，所以粒子的速度正比于到顶端的距离的平方根

2. 所以可以把粒子看成光子，根据**费马原理**，用时最短的路径可以用**斯涅尔定理**解出

   所以也可以这样描述这条曲线：处处满足斯涅尔定理
   $$
   \frac{sin(\theta)}{\sqrt{y}}=constant
   $$

3. 上述的曲线就是旋轮线

   ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/quickest-down-how.png)

   

