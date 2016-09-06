---
layout: post
title: OKHTTP的实际开发中的用法
tags:
- boatt
- Jacman
categories: boatt
description: OKHTTP的实际开发中的用法.
---
## 主题描述
OKHTTP的实际开发中的用法。

<!-- more -->
## 日志详情

>  1、OKHTTP的实际开发中的用法
>
>       Android系统提供了两种HTTP通讯类HttpURLConnection和HttpClient，Android6.0后，HttpClient就被google公司给废弃了。尽管Google在大部分安卓版本中推荐使用HttpURLConnectin，但是这个类相比HttpClient实在是太难用，太弱爆了。
>       OkHttp是一个相对成熟的解决方案，据说Android4.4的源码中可以看到HttpURLConnection已经替换成OkHttp实现了。所以我们更有理由相信OkHttp的强大。
> 使用范围：OkHttp支持Android2.3及其以上版本。对于Java，JDK1.7以上。
> 基本使用（GET）：
> ​    
>
>      总结：Request是OkHttp中访问的请求，Builder是辅助类，Response就是OkHttp的响应。
> POST提交键值对：
>     很多时候我们会需要通过POST方式把键值对数据传送到服务器。OkHttp提供了很多方便的方式来做这件事情。
>
>   总结：通过上面的例子我们可以发现，OkHttp在很多时候使用都是很方便的，而且很多代码也有重复，因此特地整理了下面的工具类。 注意：
>     1、OkHttp官方文档并不建议我们创建多个OkHttpClient，因此全局使用一个。 如果有需要，可以使用clone方法，再进行自定义。
>     2、enqueue为OkHttp提供的异步方法。
> OkHttpUtil类当中的方法：
> ①　不会开启异步线程方法：
>   public static Response execute(Request request)；
> ②　开启异步线程访问网络：
>       public static void enqueue(Request request, Callback responseCallback)；
> ③　开启异步线程访问网络，且不在意返回结果（实现空callback）：
>     public static void enqueue(Request request);
> ④　使用了HttpClient的API，只是为了方便：
> Public static String formatParams(List<BasicNameValuePair>params)；
> ⑤　为HttpGet的Url方便的添加多个name和Value参数：
> Public static StringattachHttpGetParams(Stringurl,List<BasicNameValuePair> params);
> ⑥　位HttpGet的url方便的添加一个name和value参数：
>  Public static String attachHttpGetParam(String url, String name, String value);
>