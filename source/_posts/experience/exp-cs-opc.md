---
title: ___C#编写OPC程序
date: 2018-04-28 09:23:59
tags:
  - OPC
  - C#
categories: experience
toc: true
---

[OPC基金会官网](https://opcfoundation.org/)真是弱爆了。

### 1. 配置OPCDAAuto.dll

OPC的自动化接口即OPCDAAuto.dll
1)下载文件OPCDAAuto.dll，版本2.2.5.30
2)放到System32文件夹下，用管理员身份打开cmd
3)输入regsvr32 opcdaauto.dll后提示成功
4)打开Visual Studio在项目中打开相应项目，对解决方案右键-添加-引用，浏览选择opcdaaturo.dll
5)依赖项中出现COM-Interop.OPCAutomation，在C#程序开头using OPCAutomation；不再显示红色波浪线错误，即配置成功。


Reference [u012252959的博客](https://blog.csdn.net/u012252959/article/details/49699559)


----To Be Continued----