---
title: 云服务的三种形式
date: 2019-08-05 10:45:47
tags:
  - cloud
  - service
categories: knowledge
hide: true
end: true
---

云服务是一个统称，可以分成三大类：

1.  **基础设施服务(IaaS, Infrastructure-as-a-service)**
2.  **平台服务(PaaS, Platform-as-a-service)**
3.  **软件服务(SaaS, Software-as-a-service)**

假如你是一个餐饮业者，打算做披萨生意，你可以从头到尾，自己生产披萨，但是这样比较麻烦，需要准备的东西多，因此你决定外包一部分工作，采用他人的服务。你有三个方案。

（1）方案一：IaaS
他人提供厨房、炉子、煤气，你使用这些基础设施，来烤你的披萨。

（2）方案二：PaaS
除了基础设施，他人还提供披萨饼皮。你只要把自己的配料洒在饼皮上，让他帮你烤出来就行了。也就是说，你要做的就是设计披萨的味道（海鲜披萨或者鸡肉披萨），他人提供平台服务，让你把自己的设计实现。

（3）方案三：SaaS
他人直接做好了披萨，不用你的介入，到手的就是一个成品。你要做的就是把它卖出去，最多再包装一下，印上你自己的 Logo。

对应软件开发则是下面这张图：
![SoftwareDevel](know-cloudservice/bg2017072307.jpg)

SaaS是软件开发、管理、部署都交给第三方，不需要关心技术问题，可以拿来即用。普通用户接触到的互联网服务几乎都是SaaS。
PaaS提供软件部署平台，抽象掉了硬件和操作系统细节，可以无缝扩展，开发者只需关注自己的业务逻辑，不需要关注底层。
IaaS是云服务的最底层，提供一些基础资源，用户需要自己控制底层，实现基础设施的使用逻辑。

Reference [IaaS，PaaS，SaaS 的区别](http://www.ruanyifeng.com/blog/2017/07/iaas-paas-saas.html)