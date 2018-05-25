---
title: FTTM中的软件Bug
date: 2018-05-25 12:42:56
tags:
  - FactoryTalk
  - Rockwell
  - Transaction Manager
categories: tip
hide: true
---

在使用FactoryTalk Transaction Manager过程中，有时会遇到双击配置Live Data Connector时整个程序没有响应的情况，排除可能的问题包括：
1. 两个Configuration中重名的Connector
2. 选择不存在的FactoryTalk View SE程序
3. 打开FactoryTalk View SE服务器和客户端的顺序
4. Kepserver OPC服务器安装
5. 硬盘剩余容量小

这些情况都不会造成软件崩溃。
在一次尝试中意外复现了该问题，证明如下操作会造成Live Data Connector无法配置：
对于一个未绑定FactoryTalk View SE程序的Live Data Connector，双击初次配置并选择程序的过程中**不可以**选择“Cancel取消”，**可以**任意选择一个程序后在导入标签的页面选择“Close关闭”，否则FactoryTalk Transaction Manager会立即崩溃，再次打开可以启动自身或其他Configuration中的服务，但无法更改任何Live Data Connector的配置。

软件版本：
Windows Server 2008 R2
FactoryTalk Service Platform 2.74.00 (CPR9 SR7.4)
FactoryTalk Transaction Manager 10.10.00