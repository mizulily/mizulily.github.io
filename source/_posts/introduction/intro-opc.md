---
title: OPC及OPC UA技术
date: 2018-05-17 15:11:12
tags:
  - OPC
categories: introduction
hide: true
---

OPC是一个工业标准，属于[OPC基金会](https://opcfoundation.org/)，现有会员已超过220家，包括世界上所有主要的自动化控制系统、仪器仪表及过程控制系统的公司。

经典OPC规范基于微软Windows系统提供的COM/DCOM技术，用于软件之间数据交换的规范。OPC规范定义了几种不同的，用于访问过程数据、报警信息以及历史数据的版本规范：
OPC实时数据访问规范（OPC DA）定义了包括数据值，更新时间与数据品质信息的相关标准。
OPC历史数据访问规范（OPC HDA）定义了查询、分析历史数据和含有时标的数据的方法。
OPC报警事件访问规范（OPC AE）定义了报警与时间类型的消息类信息，以及状态变化管理等相关标准。

基于COM/DCOM的技术有着不可根除的缺点，因此随着技术的进步，以及数据交换各方面需求的提高，OPC基金会在2008年发布了新的规范：OPC UA。

OPC UA规范不再是基于COM/DCOM技术，因此OPC UA不仅能在Windows平台上实现，更可以在Linux，以及其他的嵌入式平台中实现。与传统OPC规范相同，OPC UA 同样有着相同的设计目标：
1. 功能等价：所有的基于COM的OPC规范中的功能，都映射到了OPC UA中。
2. 多平台支持：支持从嵌入式的微控制器到基于云的分散式控制架构。
3. 安全：信息加密，互访认证以及安全监听功能。
4. 扩展性：不影响现有应用程序的情况下，就可以添加新的功能。
5. 丰富的信息建模：可定义复杂的信息，而不再是单一的数据。

相比于传统OPC，OPC UA具有以下特点：
一、功能方面，OPC UA不仅支持传统OPC的所有功能，更支持更多新的功能：1. 网络发现：自动查询本PC机中与当前网络中可用的OPC Server。2. 地址空间优化：所有的数据都可以分级结构定义，使得OPC Client不仅能够读取并利用简单数据，也能访问复杂的结构体。3. 互访认证：所有的读写数据/消息行为，都必须有访问许可。4. 数据订阅：针对OPCClient不同的配置与标准，提供数据/消息的监控，以及数值变化时的变化报告。5. 方案(Methods)功能：OPC UA中定义了通过在OPCServer中定义方案（Methods），来让OPC client执行特定的程序。
二、平台支持方面，由于不再基于COM/DCOM技术，OPC UA标准提供的更多的可支持的硬件或软件平台。硬件平台诸如传统的PC机、基于云的服务器、PLC、ARM等其他微处理器；而软件平台可支持微软的Windows、苹果公司的OSX、安卓，以及其他的基于Linux的分布式操作系统。
三、安全性方面，最大的变化是OPC UA可以通过任何单一端口（经管理员开放后）进行通信，这使得OPC通信不再会由于防火墙受到大量的限制

1、OPC UA在传输中可通过XML格式或者二进制格式来传输，并且可选择并兼容更多通用的IT通信协议，比如HTTPS。同时，在加密时，也能达到128或者256位的加密深度。在客户端与服务器的通信许可方面，OPC UA使用了OpenSSL许可证来规定哪些应用程序或系统可以使用OPC与另一端相连接。2、在建模方面，OPC UA将建模的架构由“数据建模”扩展为了“信息建模”。OPC UA规范中不仅仅提供了完整的面向对象的数据建模，同时也可定义复杂的多级结构体。数据类型或结构体都在配置文件（profiles）中定义，不仅可以定义已存在的传统OPC规范中的类型，还可以扩展加入其他的供应商或组织定义的新类型。

http://blog.sina.com.cn/s/blog_a68809ea0102vk1p.html

【1. OPC UA 规范组成】

 

OPC统一体系架构规范由十一部分组成。各部分规范概要介绍如下：

 
第一部分——概念
这部分规范描述了关于OPC UA 服务器和客户端的基本概念。

第二部分——安全模型
这部分规范描述了用于OPC UA客户端和OPC UA服务器之间安全交互的模型。

第三部分——地址空间模型
这部分规范描述了服务器地址空间的内容和结构。

第四部分——服务
这部分规范指定了OPC UA服务器提供的所有服务。

第五部分——信息模型
详细说明了为OPC UA服务器定义的标准数据类型和它们之间的关系。

第六部分——映射
这部分规范详细说明了OPC UA支持的传输映射和数据编码机制。

第七部分——协议
这部分规范详细说明了可用于OPC客户端和服务器的协议。这些协议提供了可用于一致性标准的服务和功能。服务器和客户端可依靠这些协议来进行测试。

第八部分——数据访问
详细说明了如何使用OPC UA进行数据访问。

第九部分——报警与事件
详细说明了使用OPC UA对报警与条件通道的支持。基本的系统包括对简单事件的支持；这部分规范拓展了对报警与事件的支持。

第十部分——程序
详细说明了OPC UA对程序访问的支持。

第十一部分——历史数据访问
详细说明了使用OPC UA对历史信息的访问。访问包括对历史数据和历史事件的访问。

【2. OPC UA 规范总貌】

2.1 介绍
    OPC统一体系结构是一个不依赖任何平台的标准，借助此标准各种各样的系统和设备能在不同的网络中以C/S的模式进行通信。OPC统一体系结构通过确认客户端和服务器的身份和自动抵御攻击来支持稳定的、安全的通信。OPC UA定义了一系列服务器所能提供的服务，特定的服务器需要向客户端详细说明它们所支持的服务。信息通过使用标准的和宿主程序定义的数据类型进行表达。服务器定义客户端可识别的对象模型。服务器可以提供查看实时数据和历史数据的接口，并且由报警和事件组件来通知客户端重要的变量或事件变化。OPC UA可以被映射到一种通信协议上并且数据可以以不同的形式进行编码来达到传输便捷和高效的目的。

2.2 设计目标

    OPC UA提供了一个一致的、完整的地址空间和服务模型。这就允许一个单一的OPC UA服务器把数据，报警与事件和历史信息统一到它的地址空间里，并且可以用一套统一的服务为它们向外提供接口。这些服务也包括一个统一的安全模型。

    对于地址空间中要被访问的对象，OPC UA也允许服务器给客户端提供类型定义。这使得标准信息模型可以被用来描述地址空间的内容。OPC UA允许数据以不同的格式暴露出来，包括二进制结构和XML文档。数据格式可能被OPC或其他标准组织和厂商定义。通过地址空间，客户端能向服务器查询描述了数据格式的元数据。在许多情况下，没有数据格式编程知识的客户也能够在运行时刻决定数据格式并能恰当的使用数据。

    OPC UA扩充了对节点间关联的支持而不是把节点限制在单一的层面上。这样就使得，一个OPC UA服务器能从不同的层面提供数据，来满足客户端有选择性查看数据的要求。这种灵活性，不仅融合了对类型定义的支持，而且使得OPC UA适用于更宽泛的领域。所以，OPC UA不仅致力于现场遥测的服务层面，而且在上层管理功能上也提供了更好的互用性。

    OPC UA的目标是源源不断地提供已公布的数据。所有OPC服务器的一个主要特色就是发布数据和事件通知。OPC UA为客户端提供的机制可以使其快速检测到传输过程中的错误，并从中恢复过来，而不用等到底层协议所设定的超时时间结束。

    OPC UA目标也要支持更广泛的服务器，从底层的PLC到企业服务器。从容量，性能，执行平台和功能上区分这些服务器。因此，OPC UA定义了一系列功能，不同的服务器可能只实现所有功能中的某些功能。为了推动互操作性，OPC UA定义了标准子集，与协议相关，以保证不同服务器的一致性。客户随后可以得到一个服务器的协议，然后依靠协议来和服务器进行交互。规范的第七部分详细说明了协议。

    把OPC UA规范划分成不同的部分是为了把核心设计从底层的运算处理和网络传输分离出来。这使得OPC UA在不改变基础设计的情况下，被运用到未来技术上称为可能。映射和数据编码被定义在规范的第六部分。这里也定义了两种数据编码形式：1、可扩展标记语言/文本形式；2、UA 二进制形式。另外，这部分规范给出了两种传输协议：1、TCP（传输控制协议）；2、运用于HTTP（超文本传输协议）之上的网络服务简单对象访问协议。

    由于客户端和服务器支持多种传输形式和编码形式，这使得最终用户可以在实施阶段来确定性能和网络服务兼容性之间的平衡点，而不是由OPC厂商在生产定义阶段确定其平衡点。

    OPC UA的设计对于基于微软COM技术的OPC客户端和服务器来说，是可移植的。可移植性在设计OPC UA的时候已经给予了考虑，以至于由OPC COM服务器（数据访问，历史数据访问和事件报警）暴露出来的数据可以通过OPC UA进行映射和暴露出来。生产厂商既可以直接遵循OPC UA标准移植他们的产品，也可以对先前的产品进行外部封装来达到从OPC COM到OPC UA的过渡。先前每种OPC规范都是定义自己的地址空间和相应服务。OPC UA用一套服务把先前的各种模型统一到一个单一的地址空间里。


2.3 统一的模型和服务
2.3.1 安全模型
2.3.1.1 概要

    OPC UA安全性主要考虑：客户端和服务器的合法性，用户的合法性，客户端和服务器之间通信的一致性和机密性，功能发布的真实性。OPC UA安全性不指定包含了多种必需安全机制的环境。安全模型规范是非常重要的，但是它可能在特定条件下由系统的设计者来制定，也可能由其他标准来指定。

    另外，OPC UA提供了一个安全模型，规范的第二部分给予了定义，安全方法可以针对给定设备进行选择和配置来满足其安全性需要。安全模型包括标准安全机制和参数。在某些情况下，用于交换安全参数的机制需要定义，但是运用这些参数的方法不用定义。框架也定义了所有UA服务器必须支持的最少安全功能子集，即使这个功能子集中的功能没有被用在所有设备中。规范的第七部分定义了安全性协议。

2.3.1.2 建立会话

    应用程序级的安全性依靠一个安全的通信通道，这个通信通道在应用程序会话过程中始终有效，并且保证所有被交换信息的完整性。这也就意味着用户在应用程序会话建立时进行一次认证就可以了，不需要第二次认证。规范的第四部分和第六部分定义了建立安全通道和应用程序会话的机制。

    当一个会话建立时，客户端和服务器应用程序协商构造一个安全通信通道并且交换表明客户端和服务器身份的软件认证书还要交换各自所能提供功能的信息。OPC基金会发布的软件认证书显示了OPC UA中应用程序需要实现的基本要求，而且OPC UA认证标准贯彻到了每个协议中。规范的第七部分详细说明了每个协议和认证书的细节。由其他组织发行的认证也可能在会话建立期间进行交换。

    会话建立之后，服务器会对用户身份进行鉴别，随后批准用户对服务器中对象访问的请求。诸如访问控制列表这样的授权机制，OPC UA规范没有给予详细说明。这些机制与特定的应用程序或系统有关。

2.3.1.3 审核

    在客户端和服务器审查日志可查的条件下，用户级安全性为安全审查记录提供支持。如果在服务器端检测到一个安全连接问题，与之关联的客户端将在其审查日志中添加相应条目。OPC UA也为服务器提供了产生审查事件通知的功能，审查事件通知可以向有能力处理和记录审查事件的客户端报告审查性的事件。OPC UA定义了标准审查参数，审查日志和审查事件通知都可以包含这些参数。规范的第五部分定义了这些参数的数据类型。并不是所有的服务器和客户端都提供所有的审查特性。规范第七部分的协议显示了所要支持的审查特性。

2.3.1.4 传输安全性

    OPC UA安全性弥补了大部分网络服务可选平台上底层结构安全性的不足。传输级别上的安全性可以用来加密并标记消息。加密和标记技术防止了信息的泄露，保证了消息的完整性。用于在OPC UA应用程序之间传递消息的底层通信技术提供了加密功能。规范的第七部分定义了用于给定协议上的加密和标记方法。

2.3.2 统一的地址空间模型

    OPC UA服务器为客户端提供的对象和相关信息都是与服务器的地址空间有关的。OPC UA地址空间是以一组用引用形式连接起来的节点来描绘它的内容的。

    OPC定义的属性描述了节点的原始特性。属性仅仅是一个服务器中拥有数值的元素。用来定义属性值的数据类型既可以是简单数据类型也可以是高级数据类型。

    依照地址空间中节点的用途和含义，把它们进行分类。节点类为OPC UA的地址空间定义了元数据。规范的第三部分定义了OPC UA节点类。

    节点基类定义了所有节点的公共属性。包括认证，分类和命名。每个节点类继承这些属性并可以另外定义自己的属性。

    为了提高客户端和服务器的互操作性，在对所有服务器进行最高级标准化的条件下，对OPC UA的地址空间进行分层组织。尽管地址空间中的节点经过分层后，是相对独立唯一的，但是节点之间可能存在引用关系。这就使得地址空间可以描绘出一个相关联的节点网络。规范的第三部分定义了地址空间模型。

    OPC UA服务器把地址空间以视点的形式划分成不同的子集，以此向客户端扩充自己的访问通道。3.3.3.3展示了地址空间视点的更多细节。

2.3.3 统一的对象模型
    OPC UA对象模型提供了一套一致的、完整的节点类来描述地址空间中的对象。模型中根据对象包含的变量，事件，方法以及和其他对象的关系来描绘对象。规范的第三部分详细介绍了对象模型。

    OPC UA对象模型允许服务器为对象提供类型定义和对象组件。类型定义可以被继承，也可以标准化或是由系统指定。对象类型可以由OPC基金会，其他权威组织，生产商或最终用户来定义。

    统一对象模型允许把数据访问，事件报警，和历史数据访问功能集成到一个单一的OPC UA服务器中。例如，OPC UA服务器可以把一个温度传感器描述成一个对象，它由温度值，报警参数和相应的报警上下限组成。

2.3.4 统一的服务
    OPC UA客户端和服务器之间的接口被定义成了一系列服务。这些服务又被组织划分成不同的组，每个组叫做服务子集。第四节对服务集进行了讨论，规范的第四部分详细说明了服务集。

    OPC UA服务向客户提供两种功能服务。首先，它们允许客户端向服务器发送请求并接受服务器的相应消息。而且，它们也允许客户端向服务器订阅通知。服务器用通知来发布某些事件的发生，如报警，数据值的改变，事件以及程序执行结果。

    为了提高传输性能，OPC UA消息可以被编码生XML文本格式或是二进制格式。它们可以使用多种传输协议进行传输，例如：TCP或是通过HTTP的网络服务。规范的第七部分介绍了不同的编码和传输机制。

2.4 会话
    OPC UA需要一个状态模型。状态信息被保存在应用程序会话之中。例如，状态信息可能包括订阅信息，用户认证书和跨越多重请求操作的延长点信息。

    会话就是客户端和服务器之间的合法连接。服务器可以根据有效资源，许可限制或其他约束条件来限制并发的会话的数量。每个会话是不依赖底层通信协议的。通信协议的失败不会自动终止会话。会话的终止依靠客户端或服务器的指令，或客户端的失效。在会话建立时，要设定会话的间隔时间。

2.5 冗余

    OPC UA的机制确保了开发商可以用同一种方式开发冗余客户端和服务器。冗余可用于提高系统的稳定性，容错性和负载平衡能力。规范的第四部分介绍了冗余的细节。规范的子协议中要求冗余支持，但是基本协议不需要冗余支持。

 【3. OPC UA 系统概要】

3.1 总貌
    OPC UA系统结构以相互联系对象的方式模型化了OPC UA客户端和服务器。每个系统可能包含多个客户端和服务器。每个客户端可能同时与一个或多个服务器相连接，每个服务器也可能同时与一个或多个客户端相连接。一个应用程序可能同时包含了服务器和客户端的两部分组件，以此来达到与其他服务器和客户端的连接要求，3.3.6节描述了这种情况。

3.2 OPC UA客户端

    OPC UA客户端结构模型化了C/S结构中的客户端部分。

    客户端应用程序的代码实现了客户端的功能。客户端应用程序使用OPC UA客户端的API来向OPC UA服务器发送和接收相关服务的请求和响应。第四节介绍了OPC UA的服务，规范的第四部分详细说明了OPC UA的服务。

    注意到“OPC UA客户端API”是一个内部接口，它把客户端应用程序代码从OPC UA通信堆栈中分离出来了。OPC UA通信堆栈把OPC UA客户端的API调用转换成消息，并通过底层消息体发送给服务器，通知服务器客户端应用程序的请求。OPC UA通信堆栈也接受来自服务器的响应和通知消息，并通过OPC UA客户端API传递给客户端应用程序。

3.3 OPC UA服务器

    OPC UA服务器结构模型化了C/S结构中的服务器部分。

3.3.1 真实对象

    真实对象是可以由OPC UA服务器应用程序直接访问的物理设备或包含在其内部的软件程序。

3.3.2 OPC UA服务器应用程序

    OPC UA服务器应用程序的代码实现了服务器的功能。服务器应用程序使用OPC UA服务器的API来向OPC UA客户端发送和接收消息。注意到“OPC UA服务器API”是一个内部接口，它把服务器应用程序代码从OPC UA通信堆栈中分离出来了。这可能是OPC基金会提供的一个标准应用或是由生产商制定的应用。

3.3.3 OPC UA地址空间
3.3.3.1 地址空间节点
    地址空间由一系列节点组成，客户端可以通过使用OPC UA服务（接口和方法）来访问节点。地址空间中的节点用来代表真实对象，以及它们的定义和相互之间的引用。

3.3.3.2 地址空间组织

    规范的第三部分讲述了用“积木”模型以一种标准的一致的方式构造空节点地址空间的细节。服务器可以在它们的地址空间中自由的组织它们选择的节点。节点间引用的使用，允许服务器可以把地址空间组织成分层结构，网状节点结构，或任何可能的结构混合。

规范的第五部分定义了OPC UA节点，引用以及它们在地址空间中组织结构的标准。

3.3.3.3 地址空间概要
    视点是地址空间的子集。视点限制了服务器向客户端暴露的节点数量，也就限制了客户端所能请求到的地址空间尺寸。视点的默认设置是整个地址空间。服务器可以有选择的定义其他视点。视点也就隐藏地址空间中的某些节点和引用。通过地址空间视点是可见的，客户端可以通过浏览视点从而确定它们的结构。视点通常是分层结构的，这样利于客户用树形结构来理解和表示它。

3.3.3.4 对信息模型的支持
    OPC UA地址空间支持信息模型。支持如下：a)节点引用允许地址空间中的对象相互关联；b)对象类型节点为真实对象提供语义信息（类型定义）；c)对象类型节点支持类型定义子集；d)地址空间中暴露的数据类型定义允许使用工业上特定的数据类型；e)OPC UA的联合标准允许工业团体在OPC UA服务器的地址空间中制定它们特定信息模型的表示方法。

