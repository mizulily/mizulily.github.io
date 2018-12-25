---
title: 强制停止Windows服务
date: 2018-07-24 12:41:59
tags:
  - Service
categories: tip
hide: true
end: true
---

状态为Starting或Stopping的服务无法在Service桌面应用或任务管理器的Service选项卡中启动或停止，可以通过命令行taskkill指令进行强制停止。

    taskkill /PID 任务管理器中的服务PID /F
