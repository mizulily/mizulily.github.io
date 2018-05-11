---
title: 《Learning hard C#学习笔记》笔记
date: 2018-04-28 08:55:46
tags:
  - C#
  - programming language
categories: note
toc: true
---

<!-- toc -->
## 第一章 基础知识 ##

C#


## 第八章 委托

**委托**是C#中最中需要的特性之一，它使得C#中的函数可以作为参数被传递，与C/C++中的函数指针类似。它是一个特殊的类，所有的委托都是从System.MulticastDelegate类派生的。
委托的定义和方法的定义类似，只是在定义前多了一个delegate关键字：

    访问修饰符 delegate 返回类型 委托名([参数表])

能被委托包装的方法需要满足：
1. 方法的签名与委托一致（参数个数、类型、顺序）
2. 方法的返回类型与委托一致

委托也可以封装多个方法，称为**委托链**或多路广播委托，在委托链上的委托都会被顺序执行。可以通过“+”运算符把委托链接到一个委托对象实例上，也可以使用“-”运算符将某个委托从委托链对象上移除。

{% fold 委托和委托链的例子（点击显示代码） %}
``` csharp
using System;

namespace CSbook
{
    class Program
    {
        //委托的定义
        public delegate void MyDelegate(int para1, int para2);

        private static void MyMethod(MyDelegate mydelegate){
            mydelegate(1, 2);
        }
        static void Main(string[] args)
        {
            MyDelegate m = new MyDelegate(Program.Mult);
            // 方法Program.Mult作为方法MyMethod的参数
            MyMethod(m);
            

            MyDelegate p = new MyDelegate(new Program().Add);
            MyDelegate q = new MyDelegate(new Program().Sub);
            MyDelegate chain = null;
            chain += m;
            chain += p;
            chain += q;
            chain -= m;
            chain(1,2);

            Console.Read();
  
        }
        // 实例方法
        void Add(int para1, int para2){
            int sum = para1 + para2;
            Console.WriteLine("Sum is: " + sum);
        }
        void Sub(int para1, int para2){
            int sub = para1 - para2;
            Console.WriteLine("Sub is: " + sub);
        }
        // 静态方法
        static void Mult(int para1, int para2){
            int mul = para1 * para2;
            Console.WriteLine("Mul is: " + mul);
        }

    }
}
```
{% endfold %}

## 第九章 事件
