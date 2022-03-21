---
title: 域名系统DNS
tags:
  - DNS
categories:
  - 网络
mathjax: true
abbrlink: a6cd
date: 2021-06-06 08:20:00
top_img: /img/featureimages/12.jpg
cover: /img/featureimages/12.jpg
---

# 域名系统DNS

## DNS查询

DNS（domain name system）的作用是将域名解析为IP地址。

DNS的查询方式：

![](https://raw.githubusercontent.com/wht6/image/master/img/dns_chaxun.jpg)

而实际的查询流程往往是：

1 浏览器缓存——2 系统缓存（host文件）——3 路由器缓存——4 ISP服务器（本地DNS服务器）的DNS缓存——5 根域名服务器——6 顶级域名服务器——7 主域名服务器——保存结果到缓存中。

## DNS记录

DNS的域名记录的几种形式：

A记录（address）正向解析。主机名于ip关联起来，通过域名找ip。

PTR记录（Pointer）反向解析，主机名于ip关联起来，通过ip找域名。

CNAME记录（canonical name）别名。允许多个域名映射到同一台服务器。

MX记录（mail exchange）指向邮件服务器。根据邮箱地址定位mail服务器。

NS记录（name sever）指定该域名是由哪个域名服务器解析的。

## HOST文件

系统的host文件包括常用的域名和对应的ip（其中包括你之前访问过的域名），相当于本地DNS缓存，解析域名的时候会先去查找本地host文件中是否有域名对应的ip。修改host文件可以屏蔽一些网站，比如修改域名的ip为127.0.0.1。

windows的host文件在路径C:\Windows\System32\drivers\etc中。

修改示例：127.0.0.1 www.baidu.com。保存后，命令行输入：ipconfig /flushdns刷新dns缓存，再去访问www.baidu.com就访问不到了。