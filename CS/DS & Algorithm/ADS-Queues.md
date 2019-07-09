---
title: PADS-Queues
author: Junhan Hu
tags: [DS]
mathjax: true
categories:
- CS
- DS & Algorithm
date: 2019-1-3
---

## 1 Introduction

### 1.1 Queues

> A queue is an ordered collection of items where the addition of new items happens at one end, called the “rear,” and the removal of existing items occurs at the other end, commonly called the “front.”

* Example: wait in a line for a movie/ OS use queues control processes

* Usage: keep in order

  ![queues](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/queues.png)

  <!-- more -->

### 1.2 ADT

|Queue Operation|Queue Contents|Return Value|
| :--------------: | :-------------------: | :---: |
|   q.is_empty()   |          []           | True  |
|   q.enqueue(4)   |          [4]          |       |
| q.enqueue('dog') |      ['dog', 4]       |       |
| q.enqueue(True)  |   [True, 'dog', 4]    |       |
|     q.size()     |   [True, 'dog', 4]    |   3   |
|   q.is_empty()   |   [True, 'dog', 4]    | False |
|  q.enqueue(8.4)  | [8.4, True, 'dog', 4] |       |
|   q.dequeue()    |  [8.4, True, 'dog']   |   4   |
|   q.dequeue()    |      [8.4, True]      | 'dog' |
|     q.size()     |      [8.4, True]      |   2   |

## 2 A Queue Implementation

In practice, use the standard library's `collections.deque` to achieve high performance( $O(1)$) enqueues and dequeues.

## 3 Example: Simulating Hot Potato

As mentioned in the first section, **queues** can be used in FIFO manner.

**Hot Potato game**: people line up in a **circle** and pass item to neighbor, at a certain point, the action stopped and the man who has the item is removed from the circle. Finally there will be only 1 person left.

![hot-patato](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/hot-potato.png)

The person who is in front of the queue may be randomly removed.