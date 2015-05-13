---
id: 71
title: 创建Erlang的Application
author: 李攀
layout: post
guid: http://www.aixixili.com/?p=71
permalink: /2012/05/23/create-erlang-application/
duoshuo_thread_id:
  - 1401335266181906440
categories:
  - Erlang
---
我们写完一组功能模块后（在erlang中，以module为单位），总是希望这一组模块，可以打包成一个应用，作为一个单独的整个，可以启动，停止，象mnesia一样。并可以在其它应用中引用。如何来做到这一点呢。每一个应用都是通过application:start系列函数来启动，application:stop可以停止一个应用。

一个应用需要一个.app文件来描述，主要描述它包括哪些文件，参数等。

如果在启动erlang的VM时就启动一个应用呢，实际上，我们是没有办法通过VM的参数来直接启动一个自定义应用，有些参数如：start_sasl可以启动一些内部的标准的build-in应用，但是我们可以给VM一个执行入口，这就象C语言或是java语言的main函数一样，VM启动时，执行这个程序的入口点，这样就可以在这个入口中执行启动应用的操作。

这个入口点通过参数-s 来指定。下面我们来看一个例子：

1.   erl  -s sd  
这个参数指定，VM启动后，调用sd:start()无参函数

2.   在sd:start()函数中，我们写如下代码：  
application:start(server).

上面这句话，启动一个server的应用，这里，VM就会在ebin目录中找到server.app这个文件，如果不到，报错，如果找到，则按这个文件中的指示，启动server应用。这一部分可以参看相关的文档，简单的，在中一搬有一个参数{mod,{mod\_name\_app,[]}} 这个参数指示，调用mod\_name\_app：start(_type,Argu)这个函数。
