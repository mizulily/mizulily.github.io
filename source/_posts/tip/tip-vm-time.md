---
title: 修改虚拟机启动时间
date: 2018-04-28 14:51:56
tags:
  - virtual machine
  - VMWare
categories: tip
hide: true
end: true
---

由于软件license的时间限制，需要用过去的时间启动虚拟机。
1. 修改主机时间。启动虚拟机后系统时间即当前主机时间。但在主机中打开Chrome浏览器会报错，提示时钟慢了，无法建立私密连接。
2. 修改虚拟机启动时间。用文本编辑器打开虚拟机.vmx文件，寻找以下设置项并关闭同步，设置虚拟机启动时间，保存后启动虚拟机。
```
tools.syncTime = "FALSE"  
time.synchronize.continue = "FALSE"  
time.synchronize.restore = "FALSE"  
time.synchronize.resume.disk = "FALSE"  
time.synchronize.shrink = "FALSE"  
time.synchronize.tools.startup = "FALSE" 
rtc.startTime = 1462003200
```
注：rtc.startTime是从1970年1月1日0时0分0秒（Unix时间）到系统启动时间间隔的时间，单位是秒，可以到[计算时间的网站](http://www.onlineconversion.com/unix_time.htm)上换算得到希望虚拟机的启动时间。

Reference [VMware12.0 设定虚拟机时间](https://blog.csdn.net/sagafive/article/details/53031740)