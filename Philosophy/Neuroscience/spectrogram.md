---
title: 时频图计算
author: Junhan Hu
tags: [neuroscience]
mathjax: true
categories:
  - Philosophy
date: 2020-03-08 23:57:00
---

## Intro

利用短时傅里叶变换来计算时频图, 可以观察随着时间变化的频谱信号

基本的计算步骤如下

1. 将信号分割成许多个短的片段, 长度为*NSC=length/N*
2. 将每个片段都用窗函数滤波, 比如hamming窗
3. 指定两个片段之间有50%的交叠
4. 计算每个片段的FFT, 点数为$max(256,2^p)$, 其中$p=log_{2}{NSC}$

