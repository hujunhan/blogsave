---
title: Apple's 3D Face ID Tech
author: Junhan Hu
tags:
  - skills
  - apple
mathjax: true
categories:
  - Life
date: 2019-07-29 21:59:00
---

## Overview

Apple use Face ID as an unlocking method first in iPhone X, it use a bunch of technology to improve its performance.

* Front facing **depth-camera**
* **infrared camera**
* **Deep learning**

I was so interested in this tech especially how can Apple apply deep learning with little data and limited compute resource in mobile phone.

<!-- more -->

## How it Works?

Apple release a whitepaper about Face ID, so we can learn something from it.

The whole security system is called **TrueDepth camera system**

* **map the geometry** of your face
* **confirms attention** by detecting the direction of your gaze

As for users, they need to do something similar to Touch ID:

1. Register users’ face
   1. Look at the phone
   2. slowly rotate the head
2. DONE!

As we can see, the process is pretty simple and quick.

---

The problem here for **normal classification** procedure are

* The raw data is limited
* Computing resource is limited
* Lack of negative samples

So I think Apple use another method to solve this problem

## Possible Way

Above all, I think **extracting features** on faces is the very first thing to do. In this way, device can get a **small vector** rather than a huge image to **train** some classification or neural networks **in a short time**

**siamese-like convolutional neural network** might be a good way to do the job

> ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/siamese-neural-network.png)
>
> Two network share the weights
>
> The main purpose of this work is to value the **similarity of two input**

So Apple can 

1. **pre-train** such a model that can detect different feature in users’ face
2. Get users’ face when they register Face ID and set it as *input 1*
3. When users need to unlock their devices or use Face ID to purchase something, the camera get a image as *input 2*
4. Calculate the similarity between *input 1* and *input 2*

## Ref

[Towards Data Science Blog](https://towardsdatascience.com/how-i-implemented-iphone-xs-faceid-using-deep-learning-in-python-d5dbaa128e1d)

[Face ID White Paper](https://images.apple.com/business/docs/FaceID_Security_Guide.pdf)

