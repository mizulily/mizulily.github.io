---
title: 编程命名规范
date: 2019-08-20 11:03:51
tags:
  - programming
  - notation
hide: true
end: true
---

1. **匈牙利命名法**(Hungarian Notation)
匈牙利命名法是微软内部一个匈牙利人发起使用的，随后逐渐在微软内部流行起来并推广给了全世界的Windows开发人员。
其主要思想是：在变量和函数名中加入前缀，以增进人们对程序的理解。
常用前缀一览：
    b   ->  boolean
    ch  ->  char
    f   ->  float/flag
    db  ->  double
    dw  ->  double word
    i   ->  int/index
    c   ->  count of items
    p   ->  pointer
    a   ->  array
    s   ->  string
    st  ->  structure
    fn  ->  function
    h   ->  handle
    m   ->  member
    g   ->  global
    l   ->  local

2. **驼峰命名法**(Camel-case Notation)
小驼峰命名法第一个单词首字母小写，其他单词首字母大写。
大驼峰命名法每个单词都大写，也称**帕斯卡命名法**(Pascal Notation / Upper Camel-case)。

3. **下划线命名法**(Under-score-case Notation)
每个单词都用下划线分割，这种方法在C语言和UNIX环境中非常普遍。