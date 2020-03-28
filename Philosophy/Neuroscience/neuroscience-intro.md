---
title: Background for Neuroscience
author: Junhan Hu
tags: [neuroscience]
mathjax: true
date: 2020-03-22 17:00:00
---

* Neuron 

  Action potenitals: spiking or firing

  ![image-20200322163123664](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20200328184546.png)

* Anatomy

  ![image-20200322163256644](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20200328184555.png)

* Recordings

  * **invasive**(most accurate): it could be single unit or multi-unit

    ECoG: very rare

  * **neuroimaging**: MEG/EEG/fMRI(good spatial resolution but bad time accuracy)

    Why it works: nice properties that neurons in the **same orientation**

* Visual system

  ![image-20200322164400363](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20200328184603.png)

  * Ventral Stream: **what** is the object
  * Dorsal Stream: **where** is the object

  feed-forward, feed-back connection

  ![image-20200322164604869](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/20200328184610.png)

  真正的神经网络可能也是层级的, 一层处理某一项功能, 比如浅层的来识别物体种类, 深层的识别物体位置.

  如果要通过计算机实现上述的模型, 会用到一个分层的前馈模型

  * CNN

  * 简单的cell: 映射

  * 复杂的cell: 类似于卷积

    Max Pooling: 池化作用于图像中不重合的区域, 所以pooling之后会变小