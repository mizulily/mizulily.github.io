---
title: OPC数据访问
date: 2018-07-30 08:21:16
tags:
  - OPC
categories: knowledge
hide: true
---

OPC采用client/server模式，主要包括三部分：服务器(server)、组(group)和数据项(item)。**服务器对象**保存服务器和服务器作为OPC组对象容器的所有信息。**组对象**包括公共组和私有组两种，公共组由多个客户共享，私有组只隶属于一个OPC客户。OPC客户可以通过组对象来读写数据并设定OPC服务器应提供的数据更新速率。**数据项对象**是读写数据的最小逻辑单位，每个数据项包括值(value)、品质(quality)、和时间戳(timestamp)三个变量。

OPC数据访问主要有同步访问和异步访问两种方式。**同步数据访问**时，OPC服务器按照要求返回数据之前，OPC应用程序一直处于等待状态，在动作完成前不能执行任何应用程序侧的处理。**异步数据访问**时，对OPC服务器提出数据访问要求后立即返回到OPC应用程序中，服务器完成后通知OPC应用程序，从而得到数据访问结果。

C#中调用OPC主要使用自动化接口OPCAutomation.dll库。
1. SyncR


----To Be Continued----
