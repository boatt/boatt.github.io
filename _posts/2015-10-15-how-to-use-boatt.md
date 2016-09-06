---
layout: post
title: FastJson最全面的Json解析框架
tags:
- boatt
- Jacman
categories: boatt
description: .
---
## 主题描述
阿里巴巴FastJson是一个Json处理工具包，包括“序列化”和“反序列化”两部分。

<!-- more -->
## 日志详情

> 1、FastJson最全面的Json解析框架
> FastJson使用详解
> 一、阿里巴巴FastJson是一个Json处理工具包，包括“序列化”和“反序列化”两部分，它具备如下特征：
> 速度最快，测试表明，fastjson具有极快的性能，超越任其他的Java Json parser。包括自称最快的JackJson；
> 功能强大，完全支持Java Bean、集合、Map、日期、Enum，支持范型，支持自省；无依赖，能够直接运行在Java SE 5.0以上版本；支持Android；开源 (Apache 2.0)
> Fastjson API入口类是com.alibaba.fastjson.JSON，常用的序列化操作都可以在JSON类上的静态方法直接完成。
>
> FastJson解析JSON步骤
>
>    A、服务器端将数据转换成json字符串
>       首先、服务器端项目要导入阿里巴巴的fastjson的jar包至builtPath路径下（这些可以到fastjson官网下载：http://code.alibabatech.com/wiki/display/FastJSON/Home-zh）
>  然后将数据转为json字符串，核心函数是：
>
> public static String createJsonString(Object value)
>     {
>         String alibabaJson = JSON.toJSONString(value);
>         return alibabaJson;
>     }
>
> B、客户端将json字符串转换为相应的javaBean
>
>   首先客户端也要导入fastjson的两个jar包
> 1、客户端获取json字符串
>
>
> 2、使用泛型获取javaBean（核心函数）
>
> 2、Gson一句代码搞定Json的解析
>  （一） Gson简介
>  谷歌GSON这个Java类库可以把Java对象转换成JSON，也可以把JSON字符串转换成一个相等的Java对象。Gson支持任意复杂Java对象包括没有源代码的对象。
>
>
> （二）Gson解析Json步骤
>  A、服务器端将数据转换成json字符串
>    首先、服务器端项目要导入Gson的jar包到BuiltPath中。（
> Gson的jar：http://code.google.com/p/google-gson/ 
>
> 
>
> 
>
>
> 然后将数据转为json字符串，核心函数是：
>     public static String createJsonString(Object value)
>     {
>         Gson gson = new Gson();
>         String str = gson.toJson(value);
>         return str;
>     }
> B、客户端将json字符串转换为相应的javaBean
>     首先客户端也要导入gson的两个jar包，json的jar就不需要导入了（因为android项目中已经集成了json的jar包所以这里无需导入）
>    1、客户端获取json字符串
>
>
> 2、使用泛型获取javaBean（核心函数）
> ​    
>