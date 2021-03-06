---
title: 《工业控制网络》笔记
date: 2018-05-25 12:41:39
categories: note
tags:
  - industrial control
  - communication basis
toc: true
---

**《工业控制网络》 主编：王振力 人民邮电出版社 2012年1月第1版 TP273 ISBN: 978-7-115-30136-9 **
本书介绍了工业控制网络的特点、发展历程、技术现状和发展趋势，重点介绍了Modbus、Profibus、CAN、DeviceNet及CANopen等现场总线技术，还介绍了EAP、Profinet、HSE、EtherNet/IP及Modbus-TCP等工业以太网技术，并结合台达工业自动化产品有针对性地安排了大量工业控制网络应用案例和实验内容。
<!-- more -->

<!-- toc -->

## 第一章 绪论 ##

### 1.1 工业自动控制系统历史 ###
20世纪50年代前 - **模拟仪表控制系统(Analog Control System, ACS)**：精度低、干扰大
20世纪60年代起 - **直接数字控制系统(Direct Digital Control, DDC)**：中心计算机可靠性差
20世纪70年代起 - **集散式控制系统(Distributed Control System, DCS)**：电缆多、互操作性差
20世纪90年代起 - **现场总线控制系统(Fieldbus Control System, FCS)**：成本低、通信可靠

### 1.2 工业控制网络特点 ###
工业控制网络是3C技术(Computer,Communication,Control)发展汇集成的结合点，是信息技术、数字化、智能化网络发展到现场的结果，是一类特殊的网络，与传统信息网络相比有如下特点：
1. 应用于工业现场，对环境要求高
2. 包含多种复杂、异构的节点，多为嵌入式CPU
3. 主要任务为传输工业数据、承担自动测控任务，实时性要求高

### 1.3 传统控制网络：现场总线 ###
现场总线技术源于欧洲，目前以欧美日地区最为发达，经过近20年的竞争和完善，目前较有生命力的有10多种，并仍处于激烈的市场竞争中。诞生于不同领域的总线技术往往对特定领域的适用性较好，如Profibus较适合工厂自动化、CAN适合汽车工业、FF适用于过程控制、LonWorks适用于楼宇自动化等。

### 1.4 现代控制网络：工业以太网 ###
工业以太网是在以太网技术和TCP/IP技术的基础上发展起来的一种工业控制网络。由于现场总线多种标准并存，异种网络通信困难，以太网进入工业自动化领域并快速发展。
以太网是在1972年发明的，并于1982年公布了以太网规范，IEEE802.3就是以这个技术规范为基础制定的。以太网技术具有成本低、通信速率和带宽高、兼容性好、软硬件资源丰富等诸多优点。
将工业以太网引入工业控制领域，主要有以下优点：
1. 采用TCP/IP国际标准，协议开放，互连和互操作性强
2. 可实现远程访问和诊断
3. 网络速度快，不同传输介质可以灵活组合
4. 指出冗余连接配置，数据可达性强
5. 成熟可靠的系统安全体系

同时工业以太网也存在实时性、可靠性、安全性、总线供电等问题。

### 1.6 工业控制网络发展趋势 ###
纵观当今工业控制网络的发展趋势和市场需求，未来工业控制网络发展方向包括：
1. 提高通信的实时性：操作系统和交换技术的实时性
2. 提高通信的可靠性：虚拟自动化网络
3. 提高通信的安全性：黑通道机制和安全完整性等级SIL
4. 多现场总线集成：{% post_link introduction/intro-opc %}
5. 无线网络技术应用：工业WLAN协议(IEEE802.11n)、蓝牙(IEEE 802.15.1)和ZigBee(IEEE 802.15.4)

## 第二章 数据通信与网络基础 ##

### 2.1 数据通信系统概述 ###
**数据通信系统**一般由信息源与信宿、发送与接收设备和传输介质几部分组成。**信源和信宿**是信息的产生者和使用者；**发送设备**将信息源产生的消息信号经过编码变换为便于传送的信号形式并送往传输介质；**接收设备**的任务是从带有干扰的信号中正确恢复出原始信息，解除多路复用等；**传输介质**指发送设备到接收设备之间的信号传递所经的媒介。
![comm_system](note-industrial/comm_model.JPG)

衡量数据通信系统性能的指标包括：
1. **误码率**，二进制数据被错误传输的概率
2. **传输速率**，单位时间内传送二进制数据的位数
3. **协议效率**，所传数据包中有效二进制数据位数与所传输的总位数之比

总体来说通信协议越简单，协议效率越好，但往往无法满足可靠性要求。

### 2.2 数据编码技术 ###
在信息源中将原始的信息转换成代码表示的数据过程称为**信源编码**，如BCD码、ASCII码、汉字区位码等。**信道编码**是将信源编码变换到某种适合于信道传输的信号形式。

数字信号可以通过调制和解调在模拟通信信道中传输，根据所控制的载波参数不同分为幅移键控法(ASK)、频移键控法(FSK)和相移键控法(PSK)。

数字信号编码方法很多，信号电平有正负两种极性的称为**双极性码**，只有一种极性称为**单极性码**；信号电平在每位二进制数传输时间内都返回零电平的称为**归零码**，与之对应信号电平保持的称为**不归零码**，最普遍采用的信号编码方法为单极性不归零码。





### 2.4 工业控制网络的节点 ###

**可编程控制器**，工业控制网络中不可或缺的设备，大多支持多种现场总线和工业以太网。
**传感器**将检测感受到的信号按一定规律变换成标准信号，**变送器**将传感器输出信号转换为可以被控制器接受的标准信号。仪器仪表公司为了适应工业控制网络的需求，设计了智能型传感器与变送器，通过嵌入式微处理器实现现场总线和工业以太网的通信接口。
**执行器**是过程控制系统中对被控对象施加控制作用的仪表，**驱动器**是运动控制系统中驱动各种电动机的装置。工业控制中使用最多的执行器和驱动器包括电动调节阀、变频器和伺服驱动器。
**人机界面**泛指控制系统与操作人员交换信息的设备。
**网络互连设备**是工业控制网络互联互通的关键，主要包括网卡（网络适配器）、中继器、集线器、网桥、交换机、路由器和网关。

### 通信传输介质 ###




----To Be Continued----