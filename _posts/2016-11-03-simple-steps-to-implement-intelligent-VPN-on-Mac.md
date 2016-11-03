---
id: 224
title: 简单几步在Mac上实现智能VPN
author: 李攀
layout: post
permalink: 
categories:
  - 开发
---
VPN 是好用，挂上之后国外的网站是能访问了，但原来国内正常访问的网站立刻变得慢吞吞了，怎么破？这是个问题。如果连了 VPN 没做任何设置的话，会导致所有网络都是通过 VPN 访问，缺点有二：
1、VPN 的流量问题;
2、国内网站变慢吞吞的问题。

方法：
1、自行搭建 VPN 服务器或购买 VPN 提供商的服务(见上一篇)。
2、打开系统偏好设置—>网络，增加 VPN 设置，根据提示设置用户名密码等信息即可。
3、下载 chnroutes.py，
https://github.com/jimmyxu/chnroutes/blob/master/chnroutes.py
4、打开终端进入下载文件的目录，执行：python chnroutes.py -p mac，该目录下会生成两个文件「ip-up」和「ip-down」。
5、把这两个文件复制到 /etc/ppp 下
搞定！
