---
title: Tutorial: Decoding to Understand Neural
author: Junhan Hu
tags: [tips,cs]
mathjax: true
date: 2020-04-6 18:33:00
---

## Motication

* have some idea about how brain works
* run a experiment and make neural recordings
* get a buch of data

**convert data into answers**

## Decoding?

Alternative name: readout MVPA

predict stimulus/behavior from neural activity

Classifier: 

1. see some image, record the eeg
2. train pattern classifier
3. predict

this a analog to the real brain

<img src="https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20200406185819.png" alt="image-20200406185816001" style="zoom:50%;" />

## Neural Content

Start with a simply experiment 

Confusion Matrices, predict pretty well

different classifiers? both good

* MCC
* EDist(good)
* SVM

### Abstract representations

Different angles/language/color, we can still tell

Example: position invariance experiment

* train upper, better accuracy upper, but not bad at middle and lower 
* different pose ML/MF/AL/AM 

## Data analsis

neural content: what information

coding: what feature does brain process