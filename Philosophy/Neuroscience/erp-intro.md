---
title: ERP Overview
author: Junhan Hu
tags: [neuroscience]
mathjax: true
date: 2020-03-31 13:44:00
---

## What is ERP?

[ref](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3016705/)

**定义**：Event-related potentials (ERPs) 事件相关电位，是由特定刺激而导致的脑中的电位。宏观反映了大量定向相同的神经元（百万级别）在处理信息时同步放电产生的突触电位的总和。

**前因**：ERP可以由多种事件诱发：感官上的，认知的，运动事件

**后果**：在人类大脑中，ERP主要可以分为两类

* Early waves，一个波峰在刺激发生之后的100毫秒左右。这种ERP是**外源性**的，因为这个响应主要取决于外部刺激的物理性质
* Later parts，在之后的响应一般是**内源性**的、认知性的

**表现形式**：和latency相关的amplitude，eeg信号

<!-- more -->

## Calculation

通过EEG记录了多次大脑对单一刺激的响应。但是由于EEG记录过程中，有随机的脑活动和其他生物信号以及电磁干扰（比如电路噪声、荧光灯）等会对记录的ERP信号造成噪声干扰。将多次响应平均在一起，可以达到去噪的效果，求出平均的大脑响应

ERP的计算有两个假设

1. 所要求的ERP信号是有着不变得到延迟和形状的
2. 噪声是零均值的

## Different ERP Waveforms

下面所说的信号形式中P for Positive，N for Negative，数字代表延迟（毫秒）

按顺序出现

1. P50
2. N100
3. P200

## Analysis

We want to compute from **Raw Data** to **ERP**

原始数据： 低信噪比； 期望的ERP：高信噪比、

处理顺序

1. 清理、手工移除

   去除眼动、眨眼等

2.   滤波

3. 切片

4. Baseline Correction

5. 平均