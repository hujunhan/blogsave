---
title: MIT EECS 导论课 2
author: Junhan Hu
tags: [cs]
mathjax: true
date: 2020-03-17 17:09:00
---

# 软件工程

首先介绍了一下基本的Python编程, 然后着重介绍了抽象和模块化的重要性, 并且以移动机器人为例具体介绍了**过程, 数据结构, 对象, 状态机**

> 我一开始学习的编程语言就是C语言, 一个非常简单又非常难写的语言, 语法简单好学, 可能一个下午语法就学完了. 但是过于简单导致编程过程中经常花很多时间用在学习一些和程序本身没有关系的知识上(计算机系统), 我觉得实在是得不偿失

首先介绍了基础的**PCAP框架**, Primitives, Combination, Abstraction, Patterns. 恰好Python可以方便地实现这个框架

这个基本的框架是我们们在考虑建模时要经常考虑的问题, **它可以帮助我们设计有用的模型**

<!-- more -->

## 1 程序和数据(Low Level)

介绍了一个程序中的基本结构

* 数据
  * 基本数据
  * 数据结构, 变量更像是一个指针
* 过程
  * 语句的组合, 可以看成是一个函数
  * 通过定义函数达到抽象的目的
* 对象: 面向对象编程
  * 对象和实例
  * 继承
* 递归: 确保每次调用时, 工作量会变小. 递归程序分成两部分, **在解释器上用到了递归的思想**
  * 基本情况
  * 递归情况

> 虽然用的是Python, 但是其中仍然有指针的概念, 一样能将计算机系统介绍的很清楚, 甚至在本章的后半部分还带学生实现了一个简单的解释器, 既兼顾到了广度(程序设计的基本设计模式), 又实现了深度(解释器的设计), 我觉得光这一节课就顶的上我所上过的*C程序设计+面向对象+计算机基础+自学的解释器*, 效果也更加好

### 助教课: 函数式编程

在python中, 函数也是一等公民, 也就是可以作为参数或者被return.

所以虽然总体上Python是一个面向对象的语言, 但是我们也可以写成**函数式**的程序

```python
def square(x): #定义了一个平方函数
    return x*x

def selfComposition(someFunction):
    def returnFunction(*args):
        return someFunction(someFunction(*args))
    return returnFunction #返回的参数是一个函数

f=selfComposition(square)
#或者
f=selfComposition(lambda: x x*x)
f(2)
# 16
```

Lamdas:  定义一个没有名字的函数, 非常简洁

非常好用的用处是操控一些数列

```python
map(lambda x:x*2,demolist)
```

也可以用于list comprehension

> 助教课我觉得是一种很好的学习方式, 因为作为同龄人, 他们更能理解学生的学习方式, 也可以介绍一些比较前沿的内容, 不适合在课上讲的内容. 

## 2 状态机(High Level)

介绍了状态机的定义: 一种建模方法, 其输出取决于其输入的整个历史, 它表示了**控制过程**, 它的表示方式简洁, 能从程序的循环中脱离, 是模块化的

虽然现实生活是连续的, 但是在计算机系统中, 控制策略都是**高度非线性和离散**的. 我们可以把嵌入式系统或者机器人系统看成一个处理**输入值流**(Input Stream)到输出值流的转换, 所以时间越长, **过程就越复杂**.  为了解决这个问题, 我们需要**捕捉历史的基本属性**

状态机有以下几个基本属性: **状态集合, 输入集合, 输出集合, next-state方程, ouput方程, 初值**. 如果状态是有限的, 那就是有限状态机

一般来说, 状态机也可以分成三种, 对应着与环境交互的三种模式

* 综合型 由目标决定
  * 输入: 传感器读到的外部环境
  * 输出: 控制指令
* 解析型 由系统决定
  * 输入: 控制指令
  * 输出: 系统的一些简单度量, 比如是否会收敛到稳定
* 预测型 由系统和环境决定 (SLAM)
  * 输入: 控制指令
  * 外部环境的状态

当然复杂的状态机也是由许多简单的状态机构成的

### Primitive

定义一个Abstract Class, SM(State Machine), 其他所有状态机都继承于这个类.

对于每一个状态机来说, 都需要指定

* 初值 startState

* 获取输出 getNextValue, 输入是这一时刻状态和输入, 输出是下一时刻的状态和输出

  这个函数**不会改变状态机的状态**, 为什么要这样设计? 虽然有很多种设计方式, 但是实践表明这种**没有副作用**的函数是非常有用的

例子: 要做一个加法器Accumulator的状态机

```python
class Accumulator(SM):
    def __init__(self,initialValue): #定义初值, 每个SM都一样
        self.startState=initialValue
        
    def start(self): #状态机的开始, 每个SM都一样
        self.state=self.startState
        
    def step(self,input): #更新状态
        (s,output)=self.getNextValue(self.state,input)
        self.state=s
        return output
    
    def transduce(self,input_stream): #处理流数据
        self.start()
        return [self.step(input) for input in input_stream]
    
    def getNextValue(self,state,input):#输入是这一时刻状态和输入
        return (state+input,state+input)#输出是下一时刻的状态和输出, 这里状态和输出是一样的
    
```

### Combination

在上一节构建了基础的状态机之后, 我们可以组合起来变成更加复杂的状态机

基础的组合方式包括: 级联, 并联, 负反馈

```python
#用Python实现负反馈的关键: 存在未定义的时刻, ignore掉
def getNextValues(self,state,inp):
	(ignore,o)=self.m.getNextValues(state,’undefined’
	(newS,ignore)=self.m.getNextValues(state,o)
	return(newS,o)
```

终止状态机(TSM)也是一种非常有用的状态机, 比如扫地机器人先扫A房间, 再扫B房间, 这就是终止了某一个状态机开启了另一个状态机

### Control Robot Using State Machine

抽象出输入(传感器), 输出(执行器), 然后再对行为建模做成一个状态机, 写成代码. 机器人所做的事情就是

1. 读取传感器输入
2. 将输入喂给状态机
   1. 前进状态机
   2. 旋转状态机
   3. 坐标系状态机
3. 执行输出

## 3 总结

对于大部分系统, 我们都可以找到一个PCAP系统来描述它, 如果没有, 就发明一个. 通过这种方式, 我们可以将一个复杂的问题变得更加简单, 容易解决

e.g. 以SLAM为例

主要就是三个状态机

1. 地图构建状态机
   * 读取传感器
   * 输出地图
2. 路径规划状态机
   * 读取地图和传感器
   * 输出路径
3. 执行器状态机
   * 读取路径和传感器
   * 输出指令