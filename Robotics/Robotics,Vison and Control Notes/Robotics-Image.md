---
title: Robotics-Images and Image Processing
layout: draft
author: Junhan Hu
tags: [robotics,vision]
mathjax: true
categories:
- Robotics
- Robotics,Vison and Control Notes
date: 2019-1-7 17:03:00
---

## 1 Introduction

> A process that transforms one or more input images into an output image.

Main purpose: **enhance** an image for *human* viewing

<!-- more -->

A image is just a matrix.

* Value: `uint8` ,[0-255] (from darkest to brightest)
  * if use complex algorithms, may use floating-point numbers
* Descibe: width $\times$ height

## 2 Useful Algorithms

> Histogram: the number of times each pixel value occurs.

If a picture was under-exposed, the histogram would shift to the left.

Find peak in *nearby* x value: 

## 3 Monadic & Diadic Operations

### 3.1 Monadic

![monadic](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/monadic.png)

A function about single pixel. That is $O [ u , v ] = f ( I [ u , v ] ) , \quad \forall ( u , v ) \in I$

Example:

* convert a color image to a greyscale image
* stretch
* normalize hist

### 3.2 Diadic

Example:

1. chroma-keying: superimpose the image of a person over some background.

   1. gamma encoded image to linear tristimulus value.
   2. mask = g<0.45 (just a example)
   3. mask.*image

   This an important problem in robot vision. But variation is a significant problem in real-world.

2. Provess image sequence and *estimate* the **background**

   1. $\hat { \boldsymbol { B } } \langle k + 1 \rangle \leftarrow \hat { \boldsymbol { B } } \langle k \rangle + c ( \boldsymbol { I } \langle k \rangle - \hat { \boldsymbol { B } } \langle k \rangle )$
      $$
      c ( x ) = \left\{ \begin{aligned} \sigma , & x > \sigma \\ x , & - \sigma \leq x \leq \sigma \\ - \sigma , & x < - \sigma \end{aligned} \right.
      $$

   2. ![diadic](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/diadic.png)


## 4 Spatial Operations

Each pixel in the output image is a function of all pixels in a region
$$
O [ u , v ] = f ( I [ u + i , v + j ] ) , \quad \forall ( i , j ) \in \mathcal { W } , \quad \forall ( u , v ) \in I
$$
Spatial operations are **powerful** for the **variety** of possible function $f ( \cdot )$

### 4.1 Linear

* Smoothing

  * ones(K)

  * gaussian $\mathrm { G } ( u , v ) = \frac { 1 } { 2 \pi \sigma ^ { 2 } } e ^ { - \frac { u ^ { 2 } + v ^ { 2 } } { 2 \sigma ^ { 2 } } }$

    ![gaussian](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/gaussian.png)

* Edge Detection

  * $p ^ { \prime } [ v ] = p [ v ] - p [ v - 1 ]$
  * $p ^ { \prime } [ v ] = \frac { 1 } { 2 } ( p [ v + 1 ] - p [ v - 1 ] )$ 
  * Sobel
  * Canny