3.3.4.1 监控项
    监控项是由客户端在服务器中创建的实体，它用来监控地址空间中的节点和它们现实世界中所对应的实体。当监控项检测到数据变化或有事件或报警发生时，它们就产生通知，由订阅传送给客户端。

3.3.4.2 订阅
    订阅是服务器中的一个终端，它用来向客户端发布通知。它是客户端控制发布的条件。

3.3.5 OPC UA服务接口
3.3.5.1 概要
    第四节对OPC UA定义的服务进行了介绍，规范的第四部分对它们进行了详细说明。
3.3.5.2 请求/响应服务
    请求或响应服务是由客户端通过OPC UA服务接口调用的服务，它们对地址空间中的节点进行特定的操作并返回操作结果。
3.3.5.3 发布服务
    发布服务是由客户端通过OPC UA服务接口调用的服务，它的作用是周期性地向客户端发送通知。通知都包括事件，报警，数据变化以及程序输出结果。
3.3.6 服务器之间的关联
    服务器之间的关联就是一个服务器作为另一个服务器的客户端。服务器之间的关联考虑到了服务器的以下拓展能力：a)相互间以点对点的形式交换信息，这使得一个服务器可以连接一个冗余服务器或是一个远程服务器，用它们来保存系统额外的类型定义；b)以分层结构链接起来的服务器可以提供如下功能：1)集合底层服务器的数据；2)上层数据发往客户端；3)客户端的接口层为每个底层服务器提供单一访问结点。

 

