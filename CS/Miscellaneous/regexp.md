---
title: Regular Expressions
author: Junhan Hu
tags: [tips,cs]
mathjax: true
date: 2019-7-30 17:00:00
---

## Overview

Regular expressions are useful in **text** processing fields to **extract information**.

The main idea: writting **patterns** to **match** a specific sequence of characters

## Quick Start

* Letters

  `a` matches *a*

  `ab` matches *ab*

  `[abc]` matches only *a / b / c* (1 character)

  <!-- more -->

  `[^abc]` matches only 1 character **except a\b\c**

  `[a-z]` matches only 1 character *from a to z*

* Digits

  `123` matches *123*

  `\d` matches *any digit*

  `\D` matches any *Non-digit*

* Wild Card

  `.` matches *any character*

  `\.` matches *.*

  `\w` matches *any Alphanumeric* (alphabet + number) character

  * equals to `[A-Za-z0-9_]`

  `\W` matches *any non-alphanumeric* character

* Repetitions

  `a{3}` matches *aaa*

  `a{1,3}` matches *a / aa / aaa*

  `a*` matches *0 or more* repetition of a

  `a+` matches *1 or more* repetition of a

  `a?` a is optional in this case, so matches *0 / 1* repetition of a 

* Whitespace

  There are many common forms of **whitespace**

  * space
  * tab
  * new line
  * carriage return

  These can be matched by `\s`, so `\s` is extremely useful when dealing with raw input text

* `^...$`

  Defines what should be matched in a **line**‘s begining and end

* Group

  Use `( )` to **extract information** for further processing 

  e.g. ` ^(IMG\d+)\.png$` will match .png file but will only capture files’ *name*

  * Nested Group

    Use nested `( )` to extract multiple layes of information

## Ref

[RegexOne](https://regexone.com/)