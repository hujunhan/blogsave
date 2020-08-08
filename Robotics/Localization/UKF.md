---
title: 无迹卡尔曼滤波
author: Junhan Hu
tags:
  - robotics
mathjax: true
date: 2020-7-18 14:00:21 
---

## Why

既然扩展卡尔曼滤波可以解决非线性问题，为什么还要提出无迹卡尔曼滤波呢？

**性能**：在扩展卡尔曼滤波中，我们只使用了**一个点**展开来线性化，这就导致了这种估计方法的效果不佳

**更好的方法**：用许多点来近似

**Trade-Off**： 如果使用所有的点来近似，那就又会要求太多的计算资源，因此我们只用少量的计算资源获取大大提高的精度

## How

选择Sigma Points：用少数几个点来表示整个分布，用的点越多，近似就越精确

高斯分布在经过一个非线性变换之后就不再是高斯分布了，所以在这里引入一个Unscented Transform来完成这个变换任务

1. 计算一个Sigma Point的集合

   通常来说，如果系统是N维的，那么Sigma Point的个数选择$2N+1$
   $$
   \begin{aligned}
   X ^{[0]} &=\mu \\
   X ^{[i]} &=\mu+(\sqrt{(n+\lambda) \Sigma})_{i} \text { for } i=1, \ldots, n \\
   X ^{[i]} &=\mu-(\sqrt{(n+\lambda) \Sigma})_{i-n} \quad \text { for } i=n+1, \ldots, 2 n
   \end{aligned}
   $$
   其中$\Sigma$是协方差矩阵，$\lambda$是一个扩张系数（一般选择$3-n$），$X$是Sigma Point矩阵，每一行都是Sigma Point的集合。

   如果系统是2维的，那么$X$就是$2\times5$的大小

2. 给每个Sigma Point赋予不同的权重
   $$
   \begin{aligned}
   w^{[0]} &=\frac{\lambda}{n+\lambda} \\
   w^{[i]} &=\frac{1}{2(n+\lambda)} \quad \text { for } i=1, \ldots, 2 n
   \end{aligned}
   $$
   
3. 将这些点做一个非线性变换$g(x)$

4. 变换后的点计算高斯

5. 计算新分布的均值和方差
   $$
   \begin{aligned}
   \mu^{\prime} &=\sum_{i=0}^{2 n} w^{[i]} g\left( X ^{[i]}\right) \\
   \Sigma^{\prime} &=\sum_{i=0}^{2 n} w^{[i]}\left(g\left( X ^{[i]}\right)-\mu^{\prime}\right)\left(g\left( X ^{[i]}\right)-\mu^{\prime}\right)^{T}
   \end{aligned}
   $$
   

## 卡尔曼滤波框架

1. 预测步骤：用上一节提到的几个公式计算新的期望和方差
2. 更新步骤：我们可以选择采用之前生成的Sigma Point

## Ref

https://towardsdatascience.com/the-unscented-kalman-filter-anything-ekf-can-do-i-can-do-it-better-ce7c773cf88d