【4. OPC UA 服务设置】

4.1 概要

    OPC UA服务被划分成不同的服务子集，每个子集定义了一组逻辑上相关的服务，用于显示服务器一个特定的方面。以下介绍了服务子集。规范的第四部分详细说明了服务子集和它们所包含的服务。无论一个服务器是否支持一个服务子集，服务子集中的特定服务都被服务器的协议所定义。规范的第七部分介绍了协议。

4.2 安全通道服务集

    这个服务子集定义的服务用作去查询一个服务器的安全配置并且构造一个通信通道，这个通道可以确保与服务器交换的所有消息是保密的，完整的。规范的第二部分定义了UA安全性的基本概念。

    安全通道服务与其他服务不同，因为安全通道服务不被UA应用程序直接执行。它们是由UA应用程序所依靠的通信堆栈来提供的。例如，一个UA服务器可能被建立在一个简单对象访问协议堆栈上，这个协议堆栈允许应用程序使用网络服务安全会话规范建立安全通道。在这些情况下，当UA应用程序接收到消息时，它仅需要校验网络服务安全会话是可用的。规范的第六部分描述了安全通道服务如何被使用。

    安全通道是单一客户端和单一服务器之间一个长期运行的合法连接。通道内保存了许多只有客户端和服务器知道的密钥，这些密钥用于认证和编码在网络间传输的消息。安全通道服务允许客户端和服务器安全协商密钥的使用方法。

    服务器的安全策略描述了鉴定和加密消息的确切算法。一个客户端在构造一个安全通道时，必须选择一种服务器所支持的安全策略。

    当一个客户端和服务器通过安全通道进行通信时，它们必须核实所有正在传入的消息已经依照某种安全策略进行了标识和加密。一个UA应用程序不能处理通道内不符合安全策略的消息。

    安全通道与UA应用程序会话是相分离的，然而，一个UA应用程序会话只能通过唯一的安全通道进行访问。这说明了UA应用程序必须能够决定每条消息所联系的安全通道。通信堆栈提供了安全通道机制，但它不允许应用程序知道用于给定消息的安全通道，是不能用于完成安全通道服务的。

    UA应用程序用通信堆栈去交换消息。首先，用安全通道服务在通信堆栈间构造一个安全通道，使得通信堆栈之间可以安全交换消息。然后，UA应用程序使用会话服务子集构造一个UA应用程序会话。

    当一个客户端构造一个安全通道时，它可能提供一个用户标识。这个标识可能与客户端初始化UA应用程序会话时所提供的用户标识不一样。


