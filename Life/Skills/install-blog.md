---
title: Install Hexo in New Env
author: Junhan Hu
tags: [hexo,blog]
mathjax: true
categories:
- Life
- Skills
date: 2019-7-9 18:26:00
---

## Overview

每次重装电脑都要重新安装Hexo的环境，步骤比较繁琐，所以记录下来方便之后再利用

<!-- more -->

## Scripts

```bash
# 1.安装Nodejs和npm
# Using Ubuntu
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
npm -v

# 2.安装Hexo-cli
npm install hexo-cli@2.0.0 -g
hexo -v

# 3.建站
#文件夹名称为blog
#hexo 版本为3.9
hexo init blog
cd blog
npm install

```

