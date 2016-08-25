--- 
id: 224 
title: 适合创业团队的第三方服务和资源整理（2016 更新版） 
author: 李攀 
layout: post 
permalink: /2016/08/24/services-for-startup-2016-update/ 
categories: 
  - 创业 
--- 
较早之前写过一篇创业团队适合的第三方服务和资源的文章，最近翻出来看了一下，发现当时写得比较早和粗糙，只列出了我们用到的部分，而且还有不少当时根本没有用到，随着公司和团队的发展，后来这些工具和服务更新和迁移很多，现在回想起来，很多地方都可以补充一下。

[原文链接](http://lipan.me/2015/05/25/services-for-startup/){:target="_blank"}

## 办公和协同

#### 邮箱 - [腾讯企业邮箱](http://exmail.qq.com/)
>邮箱这个老掉牙的工具，查找、沉淀、协作、效率等几乎都无法满足移动互联网公司的需求，我们现在仅用它来注册各种其他服务和印在名片上占位。但是，邮箱还是得有。

**update: 和一些外部团队的沟通，很多时候除了邮件也别无选择。**

#### 项目协作 - [Teambition](https://www.teambition.com/)
>我们不用邮箱，所有团队协作相关的东西都在这里，包括项目管理、任务(bug)、文档、日程、讨论等，TB能满足我们所有的需求，极大提高了我们的沟通协作效率。

**update：内部协作选择一款适合自己团队的工具可以大大提高生产力和沟通效率。Teambition一直保持着更新，我也给他们提了不少bug，没有一个团队协作的工具可以完美地满足所有团队，我也没有横向对比过其他工具，当然，Trello、Tower据说也很不错。**

#### 文档协同 - [Google Docs](https://docs.google.com/)
>当然，前提你得保证公司是无墙，Google Docs对于多人协同编辑和共享文档是最好的，由于门槛比较高，目前还没有第二家公司把这块做好。

**update: 貌似现在有一家叫[一起写](https://yiqixie.com/)的，收费！其实协同的需求并不是那么强烈。**

#### 招聘 - [拉钩](http://www.lagou.com/)
>拉钩是我们招聘效率和成功率最高的招聘渠道。

**update: 后面又用了[猎聘](https://www.liepin.com/)和[BOSS直聘](https://www.bosszhipin.com)**

## 云服务

#### 云主机 - [阿里云](http://www.aliyun.com/) | [UCloud](http://www.ucloud.cn/)
>国内几个大厂都大同小异，阿里云做得最早，UCloud专注游戏。

**update：由于我们是险峰的portfolio，有幸成了[AWS](http://www.amazonaws.cn/)在国内的早期用户，AWS的技术和服务远甩国内其他家好几条街，阿里云一直在抄袭AWS，AWS把“弹性计算”诠释到了极致。**

#### 云存储 - [七牛](http://www.qiniu.com/) | [又拍云](https://www.upyun.com/)
>云存储聚会玩目前用得不多。

**update：我们游戏上传和下载服务用了UPYUN，还算稳定，速度也还不错，价格也是国内最便宜的。**

#### DNS管理 - [DNSPOD](https://www.dnspod.cn/)
>稳定，用户体验好，操作简单，方便所有域名在一起统一管理。

**update：其实DNSPOD也越来越坑了，很多国外域名解析非常慢，而且一直在推付费服务，但是也一直没换。**


## 第三方SDK

#### 统计分析 - [友盟](http://www.umeng.com/analytics/) | [腾讯云分析](http://mta.qq.com/)
>各平台都大同小异，集成成本低，SDK不大，初期可以多接几个平台做一下数据对比，后期还是得自己做。

**update：后来还接了[TalkingData](https://www.talkingdata.com/)和[Fabric](https://www.fabric.io/)，Fabric最早是做崩溃统计的，后来被twitter收购了，他们家把体验做到了极致，SDK集成步骤和后台体验酷炫到爆，而且后来也增加了应用统计，可以看到实时在线数量等，非常不错！**


#### 社会化分享SDK - [友盟](http://www.umeng.com/component_social/) | [ShareSDK](http://www.mob.com/)
>聚会玩只用了友盟。

**update：还是自己实现吧，不就微博、微信、QQ三家么？**


#### 用户反馈 - [友盟](http://www.umeng.com/component_feedback/)
>能通过反馈渠道搜集到非常多的用户反馈，对产品迭代帮助很大。

**update：友盟卖给阿里后，变化太大了，用户反馈改成了阿里百川，集成SDK把阿里旺旺都打进去了，呵呵，反馈功能不复杂，还是自己实现吧！**


#### 推送 - [信鸽](http://xg.qq.com/)
>推送有很多，没做过比较，一直用信鸽，比较稳定。

**update：我们后来用了[LeanCloud](https://leancloud.cn/)接口自己实现**


#### 问卷调查 - [金数据](https://jinshuju.net/)
>非常完善的表单系统，几乎能满足你所有关于报名、投票、调查的需求。

**update：无**

#### 支付 - [ping++](https://pingxx.com/)
>目前聚会玩还没涉及到支付。

**update：谁是卧底OL项目使用了ping++的支付SDK。**

#### 短信验证 - [Mob.com](http://mob.com/)
>认证后每天有1w条免费验证额度，还是挺诱人的。

**update：额度确实诱人，但是必须接客户端的SDK才能享受，如果只使用服务端RESTful接口的话，是要收费的，那就不如用[LeanCloud](https://leancloud.cn/)了。**


#### IM服务 - [环信](http://www.easemob.com/)
>暂时没用到。

**update：可以用[LeanCloud](https://leancloud.cn/)接口自己实现。**


## 代码管理

#### Git托管平台 - [Git@OSC](https://git.oschina.net/)
>之前代码托管搭在自己的阿里云服务器上，主要是带宽问题，人多了clone代码非常慢，oschina的托管平台解决了这个问题，除了偶尔短暂抽疯以外，其他还好。要求高的话用内网服务器+GitLab自己搭吧。

**update：还是搭在内网靠谱，速度也快，我们从[GitLab](https://about.gitlab.com/)折腾到[GOGS](https://gogs.io/)，GOGS速度简直飞起来，Go还是远甩Ruby啊。。😢**


#### Code Review工具 - [Phabricator](http://phabricator.org/)
>聚会玩也用，Facebook也在用。

**update：最后，我们通过[Slack](https://slack.com/)的hook结合[GOGS](https://gogs.io/)的推送来做code review，review每一次提交的diff，很实用！**

## 持续集成（新）

#### 持续集成一条龙服务 － [Fastlane](https://fastlane.tools/)
>之前没介绍过，这个简直就是神器，从编译、打包、到上传、推送，整个一条龙都可以通过命令行来实现，极大解放了生产力，团队中可以拿一个人专门来做这块的工作，可以为整个团队减小非常大的工作量。后面专门写篇文章来介绍这个神器。

#### 自动编译 - [Jenkins](https://jenkins.io/)
>之前也没介绍，所有的编译工作都交給Jenkins去做吧，和Fastlane结合使用效果更好。


## 测试

#### Android内测 - [FIR](http://fir.im/)
>做内测非常方便，特别是Android，打包好apk扔上去，扫二维码直接下载。

**update：无**

#### iOS内测 - [TestFlight](https://developer.apple.com/testflight/)
>被苹果收购后，成了iOS最好的内测工具。

**update：TestFlight结合[Fastlane](https://fastlane.tools/)非常完美**

#### APP邀请码 - [inCode](http://incode.fir.im/)
>FIR团队做的，有需求的不用再造轮子了。

**update：无**

#### 云测试 - [Testin](http://www.testin.cn/)
>国内最早最全最专业的云测试平台。

**update：无**

## 产品

#### 交互原型 - [axure](http://www.axure.com/) | [墨刀](https://modao.io/)

>好用的两款Mockup工具。

**update：后来产品开始使用[Sketch](https://www.sketchapp.com/)来做原型和布局，从产品到设计再到开发，使用同一个文件，减少沟通成本和UI标注的成本。**

## 备案

#### [阿里云代备案系统](http://beian.aliyun.com/)
>一站式备案，统一管理。

**update：无**

## 商标版权

#### [知果果](http://www.zhiguoguo.com/)

>免费还不够吗？之前找的传统代理，价格高，服务差。

**update：无**

## 数据分析平台（新）

#### ASO - [CQASO](http://www.cqaso.com/) | [ASOU](http://www.asou.com/)

>看榜单，优化关键词，对比竞品数据等，产品和运营一定需要天天看这些东西。

## 移动广告平台（新）

#### [Google Admob](https://www.google.com/admob/) | [豌豆荚](http://developer.wandoujia.com/adnetwork/dev-docs/) | [广点通](http://e.qq.com/dev/)

>Google是以美元结算，在iOS上效果比较好，后两家刚开始都对开发者有补贴，后来好像没了，豌豆荚只有Android平台，广点通Android和iOS都有。
