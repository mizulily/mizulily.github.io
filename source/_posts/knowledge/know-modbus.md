---
title: Modbus通信协议
date: 2018-05-03 15:30:26
tags:
  - industrial network
  - protocol
categories: knowledge
---

**Modbus通信协议**是全球第一个用于工业现场的总线协议，支持RS-232、RS-422、RS-485和以太网设备等，属于应用层协议。
**Modbus网络**是一个工业通信系统，包括硬件、软件及协议，用于各种数据采集和过程监控。Modbus网络只有一个主机，所有通信由它发出，至多支持247个远程从属控制器，实际支持从机数由通信设备决定。主设备可单独和从设备通信，从设备返回一消息作为回应；也能以广播方式和所有从设备通信，从设备不作任何回应。
Modbus最初使用串行链路，分为Modbus-ASCII(美国信息交换码)和Modbus-RTU(远程终端设备)两种传输模式，其中RTU传输效率更高。随着网络发展推出了针对以太网通信的Modbus-TCP标准，



Reference [百度百科](https://baike.baidu.com/item/Modbus%E9%80%9A%E8%AE%AF%E5%8D%8F%E8%AE%AE)
More [老罗传奇的博客](http://www.cnblogs.com/luomingui/archive/2013/06/14/Modbus.html)[上海卓岚公司的网站](http://www.zlmcu.com/document/modbus_tcp_2_rtu.html)