---
layout: post
title: 多渠道打包
tags:
- android
categories: boatt
description: 多渠道打包.
---
##  多渠道打包
多渠道打包

<!-- more -->
## 日志详情

> 第一步：
>
> 在配置文件里配置meta-data标签
>
> 第二步：
> 在app目录下build.gradle配置
>
> ```
> signingConfigs {
>     config {
>         keyAlias 'key别名'
>         keyPassword 'key密码'
>         storeFile file('../app/sobig.jks')
>         storePassword 'jks密码'
>     }
> }
> ```
>
> --
>
> ```
>   defaultConfig {
>     applicationId "com.saipeisi.sobig"
>     minSdkVersion 14
>     targetSdkVersion 21
>     versionCode 2010000
>     versionName "1.0.0"
>
>     signingConfig signingConfigs.config
>
>     // dex突破65535的限制
>     multiDexEnabled true
>     // 默认是umeng的渠道
>     manifestPlaceholders = [UMENG_CHANNEL_VALUE: "umeng"]
> 	}
> ```
>
> --
>
>  	productFlavors {
>
> ```
>     wandoujia {}
>     _360 {}
>     baidu {}
>     xiaomi {}
>     tencent {}
>     sougou {}
>     oppo {}
>     mumayi {}
>     meizu {}
>     Lenovo {}
>     kuchuan {}
>     jinli {}
>     jifeng {}
>     huawei {}
>     sobig {}
> }
> productFlavors.all { flavor ->
>     flavor.manifestPlaceholders = [UMENG_CHANNEL_VALUE: name]
> }
> ```
>
> --
>
>  	buildTypes {
>
> ```
>         signingConfig signingConfigs.config
>     }
>     release {
>         signingConfig signingConfigs.config
>     }
> }
> ```