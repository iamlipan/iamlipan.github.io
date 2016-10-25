---
id: 224
title: 用AWS几分钟搭建自己的VPN服务
author: 李攀
layout: post
permalink: /2016/08/25/setup-own-vpn-with-amazon-aws/
categories:
  - 开发
---

使用VPN的好处很多，比如隐私，匿名，访问被封锁的网站，更安全，以及克服地理上的限制等。然而你总是很难信任你的VPN提供商，因为他们可能会记录或劫持你的流量。所以私有VPN服务器会给你安全感。通过按照这篇教程的步骤，你将在10分钟内搭建起自己的VPN服务器。
![](https://dijmdq8b0p1jt.cloudfront.net/blog/wp-content/uploads/2015/03/AWS-VPN-Webdigi.png)

私有VPN的好处

**简单：** 即使不懂技术也能轻松地按步骤执行
**快速：** 只需10分钟就能跟着教程搭建起一个私有VPN
**私有：** 只有你自己使用的专属VPN
**安全：** 数据加密，密码保护，以及不会留下访问日志的VPN**按需使用：** 你可以根据自己的需要启动或停止VPN服务器
**全球：** 在全球9个区域建立一个或多个VPN（包括美国、东京、新加坡）
**设备支持：** 支持PPTP和L2TP安全协议，也就是说你可以通过Android、iPhone、iPad、PC、MAC，甚至大多数路由器来使用VPN
**开源：** 你可以在github上查看源代码，提交代码。[https://github.com/webdigi/AWS-VPN-Server-Setup](https://github.com/webdigi/AWS-VPN-Server-Setup)
**免费：** AWS的新客户可以在第一年免费使用。

开始建立你的私有VPN服务器
1.首先你要有一个免费的亚马逊云服务账号
访问 [http://aws.amazon.com/free/](http://aws.amazon.com/free/) 完成注册。如果你已有亚马逊账号，请直接登陆。
**注意：完成注册需要一张可以刷美元预售权的信用卡。**
**注意：注册过程中确认联系方式时，需要你语音读出pin码。**

2.选择你的VPN所在区域
这里指的是你的VPN服务器所在的地址。亚马逊的云服务器在全球很多区域都有数据中心，你可以选择其中之一。选择后，你的流量就会通过VPN服务器所在的地方连接互联网。
![](http://blog-10057309.cos.myqcloud.com/region.png)
在国内通常推荐东京或新加坡，网速会稍微快点。

3.在AWS控制面板中打开CLoudFormation
你可以直接点 [这里](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-1) 或者根据下图所示从AWS控制台中进入。
![](http://blog-10057309.cos.myqcloud.com/0002.png)

4.开始用CloudFormation创建堆栈
在左上角点击“创建堆栈”按钮。
![](http://blog-10057309.cos.myqcloud.com/0003.png)

5.为堆栈设置模板
我们可以使用别人配置好的模板，相当于复制了一份别人的机器，很多复杂的安装过程和配置过程都已经做好了，所以我们才能在10分钟就搭建起自己的服务器。
直接选择“指定 Amazon S3 模板 URL”并将下面的链接粘贴上去，点击下一步即可。
[https://s3.amazonaws.com/webdigi/VPN/Unified-Cloud-Formation.json](https://s3.amazonaws.com/webdigi/VPN/Unified-Cloud-Formation.json)
![](http://blog-10057309.cos.myqcloud.com/0004.png)
这里相当于用json文件描述了一个EC2主机的配置，可以直接下载看看文件的内容。

6.指定服务器的详细信息
**堆栈名称:** 也就是VPN的名称**speed：** 选择Standard.VPN-Free
已经足够大多数人使用了。当然如果你要看视频的话也有高速服务可供选择。**Username：** 用于登陆VPN的用户名**VPNPassword：** 用于登陆VPN的密码**VPNPhrase：** 用于L2TP安全连接
![](http://blog-10057309.cos.myqcloud.com/0005.png)

7.不需要添加标签，直接下一步
![](http://blog-10057309.cos.myqcloud.com/0006.png)直接下一步

随后你可以对刚才配置的内容进行一次审核。直接点击创建就好。
![](http://blog-10057309.cos.myqcloud.com/0007.png)

8.等待创建完成
![](http://blog-10057309.cos.myqcloud.com/0009.png)等待创建完成这一步你可能需要等上两分钟左右。当状态变成绿色的CREATE_COMPLETE的时候，就创建完成啦。

9.获取私有VPN服务器IP地址
在输出tab下查看IP地址。这就是你私有VPN服务器的IP地址，记下它，你需要用你的设备连接到这里。
![](http://blog-10057309.cos.myqcloud.com/0010.png)

**连接你的私有vpn**
到这里我们的服务器端设置就完成了。下面我们以windows为例展示如何连接到vpn

1.进入“设置-网络和INTERNET-VPN”，选择添加VPN链接
![](http://blog-10057309.cos.myqcloud.com/0011.png)

2.填写VPN信息
**连接名称**可以随便写。
**服务器名称**要写刚才第9步里获取到的ip地址。
**VPN**类型是PPTP。
**登陆信息的类型**选择用户名和密码

下面的用户名和密码是可选的，如果不填的话，就要在每次登陆时重新填写。
![](http://blog-10057309.cos.myqcloud.com/0012.png)

3.选择连接
选中刚才添加好的VPN，点击连接，输入账号密码，等待出现完成连接
![](http://blog-10057309.cos.myqcloud.com/0013.png)

4.验证
访问 [http://ip.cn](http://ip.cn) 验证是否连接成功。当页面中显示的ip地址与你VPN服务器地址相同时，即证明连接成功，实现科学上网。
![](http://blog-10057309.cos.myqcloud.com/0014.png)
