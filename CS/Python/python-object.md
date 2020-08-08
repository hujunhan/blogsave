---
title: Python对象
author: Junhan Hu
tags: [python,oop]
mathjax: true
date: 2020-6-17 16:36:00
---

## Python类

Python有风格指南PEP8，类命名使用驼峰格式，大写字母开头，任意后续单词都以大写字母开头

```python
class TwoPoint:
    def reset(self):
        self.x=0
        self.y=0
    def __init__(self,x=0,y=0):
        self.x=x
        self.y=y
```



* 添加属性，直接在实例中添加属性

  * 点标记法，*对象.属性=值*

* 添加方法，以def关键词开头

  函数与方法之间的区别之一是，所有的方法都有一个必要的参数，按照**惯例**，这个参数命名为self

* 初始化，开头和结尾的双下划线表示特殊方法，可以提供默认参数

* 注释，通过docstring的方式来支持文档注释

  在每个类、函数的定义语句（冒号结尾的那一行）添加标准字符串作为第一行

## 模块和包

通过import语句可以导入模块或者模块中特定的类、函数。

* 永远不要用 from database import *这种语法，因为不利于后期的代码维护

**包**是模块的集合，方便我们管理模块。导入的方式有两种

* 绝对导入，from ecommerce.products import Product。用这种语法时，需要将包的搜索目录加入到环境变量中
* 相对导入，在处理同一个包下的相关模块时，用相对导入 from .database import Database
  * ..上一级，.当前级

## 权限