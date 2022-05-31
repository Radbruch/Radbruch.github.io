---
layout: post
title: Binary Search Trees
categories: ["Data Structure"]
excerpt_separator: ""
tags: [Data Structure]
---

### I. 溯源

![p1]( /assets/img/BST/p1.png)
<center>↑↑(Linked List Set)↑↑</center>

我们在使用有序的LinkedListSet时，如果要寻找一个值，通常会使用for loop，需要linear time，是否有一种方法提高搜索的效率？因此产生了Binary search trees.

![p2]( /assets/img/BST/p2.png)
<center>↑↑(Binary search trees，从中间值切入，若中间值比目标值小，则往右；若中间值比目标值大，则往左。)↑↑</center>  

  

首先回顾一下原始的Rooted trees.

![p3]( /assets/img/BST/p3.png)

↑↑(rooted trees)↑↑

* 除了root以外的每个node只有一个parent。
* 最顶上的那个node通常被视为root。
* 没有child的nood被称为leaf。
* 任意两个node之间，只能有一条路径。
* 每个node的值被称为label.

Rooted Binary search tree 除了拥有以上rooted trees的特征外，

* 所有node都不能有重复。
* 每个node只有0，1 或 2个children.
* 每个node的左分支都小于这个node，右分支都大于这个node。
  

![p4]( /assets/img/BST/p4.png)


### II. 内容

**1. Search operation原理**

出发点(递归原理)：

如果label等于目标值，则return.（base case）

* 如果label大于目标值，搜索左边分支
* 如果label小于目标值，搜索右边分支
  

Pseudo code：
{% highlight java linenos %}
static BST find(BST T, Key sk) {
    if (T == null)
        return null;
    if (sk.equals(T.key))
        return T;
    else if (sk ≺ T.key)
        return find(T.left, sk);
    else
        return find(T.right, sk);
}
{% endhighlight %}

**2. runtime**

在最差的情况下，也就是搜索值不在该binary search trees里，runtime为 Θ(logN).

**3. Insert operation原理**

Search for key.

If found, do nothing
If not found:
* Create new node
* Set appropriate link
  

Pseudo code:
{% highlight java linenos %}
static BST insert(BST T, Key ik) {
    if (T == null)
        return new BST(ik);
    if (ik ≺ T.key)
        T.left = insert(T.left, ik);
    else if (ik ≻ T.key)
        T.right = insert(T.right, ik);
    return T;
}
{% endhighlight %}

**4. Delate operation原理**

3 possible cases:

1.Deletion key has no children.
* Directly delete its parent pointer.
2.Deletion key has one children.
* Reassign the parent's child pointer to the node's child.
3.Deletion key has two children.
* 选左边的最大数，右边的最小数。这俩数都不会有两个children

**5. 源代码**  

[BST.java](https://algs4.cs.princeton.edu/32bst/BST.java.html "BST.java")

### III.如何用Binary search trees表示map

![p5]( /assets/img/BST/p5.png)

### IV.Some terminology for BST performance:

![p6]( /assets/img/BST/p6.jpg)

* depth: the number of links between a node and the root.
* height: the lowest depth of a tree.
* average depth: average of the total depths in the tree. You calculate this by taking 

  <img src="https://www.zhihu.com/equation?tex=%5Cfrac%7B%5Csum_%7Bi%3D0%7D%5E%7BD%7D%7Bd_%7Bi%7Dn_%7Bi%7D%7D%7D%7BN%7D" alt="[公式]"  />where <img src="https://www.zhihu.com/equation?tex=d_%7Bi%7D" alt="[公式]"  /> is depth and <img src="https://www.zhihu.com/equation?tex=n_%7Bi%7D" alt="[公式]"  /> is number of nodes at that depth.

The **height** of the tree determines the worst-case runtime, because in the worst case the node we are looking for is at the bottom of the tree.

The **average depth** determines the average-case runtime, average-case = average depth + 1.

