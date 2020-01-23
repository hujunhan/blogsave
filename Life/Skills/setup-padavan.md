---
title: 安装Padavan固件
author: Junhan Hu
tags: [hexo,blog]
mathjax: true
categories:
- Life
- Skills
date: 2020-1-19 19:09:00
---

## Intro

Padavan是一个路由器固件，相比一般路由器的出厂固件来说会多很多功能，~~尤其是SSR等功能~~~

## 步骤

1. 准备工作

   * 下载Breed

     这是引导器，类似于GRUB，用它来引导Padavan系统

   * 下载Padavan固件

     根据使用的路由器硬件来选择相应的固件。本次使用的是极路由3

     下载地址[点这](http://opt.cn2qq.com/padavan/) 前缀RT-AC1200HP-GPIO-12-JI3，估计是根据华硕的AC1200改的

     <!-- more -->

   * （OPTIONAL）开启路由器开发者模式

     有些路由器需要特殊操作才能刷入固件，比如说极路由需要开发者模式，在**插件市场**的**路由器信息**板块下**高级**里申请

     申请完安装开发者模式固件，提示信息：root系统的SSH端口号为1022，用户名: root，密码: 路由器后台密码；

2. 刷breed固件

   1. 传送breed固件到路由器上，使用scp命令

      ```
      scp -p 1022 /path/to/the/breed-file.exe root@192.168.199.1:/tmp
      ```

      

