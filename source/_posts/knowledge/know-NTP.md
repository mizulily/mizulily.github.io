---
title: NTP网络时间协议
date: 2018-04-28 16:55:35
tags:
  - network basis
  - protocol
categories: knowledge
hide: true
---

**NTP(Network Time Protocol，网络时间协议)**是用来同步网络中各个计算机时间的协议，属于应用层协议，采用UDP报文传输，使用UDP端口号为123。连接到互联网上的主机通过NTP与UTC(Universal Time Coordinate，世界协调时)同步，UTC由原子钟报时。
计算机主机一般同多个时钟服务器连接，利用统计学的算法过滤来自不同服务器的时间，选择最佳的路径和来源以便校正主机时间。

Reference [百度百科](https://baike.baidu.com/item/nTP)
More [sms的博客](http://blog.163.com/yzc_5001/blog/static/2061963420121283050787/)