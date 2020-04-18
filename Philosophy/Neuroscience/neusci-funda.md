---
title: Timing Synchronization in EEG Experiments
author: Junhan Hu
tags: [neuroscience]
mathjax: true
categories:
  - Philosophy
date: 2020-01-13 10:29:00
---

## Introduction

https://sccn.ucsd.edu/~mgrivich/Synchronization.html

Goal: properly **synchronize** events in the EEG experiments and **validate** the  sychronization. 

Why? verify that the timing of all data points is known with sufficient precision.  Some key points such as the playing of a sound, the display of an image.

<!-- more -->

Error

* constant offset
* drift: as time passes, the difference increase
* jitter: 

## General Principles

1. When possible, use hardware synchronization
2. streaming, in general, 50ms is easily achievable, and 1ms accuracy is achievable with effort
3. behavior must be validated

## Audio Synchronization

Playing audio is not reliable with respect to timing. Latencies of 100+/-50 ms are common.

