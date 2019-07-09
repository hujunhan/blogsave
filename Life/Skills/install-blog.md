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

## 3.1 拷贝markdown源文件
git clone https://github.com/hujunhan/blogsave.git source/_posts/.
##测试
hexo server

## 3.2 添加主题Next
git clone --branch v7.1.0 https://github.com/theme-next/hexo-theme-next themes/next

## 3.3 安装数学公式渲染器
npm un hexo-renderer-marked --save
###安装pandoc，在ubuntu下
cd ..
wget https://github.com/jgm/pandoc/releases/download/2.7.3/pandoc-2.7.3-1-amd64.deb
sudo dpkg -i pandoc-2.7.3-1-amd64.deb
cd blog
npm i hexo-renderer-pandoc --save

## 3.4 安装一些其他的包
npm i hexo-auto-category hexo-blog-encrypt hexo-deployer-git  hexo-generator-searchdb  --save

## 3.5 建立分类、tag页面
hexo new page categories
hexo new page tags
sed -i '3a type: tags' source/tags/index.md
sed -i '3a type: categories' source/categories/index.md

# 4.设置上传相关
git config --global user.email "hujh@zju.edu.cn"
git config --global user.name "hujunhan"
#在新环境中设置密钥
ssh-keygen #生成密钥
cat /home/coding/.ssh/id_rsa.pub  #读取密钥
#到Github中设置
```