4.3 会话服务集
    这个服务集定义的服务用作去构造一个应用层的连接，这个连接就是为了一个特定用户而建立的会话。

 
4.4 节点管理服务集

    节点管理服务集允许客户去添加，修改以及删除地址空间里的节点。这些服务为服务器的构造提供了一个标准接口。

4.5 视点服务集

    视点是由服务器创造的地址空间子集。视点的默认值是全部地址空间。因此，视点服务可以操作整个地址空间。规范的未来版本可能会制定相应服务来构造客户端定义的视点。

    视点服务允许客户端通过浏览视点查找节点。客户端在视点中进行分层查找，或通过节点间的引用进行查找。在这种方式下，也允许客户端查看视点的结构。

4.6 属性服务集

    属性服务集用作去读写属性值。属性是由OPC UA定义的节点原始特性。它们可能不是由客户端和服务器来定义的。属性是地址空间中允许存放数据值的唯一元素。一个特定的属性，属性值用来定义变量的值。

4.7 方法服务集

    方法代表了对象的函数调用。规范的第三部分定义了方法服务。方法被调用，无论成功与否，都在方法执行完毕后返回。不同方法的运行时间可能不同，这主要取决于它们运行的函数。

    方法服务集定义了调用方法的手段。一个方法必须是一个对象的组件。方法的暴露由浏览和查询服务来提供。客户端查询一个服务器所支持的方法是通过浏览特有的对象来完成的，这些对象标识了自己所支持的方法。

    因为方法可以控制设备操作的某些环节，所以方法调用可能依靠环境条件或其他条件。这使得反复调用同一种方法成为可能。需要调用方法的条件可能先前并没有返回一个允许该方法重新启动的状态。另外，有些方法可能支持并发调用，而有些方法只能单独调用。

