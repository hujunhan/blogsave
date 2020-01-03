---
title: Introduction to EEG
author: Junhan Hu
tags: [hardware,eeg]
mathjax: true
categories:
- Robotics
- Hardware
date: 2020-1-2 19:36:00
---

## 1 History

* 1875, observed from exposed brains
* 1914, photographed experimentally induced seizures
* 1934, "human brain waves",

## 2 Why measure EEG

Greatest advantage: **temporal resolution**, EEG can determine electrical activity in different brain regions

## 3 Physics

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/eeg-dipoles.png)

Necessary conditions: Aligned neurons and synchronous activity

<!-- more -->

Acquisition:

* electrode caps
* conductive jelly
* ruler
* EEG amplifier, laptop

## 4 Data collection

Can tell us: precise timing of neural activity, sequence of mental operations

Can NOT tell us: precise brain location of neural activity

### Analysis

* ERP: time- & phase-locked potentials
* On-going EEG: frequency-domain analysis

### Frequency-domain Analysis

| EEG Bands(Hz) |              Distribution               |  Subjective feeling   |
| :-----------: | :-------------------------------------: | :-------------------: |
| Delta: 0.1-3  |            broad or diffused            | deep, dreamless sleep |
|  Theta: 4-8   |    regional, may involve many lobes     |  intuitive, creative  |
|  Alpha: 8-12  | regional, usually involves entire lobes |        relaxed        |
|  Gamma: >30   |             very localized              |        focused        |
|  Beta: 12-30  |                localized                |       alertness       |

### Time-Frequency Analysis

apply a 'window' to the data, then perform the FFT on this windowed data

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/eeg-spectrogram.png)

## 5 Challenge

Hard to solve the Inverse Problem: 

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/eeg-inverse-problem.png)

