---
title: 音乐的乐理基础——数学角度
author: Junhan Hu
tags:
  - skills
mathjax: true
categories:
  - Life
  - Music
date: 2019-08-09 23:09:00
---

## 1 声学基础

音乐由声波构成，声波是一种机械波。声波以某种频率进行频率和强弱的变化构成了音乐

* 频率：标准计量单位为赫兹$Hz$，即一秒内峰的个数
* 振幅：音量的大小

### 1.1 声音的复合

* 纯音：以固定频率进行简谐振动
* 复合音：有多个纯音组成，音乐由大量不同的复合音构成。产生方式有
  * 谐波叠加
  * 拍音叠加

最基本的纯音组合$\to$单音，组合$\to$拍音

<!-- more -->

#### 谐波 Overtone

在音乐领域中往往称为**泛音**

一个标准的正弦波可以称为基波，频率是基波整数倍的波是谐波

钢琴的**一个**键或者小提琴的**一根**弦都能产生**多个谐波**，合成之后叫做**单音**

比若说小提琴声音的形成过程，典型的**谐波叠加**，[下载之后用播放器播放](https://github.com/hujunhan/cloudimage/blob/master/audio/violin-wave.wav)

#### 拍音

另一种复合音，由两个或多个**单音**叠加，一般要求这两个音的**振幅相近**

纯八度的拍音是由频率是$1:2$的两个单音构成的

## 2 十二平均律和五线谱

人类三大乐器有

* **弦乐**--音律学的发展起源
  * 用琴弦振动发出声音，长短、粗细、密度都决定了振动的频率
  * 一般来说，频率和长度成反比
* 管乐
* 打击乐

为了保证音乐的表达效果，所以要定出

* 相对音高，将不同的单音组合起来——使用**十二平均律**
* 绝对音高，使得在不同地方演奏的效果相同——使用**五线谱**

### 2.1 十二平均律

作用：规定两个单音的相对音高

定义：

* **纯八度**：频率为$1:2$的两个单音之间的**音程**
* 将一个纯八度分为**12份**，每份称为1个**半音**，两份称为1个**全音**
* **音程**：两个音之间的频率差矩，单位为**全音**，计算方式为$f_x=f_0*2^\frac{x}{12}$

| 相差音数     | 0.5        | 1          | 1.5        | 2          | 2.5        | 3          | 3.5        | 4          | 4.5        | 5          | 5.5        | 6          |
| ------------ | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| **音程名称** | **小二度** | **大二度** | **小三度** | **大三度** | **纯四度** | **三全音** | **纯五度** | **小六度** | **大六度** | **小七度** | **大七度** | **纯八度** |

### 2.2 五线谱

作用：记录任何形式的音乐

定义：

* 音符：一个音符表达一个单音，每个音符有绝对的音高
  * **符头**--决定了音高
  * 符杆--连接作用
  * 符尾--见机行事，符头高了就在下，符头低了就在上
  
* 五线谱：五条线，从下到上是**频率**的变化，从左到右是**时间**的变化

  ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/music-5-A-G.png)

  半、全意味着两个音符之间的音程是全音还是半音

* 谱号：五线谱最左边，规定了线和间上的音符的**音高**

* 升降记号，在音符后面添加标记

  * **升号** #
  * **降号** b

一共有7个音符

| 音名 | A    | B    | C    | D    | E    | F    | G    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 唱名 | La   | Si   | Do   | Re   | Mi   | Fa   | So   |

相邻的同名音符之间的音程是八度，也就是频率高了一倍

**规定**：

* 第二间的La，为A，频率为$440Hz$，所以以它为基准，其他音符的频率就可以推导出来了

* C4位于高音五线谱的下加一线，往高依次是D4、E4、F4，往下依次是B3、A3

  ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/music-c.png)

* A4的频率是440$Hz$，所以A音的频率为下表

  | 基准音名 | A0   | A1   | A2   | A3   | A4   | A5   | A6   | A7   |
  | -------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
  | 频率(Hz) | 27.5 | 55   | 110  | 220  | 440  | 880  | 1760 | 3520 |

  所以可以根据A的频率计算其他几个音的频率

* 若两个键之间是一个音程，那中间就可以有一个半音，比如Bb==A#

  * 有两个音没有必要升，E升半音就是F，B升半音就是C

### 2.3 和声

定义：由超过一个单音所组合而成的声音，所以定义和**拍音**非常相似

* 西方古典音乐理论中，和声主要研究的是**两个单音**构成的和声，三个以上单音一般称为和弦

有的和声比较和谐，有的比较刺耳，究其原因就是因为拍音。

相邻两个音之间的频率是以指数变化的，所以近似的频率比，周期所产生的最小公倍数会相差较大。所以最小公倍数小的，就比较和谐

|  音程  | 近似频率比 | 近似整数比 | 最小公倍数 |
| :----: | :--------: | :--------: | :--------: |
| 小二度 |   1:1.06   |   15:16    |    240     |
| 大二度 |   1:1.12   |    8:9     |     72     |
| 小三度 |   1:1.19   |    5:6     |     30     |
| 大三度 |   1:1.26   |    4:5     |     20     |
| 纯四度 |   1:1.34   |    3:4     |     12     |
| 三全音 |   1:1.41   |    7:10    |     70     |
| 纯五度 |   1:1.50   |    2:3     |     6      |
| 小六度 |   1:1.59   |    5:8     |     40     |
| 大六度 |   1:1.68   |    3:5     |     15     |
| 小七度 |   1:1.78   |    5:9     |     45     |
| 大七度 |   1:1.89   |    8:15    |    120     |
| 纯八度 |    1:2     |    1:2     |     2      |



