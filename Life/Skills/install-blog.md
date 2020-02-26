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
npm install hexo-cli -g
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
git clone https://github.com/theme-next/hexo-theme-next themes/next

## 3.3 安装数学公式渲染器
npm un hexo-renderer-marked --save
###安装pandoc，在ubuntu下
cd ..
wget https://github.com/jgm/pandoc/releases/download/2.7.3/pandoc-2.7.3-1-amd64.deb
sudo dpkg -i pandoc-2.7.3-1-amd64.deb
cd blog
npm i hexo-renderer-pandoc --save

## 3.4 安装一些其他的包
npm uninstall hexo-generator-index --save
npm i hexo-generator-index2 hexo-auto-category hexo-blog-encrypt hexo-deployer-git  hexo-generator-searchdb  --save

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

## Deploy



## Custom Domain

Prerequisite: A custom domain

设置步骤:

1. 在域名购买商处设置一条解析规则, 记录设置为CNAME(用于github.io)或者A(用于IPv4地址)
2. 在github的项目处设置Custom Domain, 这会在项目根目录下新建一个CNAME文件, 文件内容就是想要的Custom Domain.
3. 因为每次Hexo deploy之后CNAME文件都会被删除, 所以需要在Hexo项目中加入CNAME文件来解决这个问题. 在blog/source/目录下新建CNAME文件, 文件内容是想要的Custom Domain.