---
layout: post
title: 热门技术
tags:
- java
categories: boatt
description: 热门技术.
---
## 热门技术
热门技术

<!-- more -->
## 日志详情

> ## apk统计实践
>
> > 你的app被别人下载使用后,你关心哪些数据
>
> ### 三方统计sdk 约1个小时
>
> #### 友盟统计实践
>
> 1. 注册友盟账号
>    1. 来到个人中心->基础统计(立即使用)->添加应用-->得到appKey`57173b92e0f55a54960032e9`
> 2. 参考集成文档开始集成
>    1. 集成基本统计功能(新增用户、活跃用户、启动次数、使用时长等基本数据)
>    2. 页面统计(页面访问路径、访问深度（PV）的数据)
>    3. 自定义事件(应用程序中埋点来统计用户的点击行为)
>       1. 统计多少人有下载行为,以及下载程序名称
>    4. 错误上报,默认是开启的
>    5. 在线参数:动态修改应用的欢迎语，修改应用中开关选项的"on"或"off"，以及类似游戏中虚拟物品的价格等,这个通过自己服务器也能实现_可选
>    6. 社交统计:只需要调用一行代码，便可享用到丰富的社交行为和社交用户分析报表。_可选
>
> #### 了解友盟一些不足的地方
>
> > http://news.chinabyte.com/413/13492413.shtml
>
> #### 百度统计
>
> 1. 注册百度账号
> 2. 添加应用分配appKey(`0ea1c8cc30`)
> 3. 下载sdk开始集成
>
> #### Google Analytics Android_了解
>
> > - 产品介绍:https://developers.google.com/products/
> > - 分析查看:https://www.google.com/analytics/
> > - 官方demo:https://github.com/googlesamples/google-services.git
> > - 针对一些国外应用
> > - 官方文档:https://developers.google.com/analytics/devguides/collection/android/v4/star
>
> #### 运行demo
>
> 1. 下载demo `https://github.com/googlesamples/google-services.git`
> 2. 参考文档:`https://developers.google.com/analytics/devguides/collection/android/v4/start`
>
> #### 集成步骤
>
> 1. 创建analytics账号:https://www.google.com/analytics/ 在这个网站，你可以使用你的gmail账号登录,获取跟踪id(UA-76559002-1)
> 2. 根据https://developers.google.com/analytics/devguides/collection/android/v4/start文档完成即可
> 3. 集成完毕通过https://www.google.com/analytics/查看效果
>
> #### 诸葛io_了解
>
> > 诸葛io,是一款基于用户行为分析的精细化数据分析工具
>
> ## apk瘦身实践 约2个小时
>
> > 看瘦身笔记
>
> ## apk加固实践 约1个小时
>
> > - 三方平台:梆梆安全,爱加密,360加固保,阿里聚安全
> > - 个人实践:`http://blog.csdn.net/jiangwei0910410003/article/details/48415225`
>
> 
>
> ## apk打包实践 约1个小时
>
> > 看打包实践笔记