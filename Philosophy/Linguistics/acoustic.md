---
title: Acoustics
author: Junhan Hu
tags:
  - Philosophy
  - Linguist
mathjax: true
categories:
  - Philosophy
date: 2020-1-3 11:27:00
---

## Physics

Sound is a pressure wave, pressure fluctuations move through space,but each air particle moves only a small distance.

<img src="https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/ling-soundwaves.png" style="zoom:50%;" />

## Spectrums

The spectrums of a sound plays a center role in determining its **quality**

<img src="https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/ling-spectrums.png" style="zoom:50%;" />

<!-- more -->

we can represent the sound in frequency plot

<img src="https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/ling-ai-spectrums.png" style="zoom:50%;" />

* the quality of a vowel depends on the **shape** of its spectrum
* the peaks are called **formants**
* the quality depends primarily on the first three formant

## Spectrogram

A spectrogram is a visual representation of the **spectrum** of frequencies of a signal as it **varies with time**. When applied to an audio signal, spectrograms are sometimes called sonographs, voiceprints, or voicegrams. 

Time-Frequency Plot

## Auditory

### Loudness

Loudness depends on **amplitude** of the sound wave $\to$ Amplitude is usually measured in the terms of **root-mean-square(over some time window)** 

perceived loudness is more closely related to **intensity**, proportional to the square of the amplitude, relative intensity  in dB = $20log(\frac{x}{r})$

Loudness of pure tone (>40 dB) in Sones: 
$$
N=2^{\frac{(dB-40)}{10}}
$$

## Sampling

What sampling rate? Due to Nyquist Theorem, twice that frequency

Since the highest frequency ears can perceive is about $20kHz$, we must sample at $2\times20kHz=40kHz$

However, almost all of the information relevant to speech sounds is below $10kHz$, so $20kHz$ sampling rate is enough

In practical, we use a sampling rate of $44.1kHz$