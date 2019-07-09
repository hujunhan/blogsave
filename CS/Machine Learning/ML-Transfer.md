---
title: ML:Transfer Learning
author: Junhan Hu
tags: [ml]
mathjax: true
categories:
- CS
- Machine Learning
date: 2019-4-15 19:47:00
---

## 1 What is Transfer Learning

> Transfer learning is a machine learning technique where a model trained on one task is re-purposed on a second related task.

For example, if I already have a fine trained model for detecting dog and cat, and now I want to train a model can detect different kinds of dogs, I don’t need to train the model from scratch. Just use the pre-trained model and train the last few layers’ neural.

<!-- more -->

## 2 How to use Transfer Learning

Two common approaches:

* Develop Model : If you have **large dataset** on a similar problem and willing to train the model **yourself**.
* Pre-trained Model : If you don’t have enough data to train your model so you can download some **pre-trained model** released by some **research institutions**.

## 3 When to use Transfer Learning

![transfer-learning](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/transfer-learning.png)

