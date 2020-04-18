---
title: Computation Neural Model
author: Junhan Hu
mathjax: true
date: 2020-04-05 16:20:00
---

## Neural Circuits

What they want to do?

Learn some algorithm from our brain and translate them into computer code

Some feature of brain-based computations

* work for many decades
* parallel computation
* interaction

How to study brain at different **scales**

* Large to small: EEG\MEG\PET\Patch Damp
* **A central question in neuroscience:** what’s the **right** level of abstraction

Bottom-Up method, first study single neurons. Some model

* filter operation
* integrate-and-fire circuit (easy to implement)
* Hodgkin-Huxley unit
* Multi-compartmental models
* Spines, channels 

Circuits

![image-20200406153827627](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20200406153829.png)

Something like this

Visual system shows an approximately hierarchical architecture.

* V1 part is important
* Timing of the response, latency 50~60ms
* What pathway and Where pathway 

First order approximation: immediate recognition

* **behavior**, we recognize objects within ~150ms
* **physiology**, visually selective responses to complex shapes within ~150ms
* **computation**, bottom-up computational models (maybe inspire deep learning)

## Feedback Signal

### Basic Mechanisms in V1

**Feedback signal enhance surround suppression**

signals from higher part

visual cortex orientation tuning, there is a Gabor function can describe the system

There are so many models can explain the situation

* feed-forward model
* feed-back? (by cooling v2/v3 cortex) NO 

### Visual Search

**Tuned feedback signals can instantiate visual search and feature-based attention**

to see particular face/color

go through some linear and non-linear computation

1. filter 4 orientation
2. local max
3. filter
4. filter
5. comparison

## Questions

Reasons for optimism

* Wiring diagram
* Strength in numbers
* Source code