4.8 监视项服务集

    监视项服务集被客户端用来去构造和保存监视项。监视项用来监视变量，属性和事件通知器。当它们检测到特定条件发生时，它们会产生相应通知。监视项监视变量数值，状态或时间戳的变化；属性值的变化；以及事件通知器对新产生的报警和事件的报告。

    每个监视项都标识了要监视的项目和用于向客户端周期性发布通知的订阅（参阅4.9节）。每个监视项也指定了被监视项目的采集频率，对于变量和事件通知器，用过滤标准来决定什么时候来产生通知。属性的过滤标准由规范第四部分的属性定义来加以说明。

    监视项的采样速度可能比订阅的发布速度更快。所以，监视项可能由一个包含所有通知的队列组成，或是由一个仅含有最近通知的队列组成。第二种情况，队列里只含有一个通知。

    监视项服务也定义了一个监视模式。这个模式可以配置成三种模式：不采集不报告模式，仅采集模式，或是既采集也报告模式。当设置了采集模式时，服务器采集被监视项的值（或状态）。另外，通过对采集结果的判断来决定是否产生一个通知。如果需要产生通知，则构建一个通知队列。如果允许报告，则通知队列可以由订阅来向外发送。

    最后，一个监视项的报告选项能够由其他监视项来设置。在这种情况下，需要报告的监视项的监视模式仅需要再设置采集选项就可以了，当被触发的监视项产生一个通知时，需要报告的监视项通知队列由订阅来向外发送。

