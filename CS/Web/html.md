---
title: Basic HTML
author: Junhan Hu
tags: [web]
mathjax: true
categories:
- CS
- Web
date: 2019-5-20 00:54:00
---

## Overview

HTML means hyper text markup language

HTML的作用是定义网页的结构, 比如说哪一段是标题, 哪一段是文章内容, 哪一段是图片等, 就类似于MarkDown中定义了怎么样的是标题, 怎么样的是列表一样. 具体长什么样由CSS决定

## Grammar

```html
<p>My cat is very grumpy</p>
```

由部分组成

1. opening tag <>
2. 内容
3. closing tag </>

3部分组合起来叫做element. element可以有一些属性attribute

## A Typical HTML File

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <img src="images/firefox-icon.png" alt="My test image">
  </body>
</html>
```

* html包裹了网页中所有的东西
* head包裹了所有**不给浏览者**看的东西, 包括一些自定义的变量, keywords(给搜索引擎看的),标题(出现在tab上的标题)等
* body包裹了所有**给浏览者**看的东西, 包括你想要展示的内容, 图片等

## Basic Element

* \<hx\> heading, x=1~6
* \<p\> paragraphs
* \<ol\> \<ul\> list, ordered, unordered
* \<xx style=“color:red”\> inline style，内联样式，简单但不易于维护
* CSS，层叠样式表，cascading style sheets，易于维护
  * 元素选择器，style中 h2，p：colot、font-size、font-family、border
  * 类选择器 style中 .blue-text
* 锚点anchor，a元素，#死链接
* alt，图片无法加载时显示的替代文本