---
title: 开源软件协议
date: 2019-02-28 08:46:32
tags:
  - open source
  - license
categories: knowledge
hide: true
end: true
---

现今存在的开源软件协议很多，而经过Open Source Initiative 组织通过批准的开源协议目前有60多种（http://www.opensource.org/licenses/alphabetical ）。

要分清楚不同的开源协议，需要了解以下基本概念。
**贡献者**指对开源项目提供了代码的人或实体，按照贡献的先后又可分为创始人和参与者；**获取者**是指开源项目的使用者。
**源代码**是指由各种语言写成的未经编译的程序文本；**目标代码**是指经过编译后生成类似“类库”的程序，提供各种接口给他人使用的代码，如dll, jar等。
**衍生模块**是指依托或包含开源代码而产生的代码；**独立模块**是指参考或借助开源代码开发出来的独立的、不包含或依赖源代码的功能模块。

![licenses](know-opensource/opensource.png)

在OSI网站上被列为主流及被广泛使用的许可有：
1. Apache License, 2.0 (**Apache**-2.0)
允许使用者以其他协议形式修改和重新发布代码，允许闭源商业发布和销售，同时鼓励代码共享和尊重原作者著作权。

2. Berkerly Software Distribution (**BSD** 3-Clause, BSD 2-Clause)
允许使用者以其他协议形式修改和重新发布代码，允许闭源商业发布和销售，同时鼓励代码共享和尊重原作者著作权。

3. General Public Licese (**GPL**)
源代码和目标代码免费使用，但修改或衍生的代码不允许作为闭源的商业软件发布和销售，同时修改或衍生的代码必须采用同样的GPL许可证。

4. Lesser General Public Licese (**LGPL**)
允许商业软件通过目标代码引用的方式使用LGPL类库而不需要开源，但是修改或新增的额外代码必须采用LGPL协议，因此适合作为第三方类库引用，而不适合做二次开发。

5. MIT license (**MIT**)
允许修改、使用甚至出售MIT协议的代码，但是必须在发行版里包含原许可协议的声明。

6. Mozilla Public License 2 (**MPL**v2)
允许免费重发布、修改和使用，但要求修改后的代码版权归软件的发起者，围绕该软件的所有代码版权都集中在发起者手中。

7. Common Development and Distribution License (**CDDL**-1.0)
MPL的扩展协议，允许公共版权使用，无专利费并提供专利保护，可集成于商业软件中，允许自行发布许可。

8. Eclipse Public License (**EPL**-1.0)
允许任意使用、分发、修改及修改后闭源二次商业发布，但必须声明商业发布的源代码或目标代码的原始版本时可以获取的，并告知获取方法。