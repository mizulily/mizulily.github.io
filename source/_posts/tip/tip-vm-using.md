---
title: 解除虚拟机占用
date: 2018-12-10 15:35:14
tags:
  - virtual machine
  - VMWare
categories: tip
hide: true
end: true
---

打开虚拟机时提示“该虚拟机似乎正在使用中。如果该虚拟机未在使用，请按‘获取所有权(T)’按钮获取它的所有权。否则，请按‘取消(C)’按钮以防损坏”。

这是由于虚拟机未正常关闭引起的，打开存放该虚拟机的目录，删除.lck文件夹即可。