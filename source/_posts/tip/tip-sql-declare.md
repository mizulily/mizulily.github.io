---
title: Transact-SQL中变量的作用范围
date: 2018-06-05 09:47:13
tags:
  - SQL Server
categories: tip
hide: true
---

与常见的高级语言不同，Transact-SQL中局部变量的作用域是所在的**批处理**，在IF语句内定义的变量在IF外仍可继续使用，而由于Transact-SQL是以GO语句来区分批处理的，在下一个GO之后无法继续使用。
具体示例见参考链接。

Reference [SQL中declare变量的作用域](http://www.cnblogs.com/breezeli/archive/2010/04/16/1713308.html)