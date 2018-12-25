---
title: 将Ghost系统还原到虚拟机
date: 2018-10-19 11:05:28
tags:
  - virtual machine
  - VMWare
  - ghost
  - LAOMAOTAO
categories: tip
hide: true
end: true
---

1. 创建空虚拟机
安装来源界面，选择“稍后安装操作系统”，并选择需要还原的系统和版本，选择合适的内存、硬盘后完成创建。

2. 用老毛桃进入WinPE
打开老毛桃，左侧选择ISO模式，点击“生成ISO”会在D盘创建名为“老毛桃ISO”的文件夹。在刚创建的虚拟机设置里面，“硬件”标签中的光驱选择“使用ISO映像文件”并选择“老毛桃ISO”文件夹下的LMT.iso文件，“选项”标签中的高级，固件类型选择“BIOS”。
启动虚拟机后引导进入WinPE，选择一项进入，建议选择新机器的WinPE，启动成功后会进入老毛桃的WinPE，包含多个系统维护工具。

3. 用老毛桃还原Ghost
首先进行硬盘分区，打开DiskGenius分区工具，点击快速分区，选择MBR或者GUID分区表类型，并完成分区。
点击“老毛桃PE装机工具”，选择“还原分区”，选择需要还原的Ghost文件和安装的分区，点击确定进行还原。

4. 用老毛桃修复引导记录
还原完成后重启出现了“The boot configuration data for your pc is missing or contain errors”报错，点击启动“修复引导工具”并选择还原后的系统分区。
注意，若选用GUID分区，需要创建ESP分区并将引导放入ESP分区，并在虚拟机中设置UEFI启动。
修复完成后重启就可以正常启动啦！