---
layout: post
title: 你应该要知道的一些网络协议
tags:
- boatt
- Jacman
categories: boatt
description: .
---
## 主题描述
你应该要知道的一些网络协议。

<!-- more -->
## 日志详情

> HTTP协议：应用层，短连接。包括POST请求、GET请求。
> Socket：程序员层面上，长连接。socket是对TCP/IP协议的封装和应用，Socket本身并不是协议，而是一个调用接口(API)，只是使得程序员更方便地使用TCP/IP协议。通过Socket，我们才能使用TCP/IP协议。
> TCP协议：传输层，长连接。有“3次握手”，安全性高。
> UDP协议：传输层，短连接。
> IP协议：网络接口层。
> DHCP：解析协议，解析IP地址。访问网站只能通过IP地址，但是有如此之多的网址，用户不可能通过挨个记IP地址来访问不同的网址。因此DHCP协议就是为了使用户访问网址时输入的文字、数字等转换成IP地址，来访问网址。
> XMPP：用TCP传输XML数据流
> xmpp是一个应用层协议，其底层（传输层和网络层）依然是Socket通信。换句话说，xmpp是建立在Socket通信基础上的。
>
> rtsp:视频推流拉流协议