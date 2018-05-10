---
title: 《数据库原理与应用》笔记
date: 2018-05-10 11:31:31
tags:
  - databse
  - sql server
categories: note
toc: true
---

## 第十章 存储过程与触发器

**存储过程**是由一系列Transact-SQL语句构成的程序，经编译后存储在数据库中，可以通过名称直接调用。存储过程还可以接受参数，提高存储过程的灵活性。在SQL Server中，存储过程的类型主要有：用户存储过程、扩展存储过程和系统存储过程。**用户存储过程**包括Transact-SQL存储过程和CLR存储过程；**扩展存储过程**可以加载外部DLL；**系统存储过程**用来实现数据库的管理活动，存放在master中，但其他数据库也可以调用。常用系统存储过程和分类见书P301。

创建和修改存储过程的语法：

    {CREATE|ALTER} PROC[EDURE] 存储过程(组)名[;序号]
    [{@参数名 数据类型} [=默认值] [OUTPUT]] [,... n]
    [WITH {RECOMPILE|ENCRYPTION|RECOMPILE,ENCRYPTION}]
    [FOR REPLICATION]
    AS {sql语句 [,... n]} 

删除存储过程的语法：

    DROP PROC[EDURE] 存储过程(组)名

执行存储过程的语法：

    EXEC[UTE] 存储过程(组)名[;序号]
    [[@参数名=]参数值|@参数名 [OUTPUT]|[DEFAULT]] [,... n]
    [WITH RECOMPILE]

**触发器**是一种特殊的存储过程，可以看作是表定义的一部分，用于对表进行完整性约束。在SQL Server中，触发器的类型主要有：DML触发器、DDL触发器和登录触发器。

当数据库中发生数据操纵语言(DML)事件时将调用**DML触发器**。按照触发操作的不同可以分为INSERT触发器、UPDATE触发器和DELETE触发器，SQL Server为每个语句创建deleted表或（和）inserted表，表结构与定义触发器的表结构相同，触发器执行完成后自动删除。按照触发时间的不同可以分为AFTER(FOR)触发器和INSTEAD OF触发器。
当数据库中发生数据定义语言(DLL)事件时将调用**DLL触发器**，主要用于任务管理。DLL事件主要包括CREATE/ALTER/DROP/GRANT/DENY/REVOKE等语句操作。
LOGON事件激发**登录触发器**，将在登录身份验证阶段完成之后用户会话建立之前触发。

创建和修改DML触发器的语法：

    {CREATE|ALTER} TRIGGER [模式名.]触发器名
    ON {表名|视图名}
    [WITH DML触发器选项 [,... n]]
    {FOR|AFTER|INSTEAD OF}
    {[INSERT][,][UPDATE][,][DELETE]}
    AS {sql语句 [,... n]}

删除DML触发器的语法：

    DROP TRIGGER 触发器名 [,... n]

创建和修改DLL触发器发的语法：

    {CREATE|ALTER} TRIGGER 触发器名
    ON {DATABASE|ALL SERVER}
    [WITH DLL触发器选项 [,... n]]
    {FOR|AFTER} {触发事件名称|触发事件分组名称} [,... n]
    AS {sql语句 [,... n]}
其中常见的数据库作用域的DLL语句和服务器作用域的DLL语句见P315。

删除DLL触发器的语法：

    DROP TRIGGER 触发器名 [,... n]
    ON {DATABASE|ALL SERVER}

启用和禁用触发器的语法：

    {ENABLE|DISABLE} TRIGGER {[模式名.]触发器名 [,... n]|ALL}
    ON {表名|视图名|DATABASE|ALL SERVER}