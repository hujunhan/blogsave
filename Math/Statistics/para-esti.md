---
title: 参数估计简述
author: Junhan Hu
tags: [statistics]
mathjax: true
categories:
- Math
- Statistics
date: 2019-7-14 20:20:00
---

## 基本概念

* 估计量：用来估计总体参数的统计量
  * 求法：矩估计、最大似然估计法
* 估计值：根据一个样本算出来的统计量的值
* 点估计：用样本统计量$\hat{\theta}$的某个取值作为总体参数$\theta$的估计值
* 区间估计：在**点估计的基础**上，给出总体参数的一个**区间范围**
* 置信区间：在区间估计中，由样本统计量构造的总体参数的估计区间
* 对参数估计的评价
  * 无偏，$E(\hat{\theta})=\theta$
  * 更有效，$D(\hat{\theta_1})<D(\hat{\theta_2})$
  * 一致性，$\hat{\theta}$依概率收敛于$\theta$

## 矩估计

> 矩：所考虑的随机变量的幂的期望值
>
> * 一阶矩：期望，$E(x)=\int_{-\infty}^{\infty} x f(x) d x$
>
> * 二阶矩：方差，$\operatorname{Var}(x)=\int_{-\infty}^{\infty}[x-E(x)]^{2} f(x) d x$
>
> * 三阶矩：偏态，$S(x)=\int_{-\infty}^{\infty}[x-E(x)]^{3} f(x) d x$
>
> * 样本矩：$\mu_{n}^{\prime} \approx \frac{1}{N} \sum_{i=1}^{N} X_{i}^{n}$
>
>   通过这种方法求矩不需要先估计其概率分布

用样本矩估计相应的总体矩，用样本矩的函数聚集总体矩相应的函数

> e.g. 已知分布函数$f(x;\theta)$，和一些样本$X_i$
>
> 1. 求出$f$的期望\方差，其中有$\theta$
> 2. 求出样本的期望\方差，是具体的数字或者$X_i$中的信息
> 3. 用那些信息表示$\theta$



