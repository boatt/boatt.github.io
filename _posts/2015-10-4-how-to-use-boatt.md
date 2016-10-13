---
layout: post
title: ButterKnife（黄油刀）的用法 
tags:
- boatt
- Jacman
categories: boatt
description: .
---
## 主题描述
优美代码之道。

<!-- more -->
## 日志详情

> 1、ButterKnife（黄油刀）的用法 
> 优势：
> 1.强大的View绑定和Click事件处理功能，简化代码，提升开发效率
> 2.方便的处理Adapter里的ViewHolder绑定问题
> 3.运行时不会影响APP效率，使用配置方便
> 4.代码清晰，可读性强
>
> 使用总结：
> 1. Activity ButterKnife.bind(this);必须在setContentView();之后，且父类bind绑定后，子类不需要再bind
> 2. Fragment ButterKnife.bind(this, mRootView);
> 3. 属性布局不能用private or static 修饰，否则会报错
> 4. setContentView()不能通过注解实现。（其他的有些注解框架可以）
>
> 官网 http://jakewharton.github.io/butterknife/
> 使用步骤：
> 一.导入ButterKnife jar包：
> 1）如果你是Eclipse,可以去官网下载jar包
> 2）如果你是AndroidStudio可以直接 File->Project 		Structure->Dependencies->Library dependency 搜索	butterknife即可，第一个就是
> 3）当然也可以用maven和gradle配置
>
> 注：官网和github也有对应的引用步骤。
>
> 二.常见使用方法：
> 1）由于每次都要在Activity中的onCreate绑定Activity，所以个人建议写一个BaseActivity完成绑定，子类继承即可
>      注：ButterKnife.bind(this)；绑定Activity 必须在setContentView之后：
>      实现如下（FragmentActivity 实现一样）：
>
> 2）绑定fragment
>
> 3）绑定view
> @Bind(R.id.hello_world)  
> TextView mHelloWorldTextView;  
> @Bind(R.id.app_name)  
> TextView mAppNameTextView;//view  
> 4）绑定资源
> @BindString(R.string.app_name)  
> String appName;//sting  
> @BindColor(R.color.red)  
> int textColor;//颜色  
> @BindDrawable(R.mipmap.ic_launcher)  
> Drawable drawable;//drawble  
> @Bind(R.id.imageview)  
> ImageView mImageView;  
> @Bind(R.id.checkbox)  
> CheckBox mCheckBox;  
> @BindDrawable(R.drawable.selector_image)  
> Drawable selector;  
>