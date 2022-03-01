---
layout: post
title: Primitive types and reference type in Java
categories: ["Java"]
excerpt_separator: ""
tags: [Java]
---

<b>8 primitive types</b>: byte, short, int, long, float, double, boolean, char.

When declare a variable of certain type:
* int: set aside a "box" of 32 bits.
* double: set aside a "box" of 64 bits.    

And creates an internal table that maps each variable name to a location.

---
因为不同type有不同编译方法，即使二进制数一致，不同type会显示不同的“human readable symbols”。例如：
{% highlight java linenos %}
char c = 'H';
int x = c;
System.out.println(c);
System.out.println(x);
{% endhighlight %}

If we run this code, we get:
{% highlight java linenos %}
H
72
{% endhighlight %}

Equal sign("=") just copies the bits.

---
<b>Reference types</b>: 除了8种primitive types外，都是reference type.

When we instantiate an object:

![p1]( /assets/img/PrimitiveType/p1.jpg)
![p2]( /assets/img/PrimitiveType/p2.jpg)
![p3]( /assets/img/PrimitiveType/p3.jpg)

与给变量赋一个primitive type 不同，reference type 相当于给变量创建一个 instruction memory，对应的是该实例的位置(64 bits)，而primitive type是给变量创建一个data memory，这个memory直接储存了对应的二进制的值。这就是为什么：

![p4]( /assets/img/PrimitiveType/p4.jpg)

Reference types关于区分 declaration 和 instantiation( 用array举例）：

![p5]( /assets/img/PrimitiveType/p5.jpg)