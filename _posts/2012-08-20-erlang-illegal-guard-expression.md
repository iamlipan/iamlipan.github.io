---
id: 92
title: illegal guard expression
author: 李攀
layout: post
guid: http://www.aixixili.com/2012/08/20/90-autosave/
permalink: /2012/08/20/erlang-illegal-guard-expression/
duoshuo_thread_id:
  - 1401335266181906444
categories:
  - Erlang
---
今天遇到一个奇怪的问题：

<pre class="erlang">put(a, 1),
if
	get(a) =:= 1 -&gt;
		ok;
	true -&gt;
		bad
end.

* 2: illegal guard expression</pre>

查了一下官方关于Guard的文档：  
The set of valid guard expressions (sometimes called guard tests) is a subset of the set of valid Erlang expressions. The reason for restricting the set of valid expressions is that evaluation of a guard expression must be guaranteed to be free of side effects.

网上也有人问道：  
>  
> On Fri, Dec 2, 2011 at 10:30 AM, Barco You <> wrote:  
> Why does the following expression got &#8220;illegal guard expression&#8221; when compiling:  
> X = 0.5,  
> if  
> random:uniform() < X -> %error reported for this line  
> good;  
> true ->  
bad  
end.  
>  
> But if I change it to following expression, it&#8217;s ok:  
> X = 0.5,  
> Ran = random:uniform(),  
> if  
> Ran < X ->  
> good;  
> true ->  
> bad  
> end.  
Yes, and not only does this mean that only a limited set of functions are allowed as guard functions, random:uniform() \_does\_ have side effects, since it updates the seed in the process dictionary.

可见，erlang:get/1 also has side effect.
