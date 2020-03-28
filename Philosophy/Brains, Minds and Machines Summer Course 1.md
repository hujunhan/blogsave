---
title: Functional architecture of the human brain
author: Junhan Hu
tags: [tips,cs]
mathjax: true
date: 2020-03-22 16:20:00
---

有多种实现智能的方式: computation, circuits

>any device that perceives its environment and takes actions that maximize its chance of successfully achieving its goals.
>
>AI is whatever hasn't been done yet
>
>These sub-fields are based on technical considerations, such as particular goals (e.g. "[robotics](https://en.wikipedia.org/wiki/Robotics)" or "[machine learning](https://en.wikipedia.org/wiki/Machine_learning)"),[[15\]](https://en.wikipedia.org/wiki/Artificial_intelligence#cite_note-Problems_of_AI-15) the use of particular tools ("[logic](https://en.wikipedia.org/wiki/Logic)" or [artificial neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network)), or deep philosophical differences.[[16\]](https://en.wikipedia.org/wiki/Artificial_intelligence#cite_note-Biological_intelligence_vs._intelligence_in_general-16)[[17\]](https://en.wikipedia.org/wiki/Artificial_intelligence#cite_note-Neats_vs._scruffies-17)[[18\]](https://en.wikipedia.org/wiki/Artificial_intelligence#cite_note-Symbolic_vs._sub-symbolic-18) Subfields have also been based on social factors (particular institutions or the work of particular researchers).[[14\]](https://en.wikipedia.org/wiki/Artificial_intelligence#cite_note-Fragmentation_of_AI-14)

## Architecture

大脑是如何工作的?  可能

* 瑞士军刀, 一个区域负责一个功能
* 通用: 可以处理多种功能

我们为什么要关注大脑的这些功能组件呢? 因为这是关于大脑和智能的基本问题, 这是一种处理复杂问题的途径(bottom-up), 了解不同组件可以帮助我们理解\实现其数学模型

###  History

1. Spearman 1904, 对学生进行智能测试

   一个人如果能够更好地比较两个声音的大小, 那么他也能在数学考试中取得更好的成绩(强相关), 这是IQ测试的基本原理(各种智能是相互关联的)

2. Gall 1958

   将大脑分成不同的部分

3. Leision 1794  

   将大脑的某一部分伤害, 发现其他智能行为还是好的.  说明不同位置的大脑是有不同功能的

## Methods

### fMRI

有着最好的空间精细度, 原始数据: 大概有30000个3d点.

测试速度是很慢的, 可能测到的是6秒前的数据. 数据意义只有在比较时才会产生.

背后的信号产生机制(Blood-oxygen-level-dependent)还是不明确的

* 神经元活动增加$\to$局部血流增加$\to$血红蛋白的氧含量变化$\to$MRI信号变强

Meaning: 我们可以更好地了解大脑每个部分的不同功能, 进展十分迅速. 甚至在1990年我们都只能识别出两三个区域, 包括注意力\语言等, 现在我们已经能够定义十几个区域了

Important problem:

* 映射关系, 大脑的区域X和特定的功能Y之间是怎么样的映射, many X for Y? X for how many Y?
* 充分性\必要性
* 天生的?

