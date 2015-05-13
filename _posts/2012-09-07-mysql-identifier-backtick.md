---
id: 134
title: MySQL识别符，反勾号的问题
author: 李攀
layout: post
guid: http://www.aixixili.com/?p=134
permalink: /2012/09/07/mysql-identifier-backtick/
duoshuo_thread_id:
  - 1401335266181906446
categories:
  - MySQL
  - 工作
---
数据库、表、索引、列和别名是识别符。

识别符可以引起来也可以不引起来。如果识别符是一个保留字或包含特殊字符，无论何时使用，必须将它引起来。

识别符的引用符是反勾号(‘\`’)。

案例：

当前使用数据库db1，现在要查询数据库db2的表table1时，如果sql语句中的表名用反勾号\`db1.table1\`，这时数据库会在前面添加当前使用的数据库db1，使其变成\`db1.db2.table1\`，这时的sql语句显然不对，运行也会报错Table &#8216;db1.db2.table1&#8242; doesn&#8217;t exist。

解决方法：  
1. \`db1.table1\` &#8212;-> \`db1\`.\`table1\`；MySQL官方文档中有解释：如果多部分名的组件需要引用，应分别将它们引起来而不要将整个名引起来。例如，\`my-tables\`.\`my-column\` 有效，而\`my-tables.my-column\`无效。  
2. \`db1.table1\` &#8212;-> db1.table1；即当表名不含保留字和特殊字符时，不使用反勾号，这样MySQL不会在前面画蛇添足。
