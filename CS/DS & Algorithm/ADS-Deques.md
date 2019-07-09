---
title: PADS-Deques
author: Junhan Hu
tags: [DS]
mathjax: true
categories:
- CS
- DS & Algorithm
date: 2019-3-2 10:00:00
---

## 1 Introduction

### 1.1 Deques

> A **deque**, also known as a **double-ended queue**, is an ordered collection of items similar to the queue. It has two ends, a front and a rear, and the items remain positioned in the collection. In a sense, this hybrid linear structure provides all the capabilities of stacks and queues in a single data structure.

Simply speaking, deques is **stacks + queues**

<!-- more -->

### 1.2 ADT

| Deque Operation      | Deque Contents                | Return Value |
| -------------------- | ----------------------------- | ------------ |
| `d.is_empty()`       | `[]`                          | `True`       |
| `d.add_rear(4)`      | `[4]`                         |              |
| `d.add_rear('dog')`  | `['dog', 4]`                  |              |
| `d.add_front('cat')` | `['dog', 4, 'cat']`           |              |
| `d.add_front(True)`  | `['dog', 4,'cat', True]`      |              |
| `d.size()`           | `['dog', 4, 'cat', True]`     | `4`          |
| `d.is_empty()`       | `['dog', 4, 'cat', True]`     | `False`      |
| `d.add_rear(8.4)`    | `[8.4, 'dog', 4, 'cat',True]` |              |
| `d.remove_rear()`    | `['dog', 4, 'cat', True]`     | `8.4`        |
| `d.remove_front()`   | `['dog', 4, 'cat']`           | `True`       |

## 2 Implementation

In practice, we just *import deque from collections* module

Adding and removing from the **rear** is $O(1)$

Adding and removing from the **front** is $O(n)​$

## 3 Example: Palindrome Checker

![deques](https://raw.githubusercontent.com/hujunhan/cloudimage/master/img/deques.png)

```python
from collections import deque


def is_palindrome(characters):
    character_deque = deque(characters)

    while len(character_deque) > 1:
        first = character_deque.popleft()
        last = character_deque.pop()
        if first != last:
            return False

    return True


is_palindrome('lsdkjfskf')   # => False
is_palindrome('radar')   # => True
```