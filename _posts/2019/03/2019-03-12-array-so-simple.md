---   
layout:     post  
title:  【算法】数组就是这么简单  
description: 数据结构中的基础知识有很多，计划一点点介绍，这篇文章介绍数组。  
keywords: 算法  
tags: [算法]    
categories: [算法]  
updateData: 2019-03-12 23:24   
published: true 
wxurl: https://mp.weixin.qq.com/s/pjADME31K5IBVQ0YMhWNpA  
---  


## 一、背景


这篇文章主要介绍数组与动态数组，然后分享三个例子来辅助讲解数组的使用。  


## 二、数组  


数组是一个顺序储存数据的基本数据结构。  
由于数组的每个元素可以通过下标来访问，所以数组支持随机访问。  


数组可以有一维或者多维。  
这里先讲一维数组，也就是线性数组。  
例如下图：  


![](http://res.tiankonguse.com/images/2019/03/array-so-simple-001.png)  


在这个例子中，数组`A`有6个元素。  
也就是说数组的长度是`6`。  
我们可以通过`A[0]`来代表数组的第一个元素。  
因此`A[0]`可以得到值`6`，同样的，`A[1]`可以得到值`3`，`A[2]`可以得到值`8`。  


具体操作如下：  


![](http://res.tiankonguse.com/images/2019/03/array-so-simple-002.png)  


## 三、动态数组  


前面提到，对于数组是有固定的容量的。所以初始化数组的时候我们需要指定数组的长度。  
有时候，这种固定数组会有些不方便，而且也会造成空间浪费。  


因此，很多程序语言都默认支持动态数组。它仍然是一个随机访问的列表数据结构，但是大小可变。  
例如，在`C++`语言中，这个动态数组就是`vector`。  


![](http://res.tiankonguse.com/images/2019/03/array-so-simple-003.png)  


## 四、寻找数组的中心索引  


对于给定的一个数组，我们需要求对应的中心索引。  
中心索引定义：中心索引左侧所有元素之和等于右侧所有元素之和。  
如果不存在中心索引，则返回`-1`。如果存在多个，则返回最靠左边的那个索引下标。  


中心索引的左侧所有元素和右侧所有元素之和相等，那我们可以三步。  
第一步计算所有索引左侧元素之和。  
第二步计算所有索引右侧元素之和。  
第三部查找满足条件的中心索引。  


![](http://res.tiankonguse.com/images/2019/03/array-so-simple-004.png)  


## 五、至少是其他数字两倍的最大数  


给一个数组，总是存在唯一的最大值。  
我们需要判断这个最大值是否大于等于其他数字的两倍。  
如果是，则返回最大值的下标，否则返回`-1`。  


这道题分两步。  
第一步是找到最大值和下标。  
第二步是判断是否满足条件。  
注意事项是判断是否满足条件时，需要过滤最大元素。  


![](http://res.tiankonguse.com/images/2019/03/array-so-simple-005.png)  


## 六、加一  


给定一个一位整数组成的非空数组来表示非负整数。  
求加一后的数组。  


这道题有点大整数运算的味道。  
不过这里只要求加一。  


想想我们在纸上计算加一操作的步骤。  
首先个位加一，判断是否需要进位，不需要则计算结束。  
需要进位则将进位的数字加到十位，然后继续判断。  
如果到达最高位，依旧要进位，我们就将进位的数字补在最前面（总位数加一）。  


面对这道题，也应该分几步。  
第一步是循环计算进位。  
第二部是判断最高位是否依旧需要进位，需要则将进位插入到最前面。  


![](http://res.tiankonguse.com/images/2019/03/array-so-simple-006.png)  


## 七、最后  


作为一个程序员，大家看到这篇文章肯定会感觉特别水。  
不过没关系，数据结构刚开始就是很简单很水的，到后面难度会逐渐增加的。  
希望我能够坚持到那一天吧。  


-EOF-  


  