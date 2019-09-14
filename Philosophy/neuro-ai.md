---
title: Neuroscience and Aritificial Intelligence
author: Junhan Hu
tags: [tips,cs]
mathjax: true
date: 2019-09-11 10:57:00
---

## Overview

Neuroscience-Inspired Artificial Intelligence, a [paper](https://www.cell.com/neuron/fulltext/S0896-6273(17)30509-3) released by *DeepMind* in *Cell*

Why neuroscience is important for AI?

* inspiration
* validation

But in practical, biological plausibility is just a guide, not a strict requirement.

What can we do? Marr and Poggio stated that there are 3 layers of analysis

1. **top level**: the goal of the system
2. **mid level**: the process and computations, also called algorithmic level
3. bottom level: how to implement the system physically

What DeepMind do is focusing the top 2 level of the analysis

## Some History

### Deep Learning

The origin of deep learning lies directly in neuroscience

Some key timestamp:

1. Construction of neural networks —McCulloch and Pitts, 1943

   later other researcher add feedback for improvment

2. Backpropagation algorithm allowed learning multiple layers —Rumelhart et al., 1985, Werbos, 1974

3. back that time, most AI researchers was focused on building logical processing systems based on **serial computation** inspired by symbolic. **Parallel distributed processing(PDP)** is a very important tools used then. And many ideas had a sustained influence on AI research such as NLP and CV or dropout

   But stochastic and highly parallelized information processing makes pure symbolic method not practical

### Reinforcement Learning

RL methods address the problem of how to maximize future reward by mapping states in the environment to actions and are among the most widely used tools in AI research. —Sutton and Barto, 1998

RL methods were originally inspired by research into animal learning. In paticular, the development of **temporal-difference**(TD) methods, was intertwine with research into animal behavior in conditioning experiments

## Nowadays

### Attention

Biological brains are modular, with distinct but interacting **subsystems** playing key functions such as memory, languga, and cognitive control—Anderson et al., 2004/  Shallice, 1988

Most CNN models worked directly on entire images or video frames. But primate visual system works differently. 

Visual **attention shifts** strategically among locations and objects, **centering processing resources** and representational coordinates on a series regions in turn.

In practical, the attention approach were subsequently shown to produce impressive performance at difficult multi-object recognition taks both in terms of **accuracy** and **computational efficiency**

### Episodic Memory

A well known theme in neuroscience: intelligent behavior relies on **multiple memory systems**

* reinforcement-based mechanisms: long-term memory
* instance-based mechanisms: episodic memory

