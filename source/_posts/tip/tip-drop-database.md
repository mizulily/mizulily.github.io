---
title: 强制删除数据库
date: 2019-04-24 11:25:01
tags:
  - SQL Server
  - Database
categories: tip
hide: true
end: true
---

在SQL Server Management Studio中删除数据库时提示无法删除(Cannot drop database databasename because it is currently in use)。这是因为在操作数据库中出现了问题，如打开数据库连接后未正确关闭等。
解决方案是运行如下脚本：

    USE [master]
    GO
    ALTER DATABASE database_name
    SET SINGLE_USER WITH ROLLBACK IMMEDIATE --将数据库回滚到原始配置状态
    GO
    DROP DATABASE database_name--删除数据库
    GO


Reference [mx5721的博客](https://blog.csdn.net/mx5721/article/details/8057542)