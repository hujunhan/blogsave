---
title: 依据基本原理构建线代计算机--硬件部分
author: Junhan Hu
tags: [cs]
mathjax: true
date: 2019-8-14 20:53:00
---

## 0 Introduction

从与非门到俄罗斯方块的建立，课程分为两个独立的部分，硬件和软件

这门课专注于硬件部分

### Background

最简单的Hello World背后也隐藏着很多神奇的事。比如你写一句printf，最后就在显示器上显示出了内容

当然这也是计算机科学中最重要的抽象过程，你不需要知道how，你只需要知道what，只需要关注高一层的逻辑就能实现你想要的功能。

* 这样的抽象是多层次的，从最简单的电子元器件到CPU到计算机到编程语言

之后的的课程，每一次都

* 只考虑单一一层的抽象
* 把低一层的接口作为已知
* 实现高一层的接口
* 测试我们的接口是能正常使用的

<!-- more -->

### This Course

构建一个Hack计算机，能够沟通ROM,CPU和RAM

学习的方式：从下到上，从EE到CS

* 怎么建立一个芯片：使用模拟器仿真

  设计：知道了一个芯片的抽象功能，然后设计硬件图，然后转化为硬件描述语言，最后用在仿真软件里看效果

### Next Course

之前的课程中已经建立了可以运行汇编语言的电脑，在下一节课中，我们会建立更加高级的编程语言，并且建立相应的编译器、基础系统库

## 1 Boolean Functions and Gate Logic

### Boolean Functions

我们可以对布尔值进行的操作

* AND
* OR
* NOT

根据一些等价转换可以转换逻辑函数，起到化简的作用

显然我们可以根据布尔表达式求解真值表，那么如何从**真值表到布尔函数**？

* 将所有最终值为1的行表达为一个简单表达式（这个表达式只在那一行的值为1，其他行为0），然后将这些简单表达式用**or**连接起来

* 如何找最简的表达式？NP-Hard问题

* 任意表达式都可以用AND\OR\NOT组成的表达式表示

  * 进阶：任意表达式都可以用AND\NOT组成的表达式表示

    证明：$(\mathrm{x} \mathrm{OR} \mathrm{y})=\mathrm{NOT}(\mathrm{NOT}(\mathrm{x}) \mathrm{AND} \mathrm{NOT}(\mathrm{y}))$

  * **进进阶：任意表达式都可以用NAND组成的表达式表示**

    这是因为：$(\mathrm{x} \mathrm{NAND} \mathrm{y})=\mathrm{NOT}(\mathrm{x} \mathrm{AND} \mathrm{y})$

    证明：AND和NOT都可以用NAND表示
    $$
    \begin{array}{l}{\text { 1) } \operatorname{NOT}(x)=(x \text { NAND } x)} \\ {\text { 2) }(x A N D y)=\operatorname{NOT}(x \text { NAND } y)}\end{array}
    $$

### Logic Gates

基础逻辑门：NAND、AND、OR、NOT

复合逻辑门：三个输入的AND 

* 也是一种抽象，每种门的表达是一样的，但是实现可以不同（EE做的事）

### Hardware Description Language

HDL只是一种描述语言，还需要一个模拟器来将所描述的结构运行起来

* 所以描述的顺序是没有关系的，但是推荐从左到右，调高程序的可读性
* 有许多不同的HDL
  * VHDL
  * Verilog
  * 课程使用的HDL，最简化，简单

输入输出都是由外部给定的变量名

假设：我们已经有了基本的AND\NOT\OR门

设计步骤：

1. 写出基本的逻辑表达式
2. 画成电路图（也是由AND\NOT\OR门组成）
3. 写成HDL程序
4. 用模拟器测试HDL是否正确 

> 在一个实际的项目中，芯片的设计是怎么样的呢？
>
> 1. 项目中有设计师和工程师
> 2. 设计师知道要实现的具体功能
>    1. 决定要设计哪些小的芯片
>    2. 对于每个小芯片，确定**名字API、测试脚本、比较文件**
> 3. 让工程师根据以上内容，建立芯片

> Multi-Bit Buses
>
> 我们需要对一排bit进行操作，所以，使用数组进行描述

### Project 1

我们要实现的是一共**15个**门电路

除了常见的AND\NOT\OR，还有

* MUX\DEMUX

  这两个可以作用于通信领域，将不同的信息通过通过单一的数据线进行传输

  ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/nand-mux-demux.png)

实现过程：

1. 先用NAND实现AND\NOT\OR
2. 然后用AND\NOT\OR实现其他逻辑

## 2 Boolean Arithmetic and ALU

### Binary Numbers

我们可以用01来表示数，不管是二进制还是十进制

对于二进制数的操作，虽然看上去有很多，包括加减乘除比大小。但是其实我们只要能够实现**加法**，其他的一些操作都能够简单的实现

