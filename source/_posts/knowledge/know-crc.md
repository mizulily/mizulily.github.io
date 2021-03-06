---
title: CRC循环冗余校验码
date: 2018-05-14 09:30:53
tags:
  - communication basis
  - error-detecting code
categories: knowledge
hide: true
end: true
---

**循环码**(Cyclic Redundancy Check, CRC)是一种检错率高、编码效率高的检错码，通过除法运算来建立有效信息位和校验位之间的约定关系。
<!--more-->
CRC码由两部分组成，前部分是**信息码**，后部分是**校验码**，若CRC码总共长$n$位，信息码长$k$位，则称为**$(n,k)$码**，$r=n-k$即冗余位长度，也就是校验码长度。

基本概念：
- $n$位二进制码可以表示最高次幂为$n-1$的多项式。
- **按位除**（模2除）运算实际上就是在除的过程中做异或运算，同时不考虑进位，直到余数的位数小于除数时得到最终余数。在异或运算中模2减与模2加真值表完全相同。

对于一个给定的$(n,k)$码，可以证明存在最高次幂为$r$的**生成多项式**$G(x)$，满足
1. 最高位和最低位为1
2. 当被传送信息任何一位发生错误时，被生成多项式做模2除后使余数不为0
3. 不同位发生错误时使余数不同
4. 对余数继续做模2除应使余数循环

将这些条件反映为数学关系是复杂的，常用的对应不同码制的生成多项式$G(x)$详见[Wikipedia](https://en.wikipedia.org/wiki/Cyclic_redundancy_check)：
- CRC1:  $x^1+x^0$
- CRC4:  $x^4+x^1+x^0$
- CRC8:  $x^8+x^5+x^4+x^0$
- CRC12: $x^{12}+x^{11}+x^3+x^2+x^0$
- CRC16: $x^{16}+x^{15}+x^2+x^0$

具体**编码规则**如下。
1. 接收方和发送方约定发送组的信息位k和冗余位r个数，选定生成多项式$G(x)$满足上述条件
2. 发送方将原始数据左移$r$位得到$M(x)$，随后按位除生成多项式$G(x)$，得到余数$R(x)$，有$\frac{M(x)}{G(x)}=Q(x)...R(x)$
3. 发送方将$M(x)$与$R(x)$连接（等同于模2加或模2减）后一起发送
4. 接收方将收到的数据按位除生成多项式$G(x)$，若余数为$0$则传输正确，若余数不为$0$则传输错误，即$\frac{M(x)+R(x)}{G(x)}=\frac{M(x)-R(x)}{G(x)}=Q(x)...0$

CRC校验码可以检查出全部单个错、全部离散二位错、全部奇数个数、全部长度小等于$k$位的突发错，并以$1-(1/2)^{k-1}$概率检查出长度位$k+1$位的突发错。
