---
title: Hardware Transmitter
author: Junhan Hu
tags: [hardware,transmitter]
mathjax: true
categories:
- Robotics
- Hardware
date: 2019-3-15 20:36:00
---

## 1 简介

针对一个富斯FS-i6发射机及其接收机来学习接收机方面的知识

### 1.1 发射机

![flysky-transmitter](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/transmitter.png)

<!-- more -->

### 1.2 接收机

* 型号：FS-iA6B
* 调制方式：GFSK
* 数据分辨率：1024级
* 电源标准：4.0-6.5V DC

![receiver](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/receiver.png)



### 1.3 基本操作

* 开机：
  1. 先开发射机Tx
  2. 再开接收机Rx
  3. 正常情况下接收机红色指示灯常亮
* 关机
  1. 先关接收机Rx
  2. 再关发射机Tx

## 2 功能介绍

### 2.1 飞行控制

* 油门分左手和右手，我选择的是右手油门
* 左手的摇杆控制的就是飞行器的倾斜和上下俯仰
* 右手的摇杆控制飞机水平左右旋转和油门加速减速

### 2.2 逆转修正

当舵机运动方向与预期相反时，可以使用此功能修正、

### 2.3 油门曲线设置

针对油门操纵杆的动作调整油门输出曲线，使得发动机达到最佳状态

### 2.4 混控功能(Mix)

当接收机收不到信号或者失去控制时，舵机摆臂需要保持的位置

## 3 注意

* 发射机天线应和模型垂直，而不是指着飞行器（参考路由器天线摆放）

* 一共有4组微调杆
  * 通道1：副翼
  * 通道2：升降
  * 通道3：油门
  * 通道4：舵机中位

* 为保持控制质量，应尽量将接收机的两个天线保持垂直

  ![antena-place](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/antena-place.png)

* 接收机对码(Binding)

  1. 发射机选择**接收机设置**功能，选择**对码**进入对码状态
  2. 用对码线插入B/VCC通道
  3. 用4.0-6.5V DC电源插入CH1-CH6任意通道，进入对码状态，此时LED闪烁
  4. 对码成功，发射机自动退出对码状态
  5. 拔掉对码线

