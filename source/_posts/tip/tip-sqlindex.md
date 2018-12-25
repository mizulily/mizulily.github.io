---
title: 查询SQL Server表的索引
date: 2018-10-08 16:45:20
tags:
  - SQL Server
categories: tip
hide: true
end: true
---

1.执行存储过程

    EXEC sp_helpindex 表名

2.或者获取表的所有信息，即执行存储过程

    EXEC sp_help 表名

在输出结果中包含'index_name'和'index_keys'项

3.将表的设计模式打开，查看表属性