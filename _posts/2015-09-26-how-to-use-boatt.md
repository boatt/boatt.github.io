---
layout: post
title: 你应该知道的http响应码
tags:
- boatt
- Jacman
categories: boatt
description: 
---
## 主题描述
你应该知道的http响应码。

<!-- more -->
## 日志详情

> 100~199：指示信息，表示请求已接收，继续处理
>
> 200~299：请求成功，表示请求已被成功接收、理解、接受
>
> 300~399：重定向，要完成请求必须进行更进一步的操作
>
> 400~499：客户端错误，请求有语法错误或请求无法实现
>
> 500~599：服务器端错误，服务器未能实现合法的请求
>
> 常见的状态码如下：
>
> 200 OK：客户端请求成功
>
> 400 Bad Request：客户端请求有语法错误，不能被服务器所理解
>
> 401 Unauthorized：请求未经授权，这个状态代码必须和WWW-Authenticate报头域一起使用
>
> 403 Forbidden：服务器收到请求，但是拒绝提供服务
>
> 500 Internal Server Error：服务器发生不可预期的错误
>
> 503 Server Unavailable：服务器当前不能处理客户端的请求，一段时间后可能恢复正常