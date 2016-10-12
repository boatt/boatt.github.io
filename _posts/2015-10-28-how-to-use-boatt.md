---
layout: post
title: 浅谈网络框架
tags:
- boatt
- Jacman
categories: boatt
description: 浅谈网络框架.
---
## 主题描述
浅谈网络框架。

<!-- more -->
## 日志详情

> 就目前的网络请求库有：Xutils、Volley、OkHttp、Retrofit、android-async-http；
> 如：Xutils有网络请求、图片加载、数据存储、view注解，相对来说功能太杂，没有专注于网络请求这一块，也可以这样理解：依赖性太强，万一不维护了，或者中间有模块出现问题了，影响相对来说就很大，所以这个不建议用来做网络请求，还是选择专注于某一领域的框架会好一些。
> Android-async-http：作者已经不维护了，所以这个框架，用的人也相对来说很少了。
> 接下来就分析Volley、OkHttp、Retrofit这三个网络请求库
> 一、OkHttp
> 1）其实android系统里面有自带的api进行网络请求，也就是HttpClient、HttpUrlConnection，目前 HttpClient已经被废弃，而Android-async-http是基于HttpClient的，所以作者放弃去维护Android-async-http。
> 2）OkHttp是Square公司开源的针对Java和Android程序，封装的一个高性能Http请求库，所以它的职责跟HttpUrlConnection是一样的，支持spdy、http2.0、websocket，支持同步和异步，而且OkHttp又封装了线程池，封装了数据转换，封装了参数使用、错误处理等，api使用起来更加方便。可以把它理解成是一个封装之后的类似HttpUrlConnection的一个东西，但是在使用时候仍然需要自己再做一层封装，这样使用一个框架才会更顺手。
> 二、Volley
> Volley是google官方出的一套小而巧的异步请求库，该框架封装的扩展性很强，支持HttpClient、HttpUrlConnection,甚至支持OkHttp。
> 而且Volley里面也封装了ImageLoader，所以如果你愿意也可以使用图片加载框架，不过这块功能没有一些专业的图片加载框架强大，对于稍复杂点的需求还是需要到专门的图片加载框架
> Volley也有缺陷，比如不支持post大数据，所以不适合上传文件。不过Volley设计的初衷本身也就是为频繁的、数据量小的网络请求而生。
>
> 三、Retrofit
> Retrofit是Square公司出品的默认基于OkHttp封装的一套RESTful网络请求框架，RESTful可以说是目前流行的一套api设计的风格，并不是标准。Retrofit的封装可以说是很强大，里面涉及到一堆的设计模式，可以使用不同的http客户端，虽然默认是用http，可以使用不同Json Coonverter来序列化数据，同时提供对RxJava的支持，使用Retrofit+OkHttp+RxJava+Dagger2可以说是现在比较潮的框架，但相对来说门槛比较高。
>