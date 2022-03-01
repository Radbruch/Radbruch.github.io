---
layout: post
title: Java Switch
categories: ["Java"]
excerpt_separator: ""
tags: [Java]
---

61b讲switch讲得很清楚，链接：
[Shewchuk](https://sp18.datastructur.es/materials/hw/hw0/hw0_supplementary_conditionals.txt)     

原文：

Some long chains of if-then-else clauses can be simplified by using a "switch"
statement. "switch" is appropriate only if every condition tests whether a
variable x is equal to some constant.

![p1]( /assets/img/javaswitch/p1.png)

<b>IMPORTANT</b>: "break" jumps to the end of the "switch" statement. <b>If you forget
a break statement, the flow of execution will continue right through past the
next "case" clause</b>, which is why cases 4, 6, and 9 work right. If month == 12
in the following example, both Strings are printed.

{% highlight java linenos %}
switch (month) {
    case 12:
        output("It's December.");
        // Just keep moving right on through.
    case 1:
    case 2:
    case 11:
        output("It's cold.");
}
{% endhighlight %}

However, this is considered bad style, because it's hard to read and
understand. If there's any chance that other people will need to read or
modify your code (which is the norm when you program for a business), don't
code it like this. <b>Use break statements in the switch, and use subroutines to
reuse code and clarify the control flow.</b>

Observe that the last example doesn't have a "default:" case. If "month" is
not 1 nor 2 nor 11 nor 12, Java jumps right to the end of the "switch"
statement (just past the closing brace) and continues execution from there.