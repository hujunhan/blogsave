---
title: Flight Controller
author: Junhan Hu
tags: [robotics,flight-controller]
mathjax: true
categories:
- Robotics
- Project
date: 2019-4-13 14:56:00
---

## 1 Introduction

This project was brought to make a flight controller from scratch.

I want to learn from the process so the flight controller will be more general. However the model of the flight and selection of controller platform(STM32/Arduino/Linux ) will make the general task more difficult.

<!-- more -->

Before the program, I have no experience in flight controller programming. So I would learn from other project shared on Github.com. 

## 2 Learning from Others

### 2.1 HackFlight

As a education oriented project, *[Hackflight](https://github.com/simondlevy/Hackflight) is simple, platform-independent, header-only C++ firmware for multirotor flight controllers and simulators* 

#### 2.1.1 Unit

First of all, HackFlight defined some standard units to write simpler code.

* Distance $ m/s $
* Time $ s $
* Euler angle $ radians $
* Stick demand interval $ [-1,1 ] $
* Motor demands $ [0,1] $
* Quaternions interval $ [-1,1] $

#### 2.1.2 Programming Structure

This project is a practice of C++ for it’s speed and object-oriented features

HackFlight build several separate class to provide basic function of a controller.

* Board class, specifies 4 abstract method a flight must implement
  * Sending commands to the motors
  * Getting current quaternion from the IMU
  * Getting gyrometer rates from the IMU
  * Getting the current time
* Receiver class perform basic function associate with R/C control
* Mixer class that can be subclassed by specific mixer like QuadX / Bicopter
* PID_Controller class specific the PID value appropriate for your model 

#### 2.1.3 Design Principle

![hackflight-dataflow](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20190419122228.png)

There are 2 basic data type:

* State: State is updated by sensors which read IMU sensors and calculate **quaternion** 
* Demands

There are 2 basic fly mode: All a kind of PID controller

* Self-Level Mode: Auto mode, hold the angle or keep the level when there is no input. The input is regarded as the *distance* you want to move
* Rate Mode: Manual/Acro mode. The input is taken as the *speed* you want to move

