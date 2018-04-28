---
title: localhost
date: 2018-04-26 16:51:36
tags: 
  - network basis
categories: knowledge
---

localhost是一个域名，在windows中该域名是由/etc/hosts文件预定义的，默认对于ipv4指向127.0.0.1，对于ipv6指向::1，可对hosts文件进行修改配置为任意的IP地址，但可能导致只认127.0.0.1的软件失效。

127.0.0.1/8整个都是环回(loopback)地址，用来测试本机的TCP/IP协议栈，以及本机中各个应用之间的网络交互，也称虚拟网卡。Windows中看不到这个接口，Linux中这个接口叫lo，可通过ifconfig查看。

本机IP地址一般指绑定在物理或虚拟接口上的IP地址，供其他设备访问。



Reference [知乎](https://www.zhihu.com/question/23940717)