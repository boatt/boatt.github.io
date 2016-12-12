---
layout: post
title: Vitamio 是什么？
tags:
- android
categories: boatt
description: Vitamio 是什么？.
---
##  Vitamio 是什么？
Vitamio 是一款 Android 与 iOS 平台上的全能多媒体开发框架，全面支持硬件解码与 GPU 渲染。Vitamio 凭借其简洁...

<!-- more -->
## 日志详情

Vitamio 是一款 Android 与 iOS 平台上的全能多媒体开发框架，全面支持硬件解码与 GPU 渲染。Vitamio 凭借其简洁易用的 API 接口赢得了全球众多开发者的青睐。到目前，全球已经有超过 1800 种应用在使用 Vitamio，覆盖用户超过 2亿 。

Vitamio 能够流畅播放720P甚至1080P高清MKV，FLV，MP4，MOV，TS，RMVB等常见格式的视频，还可以在 Android 与iOS 上跨平台支持 MMS, RTSP,RTMP, HLS(m3u8) 等常见的多种视频流媒体协议，包括点播与直播。

## [流媒体支持 ](http://www.vitamio.org/docs/Basic/2013/0429/3.html#toc-liu-mei-ti-zhi-chi)

Vitamio 支持各种常见的流媒体协议，可以点播或者直播音频和视频，例如如下常见协议均能无缝支持：

         MMS

         RTSP (RTP,SDP), RTMP

         HTTPprogressive streaming

         HLS - HTTPlive streaming (M3U8)

## [音频和视频格式 ](http://www.vitamio.org/docs/Basic/2013/0429/3.html#toc-yin-pin-he-shi-pin-ge-shi)

