---
title: PADS-Analysis
author: Junhan Hu
tags: [DS]
mathjax: true
categories:
- CS
- DS & Algorithm
date: 2018-12-24 00:05:00
---
## 1. Big Picture

* What makes a program better？many valid criteria, which are often in conflict.
* omputer scientists *love*
  * Time
  * Memory
  * trade off
* sum of 1-n：
  * simple add
  * gauss formula
 <!-- more -->

## 2. Big O Notation

| f(n)    | Name        |
| ------- | ----------- |
| 1       | Constant    |
| $log n$ | Logarithmic |
| $n$     | Linear      |
| $nlogn$ | Log Linear  |
| $n^2$   | Quadratic   |
| $n^3$   | Cubic       |
| $2^n$   | Exponential |

## 3. Example :Anagram Detection

1. Checking off: check one by one ,$O(n^2)$.
2. Sort and Compare: $O(nlogn)$
3. Brute Force , try all possibilities: $O(n!)$
4. Count and Compare: $O(n)$

## 4. Performance of Python Types

* Lists
  * Indexing & Assigning & Appending $O(1)$
  * Poping, Shifting & Deleting, normally $O(n)$ ,beacuse has to shift changed element
  * Reversing $O(n)$
* Dictionaries
  * “getting” and “setting” : $O(1)$
  * Iterating & Copying: $O(n)$