---
title: Vision Based SLAM a review
author: Junhan Hu
tags:
  - ov
  - slam
mathjax: true
date: 2019-1-6
categories:
  - Robotics
---

## 1 Introduction

SLAM builds a map and localize the sensor in the map with a strong focus on **real-time operation**.

Camera: cheap and provide rich information of the environment.

* Monocular camera, cheapest and smallest camera
  * depth is not observable
  * scale drift and mail fail if performing pure rotations
* RGB-D camera, all these issue can be solved.
  * Outdoor performance is not good. Usually used in indoor environment

<!-- more -->

### 1.1 Main Idea

> At its heart, SLAM is an **optimization problem**, where the goal is to compute the best configuration of camera poses and point positions in order to **minimize reprojection error** (the difference between a point's tracked location and where it is expected to be given the camera pose estimate, over all points). —from [Kudan](https://www.kudan.io/post/an-introduction-to-simultaneous-localisation-and-mapping)

The optimization method: Bundle adjustment, iteratively approaches the minimum error for the whole system. 

* Problem: time consuming to find the best solution
* But with the help of multi-core machine, this problem was solved

Another essential technique: relocalization

### 1.2 How it Works

1. Read sensor data
2. Front end: VO
3. Back end: Optimization
4. Loop Closing: Correct the trajactory
5. Mapping

## 2 SLAM type

### 2.0 SLAM Framework

* Front end: Vision odometry, estimate camera’s motion based on 2 frame
  * Stereo
  * Double
  * RGB-D
* Back end: Optimization and calculate the map
  * Filter: KF EKF
  * Optimization : graph, g2o..

### 2.1 Stereo SLAM

Most modern stereo SLAM systems are **keyframe-based** and perform **BA optimization**

### 2.2 RGB-D SLAM

KinectFusion is the earliest RGB-D SLAM system. This method track the camera pose using **ICP**

Endres’ open-source system is a feature-based system.

* Front end: compute frame to frame motion by feature matching ICP
* Back end: pose-graph optimization

calculate pose by *solvepnp*

* objectPoints - 世界坐标系下的控制点的坐标，vector<Point3f>的数据类型在这里可以使用
* imagePoints - 在图像坐标系下对应的控制点的坐标。vector<Point2f>在这里可以使用