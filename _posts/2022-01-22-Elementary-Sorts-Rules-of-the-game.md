---
layout: post
title: Elementary Sorts -- rules of the game (Java)
categories: ["Java"]
excerpt_separator: ""
tags: [Java]
---


<b>Goal: Sort any type of data.</b>

<b>Method: Using "Call back".</b>

* Client pass array of objects to sort() function.
* The sort() function calls back object's compareTo() method


![不同层面的行为]( /assets/img/ElementarySortsRules/p1.jpg)   
(图注：不同层面的行为)

<b>Client</b>: Sort() function 的直接使用者，只需要传入需要排序的object[].

<b>Comparable interface</b>: built in to Java 的 interface， 其中只有一个compareTo() function，可以被implement，从而使object拥有和指定 another object进行对比的能力。被implement后的compareTo函数：less than (return -1); equal to (return 0); greater than (return 1).

<b>Object implementation</b>: 某个具体的Object 对 Comparable 进行 implementation, 从而override Comparable中的compareTo() function， 使object拥有和指定 another object进行对比的能力。实现的规则是：less than (return -1); equal to (return 0); greater than (return 1).

Java中有一些 build-in comparable types: Integer, Double, String, Date, File, ....

一个 Date data type implements the Comparable interface 的例子：


![p2]( /assets/img/ElementarySortsRules/p2.jpg)   
(图注：Date data type implements the Comparable interface.)

<b>Sort implementation</b>: 由于object 已经有了可以互相compare的能力，因此可以对sort() function进行完善。

两个很有用的helper function：compares and exchanges。   



![p3]( /assets/img/ElementarySortsRules/p3.png)   
(图注：for loop: object[] 中的每个元素和之后所有元素对比，找最小的元素，和此元素换位置。)  

最后用一个Test() function测试sort完后的object[] 是否符合sort要求：
![p4]( /assets/img/ElementarySortsRules/p4.png)  