Vitamio 使用了 [FFmpeg](https://github.com/yixia/FFmpeg-Android) 做为媒体解析器和最主要的解码器，同时开发了针对不同移动平台的硬解码方案，能够完美支持 H.264/AVC、H.263、 MPEG4 等常见的视频编码，覆盖上百种多媒体格式。下表只是一些最常见的视频格式支持，除特殊标明，全部支持硬件加速：

         DivX/Xvid

         WMV (一般只有软解码)

         FLV

         TS/TP

         RMVB (只有软解码)

         MKV

         MOV

         M4V

         AVI

         MP4

         3GP

## [字幕支持 ](http://www.vitamio.org/docs/Basic/2013/0429/3.html#toc-zi-mu-zhi-chi)

Vitamio 对字幕的支持很优秀，包括各种常见外挂字幕与很多视频格式的内嵌字幕，同多个字幕等特性的支持也非常完善。比如：

         SubRip(.srt)

         Sub StationAlpha(.ssa) / Advanced Sub Station Alpha(.ass)

         SAMI(.smi/.sami)

         MicroDVD(.sub/.txt)

         SubViewer2.0(.sub)

         MPL2(.mpl/.txt)

         Matroska(.mkv) 内置字幕

## [更多特性 ](http://www.vitamio.org/docs/Basic/2013/0429/3.html#toc-geng-duo-te-xing)

除了上面列出的常见功能之外，Vitamio 还做了相当多人性化的工作：

         多音轨与字幕支持

         细致的CPU 与 GPU 优化

         支持手机到平板各种设备

         流媒体播放缓冲支持

         播放画面比例大小随手调节

         自动文字编码检测，拒绝乱码

还有更多新特性没有被列出，请参考开发文档。

# Vitamio 4.0 新手入门

Vitamio项目发展迅猛，官方群突破800位开发者，基于Vitamio的项目突破1000个，使用Vitamio提供优质播放体验的用户超过1亿。也欢迎大家分享你的Vitamio使用经验，本文将进一步介绍Vitamio的简单使用方法。

## 下载 

目前Vitamio的项目托管在Github上面：[https://github.com/yixia](https://github.com/yixia) ，这里有很多公司的开源项目，其中：

1、VitamioBundle是Vitamio核心插件，（大家可以搜一下"Android Library"这个关键字，和jar差不多的用途），可以方便集成到项目中。

2、VitamioDemo是Vitamio的官方例子。

## 简介 

Vitamio的中文名称为“维他蜜”
Vitamio 是一款 Android 平台上的全能多媒体开发框架。Vitamio 凭借其简洁易用的 API 接口赢得了全球众多开发者的青睐。到目前，全球已经有超过 1000 种应用在使用 Vitamio，覆盖用户超过 1亿。

Vitamio 能够流畅播放720P甚至1080P高清MKV，FLV，MP4，MOV，TS，RMVB等常见格式的视频，还可以在 Android 上支持
MMS, RTSP, RTMP, HLS(m3u8) 等常见的多种视频流媒体协议，包括点播与直播。
支持 ARMv6 和
ARMv7 两种 ARM CPU，同时对 VFP, VFPv3, NEON 等指令集都做相应优化。

支持 Android2.1+ 系统，支持超过 95% 的 Android 市场。同时 Android 2.1 之前的系统也基本支持，不过没做详细测试。

更多[Vitamio的介绍](http://vitamio.org/pages/whats-vitamio?locale=zh-CN)参照这里。

 

extPlayer

**导入使用**** **

1、导入。下载回来后大家可能发现没有.project工程文件，可以通过File -> Import -> Android ->Existing Android Code Into Workspace来导入工程，然后改一下工程名称即可。

2、将VitamioBundle工程作为Android Library引入Demo工程使用即可。

**关注****Vitamio **

官方微博：[http://weibo.com/vitamio](http://weibo.com/vitamio)

官方网站/论坛：vitamio.org

Vitamio QQ 3群:283274315

**其他**** **

1、官方建议以Android Library方式使用Vitamio插件，以便后续方便升级。如果需要拷贝集成到一个工程，可能会报错找不到io.vov.vitamio.R.raw.libarm（硬编码导致的问题）

2、 Vitamio最新版本为4.0，极力推荐使用新版本。

3、 基于Vitamio仅支持ARMv6+以上的CPU，95%以上的视频格式支持，说明：

a). 无法播放的问题。使用VPlayer来测试链接，如果VPlayer没有问题那Vitamio肯定也没有问题。

b). 各种找不到so文件的情况只有两种情况：不支持设备、没有执行解压解码包。

4、Vitamio最终所有权为炫一下（北京）科技有限公司。

 

# Vitamio测试网络视频地址

Vitamio支持多种流媒体格式，以下是一些视频地址片段案例,提供给大家测试使用：

**HLS - Apple HTTP live streaming - m3u8 ******

[http://devimages.apple.com/iphone/samples/bipbop/bipbopall.m3u8](http://devimages.apple.com/iphone/samples/bipbop/bipbopall.m3u8)
[http://devimages.apple.com/iphone/samples/bipbop/gear1/prog_index.m3u8](http://devimages.apple.com/iphone/samples/bipbop/gear1/prog_index.m3u8)
[http://meta.video.qiyi.com/255/dfbdc129b8d18e10d6c593ed44fa6df9.m3u8](http://meta.video.qiyi.com/255/dfbdc129b8d18e10d6c593ed44fa6df9.m3u8)
[http://3glivehntv.doplive.com.cn/video1/index_128k.m3u8](http://3glivehntv.doplive.com.cn/video1/index_128k.m3u8)

**HTTP ******

[http://www.modrails.com/videos/passenger_nginx.mov](http://www.modrails.com/videos/passenger_nginx.mov)
[http://wsmp32.bbc.co.uk/](http://wsmp32.bbc.co.uk/)

**RTSP ******

[http://m.livestream.com](http://m.livestream.com/) (site)
rtsp://xgrammyawardsx.is.livestream-api.com/livestreamiphone/grammyawards

**MMS ******

mms://video.fjtv.net/setv
mms://ting.mop.com/mopradio
mms://112.230.192.196/zb12

 

# Vitamio产品大全

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image002.jpg)** **[酷6视频](http://as.baidu.com/a/item?docid=2896392&f=web_alad_6)********

酷6视频 Ku6Video 是酷6网竭力打造的手机视频客户端。酷6网作为国内最大的短视频网站，其客户端覆盖了资讯、娱乐、搞笑、拍客、时尚等多个频道的海量视频资源，集播放、下载、上传、分享等全新功能，让手机受众尽享视频饕鬄盛宴

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image003.gif)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image005.gif)** **[CNTV](http://as.baidu.com/a/item?docid=2305962&pre=web_am_se&f=web_alad_6@next)********

CNTV 中国网络电视台为中国网络电视台官方推出的安卓客户端。 汇聚CCTV和CNTV精彩资源，提供最全面最丰富的中国电视直播、点播服务，全天24小时滚动更新。 精品资讯细分：国家大事、社会热点新闻，一览无余 实时直播频道：王牌电视节目,随时随地看直播 精彩专题推荐：新闻、时政、经济、人文和热播影视剧在内的新闻热点聚焦 赶紧下载玩转2013年指尖上的春晚，CNTV中国网络电视……

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image003.gif)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image007.gif)** **[视讯中国](http://www.wandoujia.com/apps/com.cnlive.movie)********

是一款装机必备的免费高清电影软件。海量收录新片，爱情，动作，动漫，惊悚，喜剧等元素的高清电影，随心所欲的在线观看和下载。专为Android手机订制的视频娱乐客户端产品，为用户提供能了流畅便捷的客户端视频播放体验。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image003.gif)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image009.gif)** **[321影音](http://www.eoemarket.com/show/index/?appId=76026)********

321影音是android手机上功能最多、性能最好的多媒体播放软件，集视频播放、音频播放、电视直播、广播电台于一身，支持几乎所有流行的视频、音频格式，它将让您的android手机变成您的掌上享乐中心！

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image003.gif)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image011.gif)** **[厦门音乐广播](http://apk.hiapk.com/html/2013/02/1190526.html?module=256&info=plPolfOXUE5/Xq1k)********

厦 门音乐广播伴随着新世纪的到来，厦门人民广播电台加速发展，目前已形成了智能化控制管理的高速宽带多媒体信息网络，技术装备水平在全国城市电台中位居前 列，电波覆盖范围包括厦门、泉州、龙海、南安、晋江、石狮以及金门等地区，覆盖人口达六百多万，收听人数、收听率节节上升。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image003.gif)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image013.gif)** **[听世界](http://www.wandoujia.com/apps/com.ting)********

听世界，是一款专业的有声作品播放器，免费提供各类精彩的有声小说、广播剧、相声评书、声音故事、有声教材、幽默笑话等内容，解放您的双眼，让您爱上听的感觉！

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image014.gif)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image016.jpg) [酷云TV](http://www.kuyun.com/)

酷云TV是[北京十分科技有限公司](http://www.kuyun.com/)出品的一款电视互动产品，它可以使电视节目变得更加有趣。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image014.gif)

 [![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image018.jpg)](https://play.google.com/store/apps/details?id=com.iuculano.fplayer&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5pdWN1bGFuby5mcGxheWVyIl0.) [FPlayer](https://play.google.com/store/apps/details?id=com.iuculano.fplayer&feature=search_result#?t=W251bGwsMSwxLDEsImNvbS5pdWN1bGFuby5mcGxheWVyIl0.) 

Questo è un lettore video usatoprincipalmente da TVItaliane.

Cerca AllMyTv peravere la tv nel tuosmartphone!

TV Italiane.

FPlayer non contiene pubblicità inmodalità push e non ne conterrà mai.

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image014.gif)

[![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image020.jpg)](https://play.google.com/store/apps/details?id=com.muratkilic.tvgoo&feature=search_result#?t=W251bGwsMSwyLDEsImNvbS5tdXJhdGtpbGljLnR2Z29vIl0.) [TVGOO Live Tv](https://play.google.com/store/apps/details?id=com.muratkilic.tvgoo&feature=search_result#?t=W251bGwsMSwyLDEsImNvbS5tdXJhdGtpbGljLnR2Z29vIl0.)

You can watch free online tv channelsall over the world with tvgoo application. Updating countries and channelsautomaticaly.

Tags: online tv, live tv, tv list,free, watch, stream, mobile tv

AvailableCountries: turkey, france, germany, russia, greece, italia, italy, spain,ukraine, brazil, azerbaijan, albania, armenia, egypt, estonia, bulgaria,finland, uk, usa, belgium, india, netherlands, egypt, hungary, japan, china,macedonia, kosovo, norway, romania, usa 

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image014.gif)

[![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image022.jpg)](http://www.kugou.com) [酷狗音乐](http://www.kugou.com)

酷狗音乐手机版是最受欢迎的音乐播放器，有强大的音乐搜索和高速下载功能、 全球最全音乐曲库，最专业的音频解码核心技术，完美实现各种音频格式的高保真播放。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image003.gif)

**![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\msohtmlclip1\01\clip_image024.jpg)**** **[天天动听](http://www.ttpod.com/)********

天 天动听手机版是一款功能强大、完全免费的手机音乐播放软件，[3]支持歌词和歌曲图片下载，皮肤随心更换，更有炫丽震撼的可视化效果，同时预置丰富的均衡 器效果，支持音效增强，简洁人性化的操作，给追求音乐品质的呢带来了手机听歌的全新体验。数据表明，天天动听已经成为拇指一族必备的音乐播放工具！

# Vitamio FAQ

**Vitamio****名字的由来**** **********

Vitamio的中文名称为“维他蜜”。
Vitamio 来源于英文单词Vitamin（维他命），希望Vitamio对于安卓多媒体开发者的重要性，就像Vitmain之于人体一样不可缺少。

**Vitamio与VPlayer什么关系？ ******

Vitamio基于VPlayer开发，所以VPlayer能播放的Vitamio也能。

**Vitamio支持哪些指令集的CPU？ ******

支持 ARMv6 和 ARMv7 两种 ARM CPU，同时对 VFP, VFPv3, NEON 等指令集都做相应优化。

**Vitamio支持的Android版本 ******

支持 Android2.1+ 系统，支持超过 95% 的 Android 市场。同时 Android 2.1 之前的系统也基本支持，不过没做详细测试。

**E/Vitamio(1557): java.io.FileNotFoundException: No contentprovider ******

这个不是错误，是正常的处理。现在播放视频是这样做的：先把 URL 当做一个ContentProvider 来打开，如果打不开，就直接当做 URL 来打开。

**为什么会弹出提示框要求安装Vitamio Plugin？ ******

因为你下载和使用的是较早的Vitamio版本!

**视频/视频流(rtp、rtsp等)播放不了的问题！ ******

可能存在以下几种情况：

         视频本身就存在问题，你可以用其他播放器播放一下，是否能正常播放。

         本地网速不给力/设备本身配置过低。

         视频源卡，本身带宽不够，直接访问也很慢。

         嵌套了m3u8地址

         视频被加密了

建议先使用VPlayer和其他播放器来测试视频，确保排除外在因素。

**如何调用VPlayer来播放视频？ ******

[?](http://www.vitamio.org/docs/FAQ/2013/0508/7.html#)

rivatevoidstartPlayer(Stringurl, String title) {

   Intent i =newIntent();

   i.setComponent(newComponentName("me.abitno.vplayer.t","me.abitno.vplayer.VideoActivity"));

   i.setAction("me.abitno.vplayer.action.VIEW");

   i.setData(Uri.parse(url));

   i.putExtra("displayName", title);

   startActivity(i);



**在混淆时如何忽略Vitamio相关类库的混淆？ ******

[?](http://www.vitamio.org/docs/FAQ/2013/0508/7.html#)


  -keepclassio.vov.utils.** { *; }
  -keepclassio.vov.vitamio.**
  { *; }

**播放时拖动进度条，拖动进度不准确? ******

这是正常现象，不是播放器的问题。默认seek要到最近的关键帧，不能保证任何时间戳上都有关键帧，除非你是intra-only 的编码方式。

**如何开启硬解码? ******

实例化MediaPlayer时启用第二个参数。

[?](http://www.vitamio.org/docs/FAQ/2013/0508/7.html#)

publicMediaPlayer(android.content.Context ctx,booleanpreferHWDecoder) 

**为什么每次软件升级都会重新解压解码包? ******

为确保与当前升级软件中Vitamio的版本保持一致。Vitamio Java层的代码都已经公开，你可以自己改逻辑。

 

# Vitamio不支持特性列表

这里列举目前Vitamio不支持或支持不够好的功能：

         1. 不支持ARMv6以下的CPU（支持ARMv6+，大部分无法播放的问题均是此问题，注意模拟器请使用4.0以上版本）

         2. 不支持加密（例如DRM）视频、嵌套的m3u8（如果m3u8中有无法播放的干扰链接也会停止而不会跳过）

         3. 不支持获取Audio SessionId对象

         4. 不支持视频缩略图截图（但支持对正在播放的视频截图，函数名：getCurrentFrame）

         5. 不支持setSurface方法

         6. 设置字幕（subPath）必须是本地的字幕文件

         7. 有些机型硬解码不够成熟，建议让用户手动切换软解/硬解（VPlayer，MX player等主流播放器也是这样处理的）。

         8. 不支持华为S8600等少数几款机型，具体表现为无法解压解码包(一直停留在解压界面)。

         9. 不支持Logcat信息输出屏蔽（so里面输出的，但应用层可以屏蔽掉）

         10. 不支持自定义网络协议（你们需要修改[我们公开的 FFmpeg 代码](https://github.com/yixia/FFmpeg-Android)，在其中添加相应的 libavformat 模块就可以了，与加密和内存中数据处理是一样的或者[通过代理来转换协议](http://blog.csdn.net/hellogv/article/details/8301504)。

         11. 目前不支持两个视频同时播放

         12. 如果mp3包含了1帧视频（比如mp3专辑图片），此mp3将当成视频处理，播完这一帧就会马上结束。（Vitamio会先检测是否包含视频，如果包含视频（大于0帧）即当视频处理，否则当音频处理）。

         13.由于Youku的m3u8不标准,导致Vitamio对Youku视频支持不好，具体表现为拖拽进度条无效、突然中断。（在Vitamio 4.0中已经解决）

         14. rmvb不支持硬解，2.1以下的也不支持硬解（硬件限制）

         15. hls 不支持可变码率（在Vitamio 4.0中已经解决）

         16. 不支持swf，但支持flv（建议安装Adobe，然后用WebView播放）

# Vitamio视频缓冲处理

受限于网速等原因，播放网络视频时一般都会要加上缓冲处理，一般可以通过设置加大缓冲和显示正在缓冲的进度条来改善体验。

**关键代码 ******

[?](http://www.vitamio.org/docs/Tutorial/2013/0508/12.html#)      


  /** 是否需要自动恢复播放，用于自动暂停，恢复播放 */
     
  privatebooleanneedResume;


  @Override
     
  publicbooleanonInfo(MediaPlayer arg0,intarg1,intarg2) {
          switch(arg1) {
         
  caseMediaPlayer.MEDIA_INFO_BUFFERING_START:
              //开始缓存，暂停播放
              if(isPlaying()) {
                  stopPlayer();
                  needResume =true;
              }
              mLoadingView.setVisibility(View.VISIBLE);
              break;
         
  caseMediaPlayer.MEDIA_INFO_BUFFERING_END:
              //缓存完成，继续播放
              if(needResume)
                  startPlayer();
             
  mLoadingView.setVisibility(View.GONE);
              break;
         
  caseMediaPlayer.MEDIA_INFO_DOWNLOAD_RATE_CHANGED:
              //显示 下载速度
              Logger.e("download
  rate:"+ arg2);
              break;
          }
          returntrue;
      }

 






