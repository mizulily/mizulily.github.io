---
title: 单方ping不通的防火墙设置
date: 2018-12-19 10:47:05
tags:
  - ping
  - firewall
categories: tip
hide: true
end: true
---

A与B在同一子网内，B可以ping通A，但A却ping不通B。关闭B防火墙后可以ping通。

原因：ICMP被B的防火墙禁止了
解决办法：防火墙->高级设置->入站规则，开启“文件与打印机共享（回显请求-ICMPv4-In）”
