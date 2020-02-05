---
title: TRF计算
author: Junhan Hu
tags: [neuroscience]
mathjax: true
categories:
  - Philosophy
date: 2020-02-5 22:42:00
---

## 系统的表示方法

定义: 对于某个语音刺激(比如说音素), 将大脑假设成一个线性时不变系统, 大脑的整体响应是对语音刺激的响应加上其他的噪声(实验中应该尽量减小噪声)
$$
R(t)=TRF(t)*S(t)+Noise(t)
$$
$𝑅(𝑡)$表示大脑总的神经响应Response , $𝑇𝑅𝐹$表示时间响应函数, $*$ 表示卷积, $𝑆(𝑡)$表示语音刺激Stimulus, $Noise(𝑡)$表示测量过程中引入的噪声干扰

## 已知条件

我们的最终目的是求出$TRF(t)$函数, 现在已知的有

* $S(t)$, 通过对播放的语音信号进行处理, 获取各个音素开始的时间, 我们可以知道语音刺激的函数
* $R(t)$, 通过脑电传感器我们获得了被试者的脑电信号
* 通过滤波函数对脑电信号进行去噪, 获得$R(t)-Noise(t)$

所以我们可以计算出$TRF(t)$, 计算的方法是最小二乘法, 也就是实际脑电信号和通过$TRF$计算出的脑电信号误差要最小.

因为我们获取的脑电信号和播放的语音刺激都是数字信号, 所以我们用离散形式来表示关系. 为了便于表示, 经过滤波之后的脑电信号记为$y(n)$, 语音刺激记为$x(n)$, 时间响应函数记为$h(n)$, 误差项记为$e(n)$, 可以得到
$$
y(n)=x(x)*h(n)+e(n)
$$
为了计算h, 可以将卷积写成矩阵乘积形式:
$$
\left[\begin{array}{c}
{y_{0}} \\
{y_{1}} \\
{\vdots} \\
{y_{N}}
\end{array}\right]=\left[\begin{array}{cccc}
{x_{0}} & {x_{-1}} & {\cdots} & {x_{-k}} \\
{x_{1}} & {x_{0}} & {\cdots} & {x_{-k+1}} \\
{\vdots} & {\vdots} & {\ddots} & {\vdots} \\
{x_{N}} & {x_{N-1}} & {\cdots} & {x_{0}}
\end{array}\right]\left[\begin{array}{c}
{h_{0}} \\
{h_{1}} \\
{\vdots} \\
{h_{k}}
\end{array}\right]+\left[\begin{array}{c}
{e_{0}} \\
{e_{1}} \\
{\vdots} \\
{e_{N}}
\end{array}\right]
$$
其中矩阵的行数$N$表示神经响应的长度

矩阵的列数$k$表示系统的阶数, 也就是神经响应函数的长度

用向量表示为
$$
\vec{y}=X h+\vec{e}
$$


## 最小二乘法

计算方法是让各个误差项的平方和$E_{sum}$最小, 可得
$$
E_{sum}=\sum_{i=0}^{N} e_{i}^{2}=\vec{e}^{T} \vec{e}
$$

又有

$$
\vec{e}^{T}=(\vec{y}-X h)^{T}=h^{T} X^{T}-\vec{y}^{T}
$$

可以得到

$$
\begin{aligned}
E_{sum} &=\vec{e}^{T} \vec{e} \\
&=\left(h^{T} X^{T}-\vec{y}^{T}\right)(\vec{y}-X h) \\
&=\left(h^{T} X^{T} \vec{y}-\vec{h}^{T} X^{T} X h-\vec{y}^{T} \vec{y}+\vec{y}^{T} X h\right)
\end{aligned}
$$
为了取得误差和最小, 我们对上式对$h$求导, 当求导式子等于0时, 误差最小. 因为$h^{T} X^{T} \vec{y}, \vec{h}^{T} X^{T} X h, \vec{y}^{T} X h$都是标量, 所以得到的公式为
$$
\begin{aligned}
\frac{\partial E_{sum}}{\partial h} &=\frac{\partial\left(2 h^{T} X^{T} \vec{y}-h^{T} X^{T} X h-\vec{y}^{T} \vec{y}\right)}{\partial h} \\
&=\frac{\partial\left(2 h^{T} X^{T} \vec{y}\right)}{\partial h}-\frac{\partial\left(h^{T} X^{T} X h\right)}{\partial h}\\
&=\vec{y}^{T} X-h^{T} X^{T} X=0
\end{aligned}
$$
最终我们可以得到
$$
h=\left(X^{T} X\right)^{-1} X^{T} \vec{y}
$$
