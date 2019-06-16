---   
layout:     post  
title:  面试中必问的几道链表环问题  
description: 有几道链表相关的题面试者必问，你会吗？  
keywords: 算法  
tags: [算法]    
categories: [算法]  
updateData: 2019-04-16 23:24   
published: true 
wxurl: https://mp.weixin.qq.com/s/2tT4j-ePNeoktqkVNvAqJQ  
---  


## 一、背景


之前介绍了链表的基础知识《[单向链表就是这么简单](https://mp.weixin.qq.com/s/rG1ehI-9QK8h7p6_KkRJew)》，现在来看看几道链表题吧。  
有几道链表题在面试者是必问的。  
下面我们来看看吧。  


## 二、判断链表环  


问题：给你一个链表，请判断链表中是否有环。  


在前面《[双指针就是这么简单](https://mp.weixin.qq.com/s/w6HdSIOEHJRnTCQp1wkZDQ)》文章里，提到过双指针。  
而链表里面，判断是否有环，需要使用双指针技术，更具体的说是快慢指针技术。  


对于这样的题，其实不是一个好的面试题。  
因为听过快慢指针了就会做，没听过就很难独立想出这个方法来。  


那该如何使用快慢指针做这道题呢？  


你这样想：有两个指针，一个每次向后移动一下，另一个每次向后移动两下。  
如果没环，那就会遇到某个指针是`NULL`，自然就判断出没环了。  
如果有环，那么慢指针和快指针在环上就会相遇，从而判断出有环。  


对于没环的，很容易理解。  
而对于有环的，则存在两个疑问：  


1.快指针和满指针一定会相遇吗（不然就死循环了）？  
2.多久会相遇（转几亿次和死循环没区别）？


对于第一个疑问，可以这样证明。  
假设满指针刚到达链表与环的交点时，快指针到满指针的距离是`C`。  
快慢指针每移动一次，这个距离就减一，这样移动下去距离肯定会是零，即相遇。  


对于第二个疑问，上面的证明其实已经看直接看出结果来了。  
刚开始距离是`C`，每移动一下距离减一，那移动`C`下就相遇了。  
这个`C`是环上两点的距离，所以不大于环长，即不超过一圈既可以遇到慢指针。  


接下来就是实现代码了，也很简单，如下图。  


![](http://res.tiankonguse.com/images/2019/04/15/link-problem-in-interview-001.png)  


## 三、找链表环交点  


问题：给一个链表，返回环交点的指针。如果没有环，返回`NULL`。  


上一小节中已经教你怎么判断是否有环了。  
而且还得出结论：环上，慢指针跑不了一圈快指针就赶上了。  


那怎么找到这个交点呢？  
我们画画图，列出方程，会推导出一个公式来。  
如下图：  


![](http://res.tiankonguse.com/images/2019/04/15/link-problem-in-interview-002.png)  


可以看到`L1=L3+(k-1)*L`，其几何意义就是我们从起点`a`和相遇点`c`出发，下次相遇点肯定是交点`b`。  
是不是好神奇？  
因此我们可以实现对应的代码了。  


![](http://res.tiankonguse.com/images/2019/04/15/link-problem-in-interview-003.png)  


## 四、找两个链表的交点  


题意：给你两个链表的头指针，判断这两个链表是否相交。如果相交，输出交点。  


第一个问题：链表是否相交。  
这个只需要遍历两个链表到最后，如果最后一个指针相同，那就相交了。不同就没相交。  


第二个问题是：相交了，怎么找到交点。  
这个看看上面的链表环问题，你应该很容易想到把最后一个指针指向任意一个指针头，是不是就是求链表环的交点了？  


那有没有其他方法呢？  
其实有一个很简单的方法，只是由于你先遇到了链表环问题，就先入为主，去想环的解决方法了。  
既然是两个链表，你分别求出两个链表的长度，是不是就可以循环找到交点了？  


还不明白？  
假设一个链表长，一个链表短。你先遍历长链表，使得两个链表的长度相等。  
然后再同时遍历两个链表，相遇时就是交点了。  
是不是很简单？  


![](http://res.tiankonguse.com/images/2019/04/15/link-problem-in-interview-004.png)  


## 五、删除链表的倒数第N个节点  


题意：给一个链表，要求只扫描一遍链表，删除倒数第`n`个节点，并返回链表头。  


思路：如果使用递归的方法，可以解决这道题。但是那种方法实际上是遍历了两边链表（想象自己使用栈实现递归）。  


这时候就需要再次搬出之前提到的《[双指针就是这么简单](https://mp.weixin.qq.com/s/w6HdSIOEHJRnTCQp1wkZDQ)》了。  
如果你使用一个两个指针，距离是`n`，然后分别后移。后面的移动到最后时，前面的是不是就指向需要删除的节点了？  


![](http://res.tiankonguse.com/images/2019/04/15/link-problem-in-interview-005.png)  


## 六、最后  


好了，到这里你应该能够掌握面试里被问的频率最高的链表题了。  
这些就是判断链表是否有环、寻找链表环交点、判断两个链表是否相交、寻找两个链表的交点。  
而对于最后一道题，是免费送给你们的练习题。  


互动环节：你在面试中被问过这几道题吗？还被问到哪些链表题呢？  


-EOF-  

