---
title: SSL-Collison Avoidance
author: Junhan Hu
tags: [homework,robotics,hide]
mathjax: true
categories:
- Robotics
- Project
date: 2019-3-4 9:23:00
---

## 1 Introduction

### 1.1 SSL

> The **Small Size league** or F180 league as it is otherwise known, is one of the oldest RoboCup Soccer leagues. It focuses on the problem of intelligent multi-robot/agent cooperation and control in a highly dynamic environment with a hybrid centralized/distributed system.
>
> <!-- more -->

### 1.2 Rule

* the robot must fit within an **180 mm** diameter circle
* and must be no higher than **15 cm**
* play soccer with an orange golf ball
* field is **12 m** long by **9 m** wide

### 1.3 How it Works?

* All objects on the field are **tracked** by a vision system called **SLL-Vision**

* Robots are controlled by **off-field computers**
  * Communications is wireless
  * Uses dedicated commercial radio units

## 2 Software Enviroments

### 2.1 GrSim

> The simulator grSim was contributed to the SSL community by Parsian. It performs a physical simulation of SSL robots and publishes SSL-Vision network packages.

* Receiving and Sending data using Protobuf library
* [Install](https://github.com/RoboCup-SSL/grSim/blob/master/INSTALL.md)

### 2.2 Protobuf

> Protocol Buffers (a.k.a., protobuf) are Google's language-neutral, platform-neutral, **extensible mechanism for serializing structured data**. 

* Protobuf supports many language [(C++, Java, Python…)](https://github.com/protocolbuffers/protobuf#protobuf-runtime-installation)

* Python based protobuf programming **maybe** the easiest

  1. Download binary released [protoc.exe](https://github.com/protocolbuffers/protobuf/releases) or [build from source](https://github.com/protocolbuffers/protobuf/blob/master/src/README.md)

  2. Define your protocol format

  3. Compile your protocol buffers

     ```bash
     protoc -I=$SRC_DIR --python_out=$DST_DIR $SRC_DIR/xxx.proto
     ## If you compile "xxx.proto", the result should be "xxx_pb2.py"
     ```

  4. Install library for your python enviroment

     ```bash
     pip install protobuf
     ## Notice: the version of protobuf library must match the version of the compile tool(protoc.exe)
     ```

  5. Start programming

     ```python
     import xxx_pb2
     ......
     ```

      For furthur study, read [Google's doc](https://developers.google.com/protocol-buffers/docs/pythontutorial)

### 2.3 Packet

protobuf will be used only in simulation. In real enviroments, we need to send a byte-format package to control the robots' speed and action.

And the package is defined below (image lost)

 In our project, we just need to specify the speed of robot.

```python
commands = b'\xff\x00\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x07\x00\x00\x00'
## we need to change the value of commands[4],commands[5],commands[6],commands[7]

```



## 3  Project Task 1： Collison Avoidance

### 3.1 Background

We need to control the robot **move** from one point to another point in the field. There will be moveable and static obstacle (are robots as well), so we need to **avoid the collison** 

What we know:

* the position of every robot
* the velocity of every robot (but is **NOT** accurate)

What we can control:

* the velocity of every robot

The **key problem**:

* Path planning: in general, we want to find a path **short** but will **avoid** the static obstacle as well.
  * Action and dynamic object will change the optimal path
* Dynamic obstacle:  there will be other moveable robot in the field, so we need to **change our path in real time**
  * Action should be quick
* Path Tracking: How to control the robot **follow the path** we generated accurately

### 3.2 Approach: RRT



