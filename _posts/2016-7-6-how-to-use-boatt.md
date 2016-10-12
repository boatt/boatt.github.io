---
layout: post
title: WebAPP（H5）与原生APP的交互设计区别
tags:
- android
categories: boatt
description: WebAPP（H5）与原生APP的交互设计区别.
---
##  WebAPP（H5）与原生APP的交互设计区别
WebAPP（H5）与原生APP的交互设计区别

<!-- more -->
## 日志详情

> WebAPP和原生APP同为移动端，很少有研究这两项的交互区别，最近公司做了一次从原生APP到WebAPP（HTML5 ）的移植，故总结一下期间遇到的问题及不同点总结。
>
> > （作者注：本文WAP经指正意为 webAPP ,many thx~）
>
> 从使用场景上，WAP用户面临比APP用户更严峻的问题：
>
> **1、页面跳转更加费力，不稳定感更强**
>
> 思考点：如何减少跳转（扁平结构、页面布局技巧），增加数据及展示的流畅流程及稳定性（技术）
>
> **2、更小的页面空间（由于浏览器的导航本身占用一部分屏幕空间），更大的信息记忆负担**
>
> > 移动设备的屏幕要小得多。这种如同透过门缝进行的阅读增加了认知的负担。人脑的短期记忆是不稳定的，用户在滚动屏幕的过程中需要临时记忆的信息越多，他们的表现就会越差。
> >
> > ——《贴心设计：打造高可用性的移动产品》
>
> 思考点：排版更清晰、信息更简练 （可在APP基础上去掉一些丰富、复杂的视觉表现）
>
> **3、导航不明显，原有底部导航消失，有效的导航遇到挑战**
>
> 思考点：如何有效的提供导航？有哪些形式？
>
> **4、交互动态效果收到限制，影响一些页面场景、逻辑的理解。**
>
> 思考点：比如登录注册流程的弹出、完成及异常退出，做好文字提示。
>
> 针对以上困境，解决方法总结如下。
>
> **首先，从APP到WAP版，在产品上，最明显且核心的：**
>
> 1、精简功能，只将核心的任务实现，非核心的枝节可考虑删减。
>
> 2、做好新的WAP导航.
>
> 3、补充从WAP站对 下载APP 的引导。
>
> **>> WAP导航怎样设计？**
>
> 一、常见的几种WAP导航样式
>
> 1.1顶部底部导航的设计：
>
> [![1](http://www.aiyingli.com/wp-content/uploads/2015/02/1-1024x454.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/1.png)
>
> 常见WAP导航设计
>
> 1.2导航快捷键设计：
>
> 美团：顶部栏固定位置
>
> 淘宝：悬浮圆圈–可展开的按钮
>
> 优酷：非首屏时页面右侧悬浮
>
> [![2](http://www.aiyingli.com/wp-content/uploads/2015/02/2-1024x463.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/2.png)
>
> 导航快捷方式
>
> 二、有效的导航设计
>
> 1、基本的快捷导航中包括 返回常用页面（如 首页 我的 等）的快捷方式
>
> 2、出现深层架构时 及时补充返回重要层级页面的快捷方式
>
> 3、情境式导航，方便用户快捷跳转到ta想去的页面，如购买结束时提供查看订单详情的按钮。
>
> ps：WAP页更加需要画页面跳转的流程图，摸清各个页面的入口，尤其是页面返回的流程；有些简化的返回按钮，可以特殊注明返回到的页面
>
> **>>怎样引导用户下载APP?**
>
> 一、在哪里出现引导？
>
> 一般 首页、核心任务的页面（如 电商WAP的商品详情页 、视频WAP的视频观看页）
>
> 二、引导下载APP有哪些形式？
>
> 1、页面顶部放置下载条    2、页面底部悬浮层引导  3、融合在页面首屏中
>
> 4、下载按钮形式    5、底部foot里含： 客户端下载入口
>
> [![3](http://www.aiyingli.com/wp-content/uploads/2015/02/3-1024x364.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/3.png)
>
> 下载APP引导
>
> **其次，在设计WAP版上，有以下小技巧可以参考：**
>
> 1、从页面布局上减少跳转：使用交互技巧隐藏文字（eg 腾讯视频）
>
> [![4](http://www.aiyingli.com/wp-content/uploads/2015/02/4-1024x451.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/4.png)
>
> 利用展开收起按钮 减少页面跳转
>
> 2、取消float浮层，增大展示空间（eg：大众点评）
>
> 取消float浮层，同时在详情尾部再次加上 “购买”按钮
>
> [![5](http://www.aiyingli.com/wp-content/uploads/2015/02/5.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/5.png)
>
> 浮层的转换处理
>
> 3、页面中对图片进行缩小（因情况而异）的处理、精简一些标签导航的视觉展现
>
> [![6](http://www.aiyingli.com/wp-content/uploads/2015/02/6-1024x455.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/6.png)
>
> 视觉微调
>
> 技术上注意点：
>
> 1）各手机浏览器的兼容测试
>
> 2）底层服务的调取（能调取，但只有当其是核心功能时才保留 eg：新浪、美团等皆去掉了头像上传功能）
>
> 3）注意离线数据存储，减少数据请求频率。
>
> 4）考虑保存用户的哪些数据：设置、个人数据、阅读锚点、跳出页面等。
>
> 5）避免动效与浏览器的交互冲突
>
> 6）按顺序 异步加载  eg： 腾讯视频
>
> [![7](http://www.aiyingli.com/wp-content/uploads/2015/02/7.png)](http://www.aiyingli.com/wp-content/uploads/2015/02/7.png)
>
> 腾讯视频 异步加载
>
> > 扯一下= =：
> >
> > 虽然WAP页目前处于比较尴尬的地位，我们是由于APP中一些页面需要分享出去才开启制作WAP版。
> >
> > 但是不得不承认，基于WAP的轻APP 更新迭代起来更方便，随着H5技术的成熟和发展，也许以后就是基于H5的WAP APP的天下了0.0。r
>
>
> > 附一些与WAP站设计有关的其它文章：
> >
> > [百度无线交互设计师谈手机Web App设计方法](http://www.imoyo.com.cn/college/cehuachuangyi/shownews1236.html)
> >
> > [iPhone Web App 导航设计探讨](http://www.3lian.com/edu/2011/10-20/13075.html)
> >
> > [轻，会成为未来的趋势吗？](http://www.leiphone.com/news/201406/lite-will-enroll.html)
>
> 作者：maye ；来源：[简书 ](http://www.jianshu.com/p/7c0eac6070b5#)
>
> 转载请注明：[Android开发中文站](http://www.androidchina.net/) » [WebAPP（H5）与原生APP的交互设计区别](http://www.androidchina.net/1764.html)