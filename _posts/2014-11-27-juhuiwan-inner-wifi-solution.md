---
id: 246
title: 聚会玩内部WIFI解决方案
author: 李攀
layout: post
guid: http://www.aixixili.com/?p=246
permalink: /2014/11/27/juhuiwan-inner-wifi-solution/
categories:
  - 工作
---
很早之前就早网上看到过豌豆荚创业初期遇到的公司内部网络问题（http://www.36kr.com/p/207783.html），没想到聚会玩也没法避免。结合我们的实际情况，说一下我们的问题和解决方案。

聚会玩最初<5个人的时候，在一个民宅的客厅里面办公，当时客厅还算大，大伙儿吃喝起居办公都在客厅里面，一台TP-link的路由器也没有遇到任何问题，算是一个典型的单AP家庭式网络环境。  
慢慢的，聚会玩人多了，我们搬进了一个专门办公的民居，当时的人数不超过10人，我们听朋友的建议买了一个据说很牛逼的路由器，NetGear WNR2000v3，看着就很酷的样子，除了内部某台机器提交应用上传AppStore的时候会导致大家都断网以外，其他都没什么问题。  
聚会玩发展太好了，过了半年，这个民居坐不下了，我们搬到了一个三室一厅的商住两用套房里。这时我们的人数超过了10人，为了让大家不受上传AppStore时会断网的影响，我们将路由器省级到了Huawei WS880千兆路由器，千兆，一听就很牛逼。但随着人数慢慢增长（写这篇文章时我们是13人），又因为我们是移动互联网公司，加上测试机平均人手近3台移动网络设备，渐渐地，我们发现有些同学电脑时不时会掉线。开始，我们以为我们统一配备的电脑无线网卡出了问题，但是换新网卡后仍得不到解决，并且掉线的情况发生的频率越来越大，会随机在各种机器上出现。于是，我们认为我们被华为路由器坑了，一个网段理论上有255个ip地址，怎么连30几台设备就不行了呢？于是我们找到了华为的客服，客服GG是个工程师，毫不留情的说这个设备总共只能支持16台设备，我们已经连了30台，已经很幸运了！我擦，颠覆了偶的世界观，一台路由器只能连这么点设备，那些ip地址用来看的啊……不过这时我们可以解释为什么大家会断网，因为新的设备连接进来，把老设备挤下去了。客服告诉我们想连接新设备，可以打开Guest模式，这样可以多连16台设备。于是，我们的问题算是解决了。但是也明白了，一个AP能承受的连接数不是255，而是30个左右，也许能连接上更多，但是会出现掉线或者速度慢的情况。

为了分担WS880的的压力，我们尝试把之前的WNR2000v3也拿出来一起使用，WS880的5GHz和2.4GHz两个频段分别打开Guest，加上WNR2000v3也打开Guest，再加上电信的ChinaNet路由器，我们的网络数达到了7个，看着网络列表就觉得高大上。随后，问题马上来了，大家慢慢觉得网络特别慢，又出现了经常断线的情况，之前的问题貌似又出现了，why？

我们都知道常用的Wi-Fi频率有两个：2.4GHz和5GHz，先说2.4GHz，大多数 PC只支持2.4GHz，这是一个相对拥挤的信道，只能使用1、6、11三个非重叠信道才不会发生干扰。三个信道意味着在一个 AP信号覆盖的范围内，不能超过三个热点，否则就会发生干扰。现在我们正好有3个AP，而且我们使用的时auto信道，默认都是6，所以三个AP之间的干扰可想有多严重。于是，我们把三个AP的信道分别改成了1，6，11，这样相互之间就没有了干扰，另外，并不网络热点越多越好，热点之间也是有干扰的，于是我们关闭了WS880的Guest网络，仅保留了WNR2000v3的Guest，这样我们还剩5个网络，在不同的信道。最后，由于关掉了WS880的Guest网络，剩下的问题就是如何解决设备太多导致不断掉线的问题，我们是按照设备优先级来解决的。我们认为办公电脑的优先级是最高的，所以我们尽让电脑链接WS880，这个AP连的设备数是可控的，可以保证工作电脑不会掉线。然后我们强制让所有的移动设备连接WNR2000v3，由于在公司大家几乎都用电脑上网，移动设备对断网的敏感度不高，所以即使移动设备超过了WNR2000v3的最大连接数，也不会有太大的问题，因为大多数的移动设备是“休眠”的。此外，这样做可以很方便的做移动设备网络的带宽限制，保证工作电脑的带宽。

所以，通过多AP，信道分离，强制连接分流，我们做到了目前状态下的内部wifi的稳定。

另外，我们工作时用到了共享网盘，当几十个渠道包一打出来，大家都同时同步到本地时，我们的带宽几乎就全被吃掉了，导致上网速度特别慢。我们通过在内部AP上接外接USB移动硬盘的方式搭建了内网大文件贡献，所有的大文件都不再走外网流量，不占用公司带宽资源，大家的上网速度不会有影响，这个涉及带宽的解决方案了，下次有时间再写。