---
title: 最近发现的几个优秀库
author: 李攀
layout: post
---

最近几天发现几个有用的库，以后产品上一定能用得上，记录一下。

### [Lottie](http://airbnb.io/lottie/)

真可谓大幅降低开发工作量的库，以前客户端用程序来实现动画是一件既耗时又很难达到设计师效果的使，加上项目开发周期一般都会比较紧，动画相关的功能优先级会放低，优先级放低，很多时候也就意味着被砍掉了，原本提升用户体验的效果，结果被无奈的大打折扣。
Airbnb 开源的这个库解决了开发的问题，只要设计师通过 AE，尽情实现想要的效果，然后通过 bodymovin 插件导出 json，开发只需要用 Lottie 即可完成动画效果。
而且，Lottie 同时提供了 [iOS](https://github.com/airbnb/lottie-ios)、[Android](https://github.com/airbnb/lottie-android) 和 [Web](https://github.com/airbnb/lottie-web) 三端的库，这样也可以保证同一个效果在各端显示的一致性，Android 小哥再也不用愁和 iOS 小哥实现出来的效果不一样了，同时也保证了多个产品线风格的统一。
![Lottie](http://airbnb.io/lottie/images/Introduction_01_sm.gif)

### [Intro.js](https://github.com/usablica/intro.js)

看名字基本就知道是干嘛的，对，就是给 Web 产品用来做新功能一步步教程引导的库，这个相信有 Web 产品的同学们都能够用得上。
![introJs](https://raw.githubusercontent.com/usablica/intro.js/gh-pages/img/introjs-demo.png)

### [MPAndroidChart](https://github.com/PhilJay/MPAndroidChart) | [Charts](https://github.com/danielgindi/Charts)

基本上常用的图表都有了，还带缩放、拖拽、动画等，满足绝大多数场景。
![Charts](https://github.com/PhilJay/MPAndroidChart/blob/master/screenshots/barchart2d.png)

### [Hero](https://github.com/lkzhao/Hero)

iOS 上非常优雅的动画转场移动库。

![1](https://camo.githubusercontent.com/ad3b44a1f8c9ad51ba120b6281b03335bd78bb22/68747470733a2f2f63646e2e7261776769742e636f6d2f6c6b7a68616f2f4865726f2f656262336632632f5265736f75726365732f66656174757265732e737667)
![2](https://camo.githubusercontent.com/f5211ae92678aa22b6edf2d18e08b0dce63bcaa4/68747470733a2f2f63646e2e7261776769742e636f6d2f6c6b7a68616f2f4865726f2f656262336632632f5265736f75726365732f6665617475726573322e737667)

### [ijkplayer](https://github.com/Bilibili/ijkplayer)

B 站开源的一款基于 FFmpeg 的视频播放器，支持 Android 和 iOS 两个平台，大多数的坑，特别是 Android 上的坑都被踩过了。