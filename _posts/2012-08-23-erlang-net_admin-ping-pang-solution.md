---
id: 122
title: Erlang本地通过net_adm:ping远程节点一直返回pang解决办法
author: 李攀
layout: post
guid: http://www.aixixili.com/2012/08/23/116-autosave/
permalink: /2012/08/23/erlang-net_admin-ping-pang-solution/
duoshuo_thread_id:
  - 1401335266181906445
categories:
  - Erlang
---
一直有个问题没解决，本地节点直接可以通过net_adm:ping相互连通，但是本地一直都无法通过此方式连接到远程的服务器上的节点。

yufeng有篇[文章][1]是说这个问题，我读了至少3遍，但都没解决的这个问题。

今天发现原来是远程服务器防火墙的问题，其实yufeng在上述文章中已经提到可能是此原因，之前没有认真分析，浪费了不少时间。

> 首先从原理上分析下!由于erlang节点间通讯是透过tcp来进行的，所以我们确保以下几点：  
> 1. 确保网络连接是通的，可以透过ping来查看。  
> 2. 确保网络连接上tcp是可以通的，可以透过netcat在二个节点所在的机器上分别开个服务器端和客户端进行验证。  
> 3. 确保端口是防火墙友好的。erlang的节点是登记在epmd服务上的，所以4369端口要能访问，其次节点的动态端口是可以访问的。
> 
> > epmd -names  
> > epmd: up and running on port 4369 with data:  
> > name xx at port 46627  
> > …
> 
> 同样可以用netcat来验证。  
> 4. erlang节点的cookie是一样的，可以透过setcookie来解决。

我的问题就出在3上。

于是乎：  
到/etc/sysconfig下修改iptables，增加  
-A RH-Firewall-1-INPUT -p tcp -m state &#8211;state NEW -m tcp &#8211;dport 4369 -j ACCEPT  
-A RH-Firewall-1-INPUT -p tcp -m state &#8211;state NEW -m tcp &#8211;dport 动态端口号 -j ACCEPT  
然后  
service iptables restart  
然后从本机net_adm:ping，于是看到了可爱的pong，从此可以用observer:start()监控远程服务器的状态了。

 [1]: http://blog.yufeng.info/archives/2169
