---
title: Robotics-Vision Foundation
layout: draft
author: Junhan Hu
tags: [robotics,vision]
mathjax: true
categories:
- Robotics
- Robotics,Vison and Control Notes
date: 2019-1-7
---

## 1 Introduction

> The light that reaches the eye,or the camera, is a function of the illumination impinging on the scene and the material property known as reflectivity.

<!-- more -->

## 2 Light

Each color is a single frequency or wavelength of electro-magnetic radiation.We perceive the wavelengths between 400 and 700 nm as different colors.

In general, the light we observe can be represented as a function $E(\lambda)$ ,$\lambda$ is the wavelength. This is a function about **power **related to 

* source temperature $T$ (e.g. 4700K)
* Planck’s constant $h$ , Boltzmann’s constant $k$, speed of light $c$
* ……

![black-body-power](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/black-body-power.png)

### 2.1 Absorption

![earth-spectrum](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/earth-spectrum.png)

Spectrum will be changed (be absorbed)

### 2.2 Luminance

The light refl ected from a surface, its luminance, has a spectrum given by
$$
L ( \lambda ) = E ( \lambda ) R ( \lambda )  (W  m ^ { - 2 })
$$
where $R$ is the reflectance

### 2.3 Color

How to measure color? Take $red$ for example:
$$
\rho = \int _ { \lambda } L ( \lambda ) M _ { \mathrm { r } } ( \lambda ) \mathrm { d } \lambda
$$
where $M _ { r } ( \lambda )$ are the spectral response of the red.

## 3 Image Formation

Here we introduce how images are **formed and captured**. 

> a glass or plastic lens forms an image on the surface of a semiconductor chip with an array of light-sensitive devices to convert light to a digital image.

However, in an eye or in a camera, the depth information is lost. This is known as *projection*.

### 3.1 Model

#### 3.1.1 Perspective Camera

convex lens $\frac { 1 } { z _ { 0 } } + \frac { 1 } { z _ { i } } = \frac { 1 } { f }$

In a camera, the image plane (the surface of the sensor chip) is **fixed**. How to solve the problem? $\to$ high-quality camera lens is a compound lens comprising **multiple** glass or plastic lenses.

* central perspective imaging model

  ![perspective-camera](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/perspective-camera.png)

  Map: $\mathrm { P } = ( X , Y , Z ) \to x = f \frac { X } { Z } , y = f \frac { Y } { Z }$

  * $\mathcal { P } : \mathbb { R } ^ { 3 } \mapsto \mathbb { R } ^ { 2 }$
  * straight line $\to$ straight line
  * map is not unique
  * map is not conformal

#### 3.1.2 Mathematical Model

**world** coordinate **homogeneous** form
$$
\tilde { \boldsymbol { P } } = ( X , Y , Z , 1 ) ^ { T }
$$

**image-plane** point **coordinate** 
$$
\tilde { \boldsymbol { p } } = \left( \begin{array} { l l l l } { f } & { 0 } & { 0 } & { 0 } \\ { 0 } & { f } & { 0 } & { 0 } \\ { 0 } & { 0 } & { 1 } & { 0 } \end{array} \right)  \tilde { \boldsymbol { P } }
$$

#### 3.1.3 Discrete Model

![camera-discrete-model](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/camera-discrete-model.png)

---

Notation:

* Principle point: $(u_0,v_0)$
* width and height of each pixel $\rho_w , \rho_h$

So, the pixel coordinate
$$
u = \frac { x } { \rho _ { w } } + u _ { 0 } , v = \frac { y } { \rho _ { h } } + v _ { 0 }
$$
finally, we get 
$$
\tilde { \boldsymbol { p } } = \left( \begin{array} { c c c } { f / \rho _ { w } } & { 0 } & { u _ { 0 } } \\ { 0 } & { f / \rho _ { h } } & { v _ { 0 } } \\ { 0 } & { 0 } & { 1 } \end{array} \right) \left( \begin{array} { c c c c } { 1 } & { 0 } & { 0 } & { 0 } \\ { 0 } & { 1 } & { 0 } & { 0 } \\ { 0 } & { 0 } & { 1 } & { 0 } \end{array} \right) \left( ^ { 0 } T _ { C } \right) ^ { - 1 } \tilde { P }
$$

---

In conclusion, we can describe a projection as a function
$$
\boldsymbol { p } = \mathcal { P } \left( \boldsymbol { P } , \boldsymbol { K } , \boldsymbol { \xi } _ { \mathrm { C } } \right)
$$

* $P​$ is point in the **real world** frame
* $K$ is the camera **parameter** : $f,\rho_w, \rho_h, u_0, v_0$
* $\xi_c$ the **pose** of the camera

### 3.2 Camera Calibration

In practice, some parameter in $K$ is unclear.($f, u_0, v_0$)

So we need to calibrate the camera

