---
title: Audio Stretch
author: Junhan Hu
tags: [neuroscience]
mathjax: true
date: 2020-03-11 17:55:00
---

## 总览

[Ref](https://www.mathworks.com/help/audio/ref/stretchaudio.html)

Audio stretch, 也可以称为TSM (time scale modification)

用途:

* 拉长或缩短信号, 并且不损失信息
* 将两个语音信号拉成相同的长度, 方便做平均

## 算法

### Phase Vocoder

**频域上的拉伸**, 基本想法就是将音频做时频分析, 分成很多小段, 保留音高Pitch. 经过相位移动之后重建波形算法的主要难点和复杂之处在于如何使重叠加法重建中连续窗口的对齐

![img](https://www.mathworks.com/help/audio/ref/stretchaudio_vocoder.png)

## WSOLA -- Waveform Similarity Overlap-Add

时域上的拉伸, 是OLA算法的拓展

* OLA stand for overlap and add, 是一个简单的叠加算法, 对音频进行分帧, 然后进行合成
  * 存在问题1:  音频不连续
  * 存在问题2: 会造成部分信号幅值改变 
* WSLOLA, 特点是音频分帧之后不直接叠加, 而是在一定范围内找待叠加的音频帧, 找到最相思的去合成