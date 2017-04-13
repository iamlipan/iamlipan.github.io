---
title: Erlang Dialyzer在windows下配置和使用方法
author: 李攀
layout: post
---
1. 添加名为OTP_HOME和HOME的系统环境变量，值都为Erlang安装目录，如C:Program Fileserl5.9.1  
2. 生成PLT（耗时约20多分钟）  
在命令行输入以下命令（或放到.bat文件中）：  
dialyzer &#8211;build\_plt -r &#8220;%OTP\_HOME%/lib/erts-5.9.1/ebin&#8221;  
dialyzer &#8211;add\_to\_plt &#8211;plt &#8220;%OTP\_HOME%/.dialyzer\_plt&#8221; -c &#8220;%OTP_HOME%/lib/kernel-2.15.1/ebin&#8221;  
dialyzer &#8211;add\_to\_plt &#8211;plt &#8220;%OTP\_HOME%/.dialyzer\_plt&#8221; -c &#8220;%OTP_HOME%/lib/stdlib-1.18.1/ebin&#8221;  
dialyzer &#8211;add\_to\_plt &#8211;plt &#8220;%OTP\_HOME%/.dialyzer\_plt&#8221; -c &#8220;%OTP_HOME%/lib/mnesia-4.7/ebin&#8221;  
dialyzer &#8211;add\_to\_plt &#8211;plt &#8220;%OTP\_HOME%/.dialyzer\_plt&#8221; -c &#8220;%OTP_HOME%/lib/crypto-2.1/ebin&#8221;  
dialyzer &#8211;add\_to\_plt &#8211;plt &#8220;%OTP\_HOME%/.dialyzer\_plt&#8221; -c &#8220;%OTP_HOME%/lib/sasl-2.2.1/ebin&#8221;  
3. 上述步骤会在Erlang安装目录下生成.dialyzer_plt文件  
4. cd到项目根目录，在命令行执行dialyzer -r ebin
