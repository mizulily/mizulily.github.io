---
title: windows三个内置账户
date: 2019-04-17 09:39:01
tags:
  - Windows
  - system management
hide: true
end: true
---

Windows中处于安全性考虑有三个由操作系统创建的、较为特别的内置账户或组，主要作为系统服务或进程运行账户，与通常的用户账户没有任何关联，分别为Local System、Network Service和Local Service。

1. Local System账户，全名为NT AUTHORITY\SYSTEM，预设拥有本机所有权限，当它访问网络资源时是作为计算机的域账户使用的。

2. Network Service账户，全名为NT AUTHORITY\NETWORK SERVICE，预设拥有本机部分权限，它能以计算机的名义访问网络资源，并根据实际环境把访问凭据提交给远程计算机。

3. Local Service账户，全名为NT AUTHORITY\LOCAL SERVICE，预设拥有本机最小权限，并在网络凭证中具有匿名身份