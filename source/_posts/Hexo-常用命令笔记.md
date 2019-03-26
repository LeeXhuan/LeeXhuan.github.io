---
title: Hexo 常用命令笔记
date: 2019-03-25 09:35:45
tags: Hexo
categories: 使用说明
---

## 常用

```js
hexo n == hexo new "a new post"  新建文章，最好用双引号括起来

hexo g == hexo generate     生成静态文件到 public 文件夹

hexo s == hexo server    Server at localhost:4000，根目录为 public

hexo d == hexo deploy   部署到远程服务里，例如 github

hexo p == hexo publish  新建草稿 draft

hexo clean     清除缓存文件

hexo new page "about"   生成 /source/about/index.md 文件
```
<!-- more -->

## 服务器

```js
hexo server    默认为动态监听

hexo server -s   静态模式

hexo server -p 5000  指定端口

hexo server -i 10.20.62.123   指定IP
```

## 文章摘要

```js　　
方式1：在front-matter中编写

description: "This a digest bla bla..." 

方式2

在文章中插入一行  <!--more-->  以上部分为摘要
```