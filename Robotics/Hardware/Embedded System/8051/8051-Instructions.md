---
title: 8051 Instructions
author: Junhan Hu
tags:
  - 8051
mathjax: true
pdf: true
categories:
  - Robotics
  - Hardware
  - Embedded System
  - 8051
date: 2019-01-11 23:09:00
---

## 1 Overall

共性：

1. 立即数不能作为**目的操作数**
2. 以`A`为目的操作数的指令会影响`Parity`
3. `Rn`与`Rn`、`Rn`与`@Ri`、`@Ri`与`@Ri`不能同时出现在指令的源、目的操作数中。

<!-- more -->

操作数的表现形式

* **内部RAM：`A`、`Rn`、`@Ri`、`direct`、`#data`**
* **外部RAM：`@DPTR`、`@Ri`**
* **ROM：`@A+DPTR`、`@A+PC`** 

## 2 数据传送指令

除以累加器`A`为目的操作数的数据传送指令对P标志位有影响外，其余数据传送指令均不影响标志位。

### 2.1 内部RAM

* **MOV**
* 在`A`、`Rn`、`@Ri`、`direct`、`#data`之间互传
  * 除了*`Rn`之间*、*`Rn`与`@Ri`之间*、*`@Ri`之间*
  * `direct`可以自己传自己

### 2.2 外部RAM

* **MOVX**
* 其中必有一个为`A`
* 另外一个操作数（在片外）：
  * `@Ri`，片外低256字节
  * `@DPTR`，片外64K

### 2.3 ROM

* **MOVC**
* 都是读入`A`中
* 只有两种
  * `@A+DPTR` ：`DPTR`相当于表的位置，`A`=欲查数值距离表首地址的值
  * `@A+PC`：`PC`相当于表的位置，`A`=表首地址－当前指令的`PC`值－1

## 3 算术运算

除了`++`和`--`以外都影响标志位

1. **INC** \ **DEC**：只有`DPTR`不能--
2. **ADD** \ **ADDC** \ **SUBB**
   * 都存入`A`，只有`DPTR`不能进行运算
   * **ADDC**：(A)$\leftarrow$(A)+(Cy)+(第二操作数)
   * **SUBB**:   (A)$\leftarrow$ (A)－(Cy)－(第二操作数)
3. **MUL** \  **DIV**
   1. **MUL**: 低八位进`A`，高8位进`B`
   2. **DIV**：整数进`A`，余数进`B` 

## 4 逻辑运算

目的操作数是A时影响P标志位。除了两条带进位的循环移位指令影响C标志外，其余均不影响PSW中的各标志位。

1. **ANL** \ **ORL** \ **XRL** 

2. **RL** \ **RR** \ **RLC** \ **RRC** 

   ![logical-operation](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/logical-op.png)

3. **CLR** \ **CPL** 