* 减法和比大小显然能够轻松达成

* 乘法和除法**不会有硬件上的实现**，而是通过软件模拟

  这是为了**简单**起见，如果要构建这样的硬件，需要很多的设计花费，这也是一个trade-off

* **溢出问题**

  因为加法的两个数字长是固定的，所以如果两者相加溢出了，比如8位变成了9位。那么计算机会**直接忽略溢出的那个数**，这是需要使用计算机的人记住的，那就是**相加的结果可能不正确**，如果不使用正确的长度

如何操作负数呢？

* ~~用最左边的那一位表示符号~~
  * 这样的实现不优雅，比如会有-0的情况，而且还要分类讨论
* 用$2^n-x$代表$-x$
  * 正的范围$0...{2^{n-1}-1}$
  * 负的范围$-1...-2^{n-1}$

* **加法**就只需要按这个逻辑，效果是一样的
* **减法**可以用$2^{n}-x=1+\left(2^{n}-1\right)-x$，这样因为$2^n-1$都是111111，所以不需要进位
  * 这就是**补码的背后思路**：取反+1

### ALU

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-alu.png)

ALU接受两个输入和一个函数$f$，输出值

* $f$是一堆已经事先定义好的函数中的一个
* 确定$f$的集合大小是一个典型的trade-off的问题

在这门课中的ALU，称为Hack ALU，ALU实现的$f$的集合是**18个**函数

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-hack-alu.png)

其中比较重要的就是上面的6个控制值，他们进行了一些预处理

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-alu-6-options.png)

下面的两个zr、ng是两个寄存器，说明一些输出的性质

* zr说明了out是否为0
* ng说明了out是否为负数

> 设计的芯片的**效率问题**：总的来说基本上没有什么可以优化的，因为都是最简单的实现，没有优化的余地。
>
> 但是对于加法器ADDER，因为要计算进位，所以计算的位数越多，**延时**也就越多
>
> 解决方法：Carry Look-Ahead Adder
>
> 解决思路：
>
> * 延时有**线延时**和**门延时**，我们**主要关注门延时**
> * 改变结构，使得全加器的进入输入不来自上一级的全加器，而是**超前进位**
>   * 优点：使得延迟时间减小，固定为3级门延迟
>   * 缺点：如果拓宽加法器的位数，电路非常复杂

### Project 2

给定：在Project 1中已经实现的所有芯片

目标：构建以下新的芯片

* 半加器：XOR+AND
* 全加器：
* ALU
* …

## 3 Memory

从这一部分开始，会涉及到时间，其中会有一些问题包括

* 重复使用相同的硬件
* 记住系统的状态
* 协调速度

### Clock

在一个时钟周期内，系统的状态是一样的

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-clock.png)

当然在物理层面，系统状态的变化不会是瞬间的，就如图中所示灰色的部分一样

* 在设计时，这部分不需要考虑，因为我们只看最后平稳的那一部分
* 实际上，时钟的频率就是根据这段变化的时间来确定的，只要间隔比灰色时间长一点就好

**时序逻辑**：下一时刻的输出由上一时刻的输入决定

![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-seq-logic.png)

### Data Flip Flop

我们需要一个电路（1-Bit），能够记住一个状态

* 这个电路（1-Bit）能够永远记住一个状态，除非来了新的数据

  ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-flip-flip.png)

* 内部结构（Data Flip Flop+Mux）

  ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-mem-dff.png)

DFF和1Bit的区别：DFF是瞬时的，而1Bit的状态可以延续

> DFF的电路实现
>
> ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-dff-ee.png)

### Memory Units

基本电路就是上一节提到的（1-Bit）电路，通过把许多的（1-Bit）电路顺序地连接在一起，就变成了一个**寄存器**，寄存器的长度w，可以是16、32、64

**RAM unit**

* 就是一堆有地址的寄存器叠加起来
* 在任意时刻，只有1个寄存器被选择——被读或被写
* 地址的长度$\log_2{n}$ 

在这节课中，会建立一些不同长度、大小的RAM

### Counters

计数器的作用：递增地址，使得程序能够顺序执行

所以需要的功能有

* Reset，PC=0
* Next，PC++
* Goto，PC=n

计数器在硬件上抽象地实现了上述功能

### Project 3

给定：Project 2中所实现的所有芯片

目标：构建以下芯片

* Bit

* 寄存器

* RAM(各种大小)都是16位

  * 先建立RAM8，然后拼成RAM64，再用RAM64拼成RAM512

    ![](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/n2t-ram-hire.png)

  * 在Address部分，可以使用一部分作为那一个RAM的选择，还有一部分地址作为RAM内部寄存器的选择

* PC

  * 好几个MUX选择