4.9 订阅服务集

    订阅服务集由客户端构造并保持和使用。订阅周期性的发布来自它们相关监视项的通知消息（参阅4.7节）。所有通知都应包含一个公共消息头。通知的格式与被监视项目的类型有关。（例如：变量，属性，和事件通知器）。

    已构造出的存在的订阅并不依靠客户端与服务器的会话。这就允许由一个客户端来构造订阅，另一个客户端，可能是冗余客户端，从订阅上来接受通知消息。

    有些客户端并不需要订阅，所以订阅设置了一个由客户端周期性更新的生命周期属性。如果客户端没有成功更新订阅的生命周期，则订阅终止，服务器关闭订阅。当一个订阅被关闭后，所有与它关联的监视项都被删除。

    订阅也包括支持检测和恢复丢失消息的特性。每个通知消息都包含一个允许客户端检测丢失消息的序号。当没有通知在有效时间间隔内需要发送时，服务器发送一个保持消息，它含有最后一次被传送消息的序号。如果客户端在通信时间间隔终止之后还没有收到消息，它可以要求服务器重发先前消息。

4.10 查询服务集

    查询服务集允许客户端选择地址空间中的一个节点子集或是一个视点中的节点子集，视点建立在客户端提供的过滤标准的基础上。被查询服务选择的节点和属性叫做一个结果集。结果集可能是节点的简单组合，其中也可能包含了节点间引用的结构。

    服务器可能发现有些查询不好处理，如查询诸如设备数据一样的实时数据，或是查询操作需要消耗大量资源或存在较长延时。这些情况下，服务器可以拒绝查询。