---
title: Robotics-BioCopter
author: Junhan Hu
tags: [robotics,hide]
mathjax: true
categories:
- Robotics
- Project
date: 2019-3-11 9:42:00
---

## 1 Introduction (Prepare)

### 1.1 Goal

Build a bicopter(a kind of frame) like this

![biocopter](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/biocopter.png)

<!-- more -->

### 1.2 Pros & Cons

* Cheap : only 2 servos and 2 motors
* Unstable
* Hard to tune

### 1.3 Hardware

* Servo $\times$ 2 
* Motor $\times$ 2
* Flight Controller Board $\times​$ 1 : SP Racing F4 Pro
* Transmitter $\times$ 1 : FS-i6
  * Receiver (Rx) $\times$ 1 : FS-iA6

### 1.4 Software

* CleanFlight / BeteFlight / iNav (based on similar code)

## 2 Assemble

* 电调校准，首先要将油门信号调到最大，然后上电，然后油门信号调到最低。校准完毕

## 3 Software Setup

### 3.1 Betaflight

* Setup servo pin map [MORE](https://github.com/betaflight/betaflight/wiki/Servos-&-SERVO_TILT-for-3.1) 

  ```bash
  resource #list all avaliable pin map
  resource motor 3 none #we just need 2 motor, so we can free motor 3 & 4, remember the pin of motor 3 & 4 
  resource servo 1 a06 #setup the pin for servo 1 & 2
  save #all the changes will lose if you don't save
  
  ```




## Bib

* Receivers Type: PWM(avoid), PPM(main), Serial(advanced) [MORE](https://github.com/betaflight/betaflight/blob/master/docs/Rx.md) 

