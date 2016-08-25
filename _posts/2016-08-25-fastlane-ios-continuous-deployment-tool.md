---
id: 224
title: fastlane - iOS集成部署神器
author: 李攀
layout: post
permalink: /2016/08/25/fastlane-ios-continuous-deployment-tool/
categories:
  - 开发
---
先说一个严肃的问题，我们为什么需要集成部署（Continuous Deployment）？

- 为app提交、上传截图、发布等节省大把大把的时间（cry
- iOS大哥蜜月旅行去了，iOS小哥要修复线上紧急bug并发布客户端版本，怎么破？不要在发布版本这件事情上仅依赖一个人
- 通过高频的小版本迭代来提高版本的质量

然后，我们来看一下实际工作中的iOS开发、打包和发布流程：

0. 开发前，需要登录苹果开发者后台创建App、Provisioning Profiles、certificates等；
1. 使用Xcode开发，然后将上述相关文件和证书配置好；
2. 编译项目并自测；
3. Archive项目；
4. 上传包到iTunes后台；
5. 配置TestFlight，准备测试刚上传的版本；
6. 发布测试版本；
7. 测试发现问题，重回2；
8. 测试完成，在iTunes后台提交版本截图、描述等信息；
9. 提交App Store审核；

一直以来让iOS开发者头疼的问题就是上述10步繁琐的打包和发布流程，看似10步也不多，然而懂的人知道，这其中每一步都可能有坑，都可能都要花不少时间。然后，我们[团队](http://juhuiwan.cn)在做新项目的时候发现了一个神器，可以说是相见恨晚，这个神器就是fastlane，他几乎可以把上述流程全部自动化，而且还可以做的事情更多，想一下当初大把大把的时间都浪费在了这上面，现在终于可以解放的激动心情吧。

先介绍一下fastlane，[fastlane](https://fastlane.tools/)是一个完全[开源](https://github.com/fastlane/fastlane)的项目，现在被[Twitter](https://twitter.com/)收购，是[Fabric](https://www.fabric.io)的一部分，主要是提供自动化构建和发布的一系列的工具集合，他包括iOS和Android工具集，由于我们只在iOS上使用，所以这里仅介绍一下iOS相关的工具：

- [deliver](https://github.com/fastlane/fastlane/tree/master/deliver): 上传应用截图、metadata信息和ipa包到iTunes，提交审核
- [snapshot](https://github.com/fastlane/fastlane/tree/master/snapshot): 在所有分辨率的iOS设备上截图并上传iTunes
- [frameit](https://github.com/fastlane/fastlane/tree/master/frameit): 快速地把应用截图放入设备框里
- [pem](https://github.com/fastlane/fastlane/tree/master/pem): 自动生成推送使用到的的profiles
- [sigh](https://github.com/fastlane/fastlane/tree/master/sigh): 创建、更新、下载和修复provisioning profiles，支持App Store, Ad Hoc, Development和企业profiles，而且可以自动添加测试设备UDID
- [produce](https://github.com/fastlane/fastlane/tree/master/produce): 使用命令行在iTunes和Dev后台创建iOS app
- [cert](https://github.com/fastlane/fastlane/tree/master/cert): 自动化创建和维护你的iOS签名证书
- [pilot](https://github.com/fastlane/fastlane/tree/master/pilot): 管理TestFlight的测试版本和测试设备
- [boarding](https://github.com/fastlane/boarding): 自动创建一个表单来邀请参与TestFlight的用户
- [gym](https://github.com/fastlane/fastlane/tree/master/gym): 编译、打包iOS app，生成签名的ipa文件
- [match](https://github.com/fastlane/fastlane/tree/master/match): 通过git在团队中共享和同步你的证书和profiles，避免团队开发经常遇到的iOS证书不一致的蛋疼问题
- [scan](https://github.com/fastlane/fastlane/tree/master/scan): 跑测试用例

上述gym, sigh, match等几个工具可以说是极大提高效率的神器。

下图是一个简略fastlane工作流程：
![](https://fastlane.tools/assets/img/intro-fastlane-tree.png)

总之，fastlane帮你统一定义、运行、自动化你的app发布流程，并且可以和其他第三方工具如CocoaPods等很好的结合，也可以和其他第三方持续集成(Continuous Integration)工具如Jenkins等完美的结合，不说了，从现在就开始快回去拯救你团队成员的生命吧～
