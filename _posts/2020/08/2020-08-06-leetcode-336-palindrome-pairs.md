---   
layout:     post  
title: leetcode 336. 回文对
description: 暴力判断回文串。  
keywords: 程序人生  
tags: [程序人生]    
categories: [程序人生]  
updateData:  2020-02-18 21:30:00  
published: true  
---  


最近尝试使用 golang 做每日一题。  


leetcode 在 2020-08-06 的每日一题是 336 回文对。  


题意：给一个字符串数组，挑选两个字符串当做前后缀组成新串可能是回文串。  
求所有是回文串的组合。  


思路：最简单的方法就是暴力，即枚举所有组合，判断是不是回文串。  


不过暴力里面也有优化，我们不能额外申请内存，需要在两个字符串上判断是不是回文串。  


大概思路是，如果前缀后缀长度不相等，从两边依次比较，某个游标到达边界时会还剩下一段字符串没比较。  
此时判断那段字符串在前缀还是后者，然后调整游标边界继续比较即可。  


![](http://res.tiankonguse.com/images/2020/08.06/001.png)  


点评：由于是暴力方法，复杂度为`O(n^2 * L)`，所以耗时较长。  
不过没有使用内存，内存排名比较靠前。  


![](http://res.tiankonguse.com/images/2020/08.06/002.png)  


优化：暴力是枚举所有组合。  
如果预先使用字典树建立好索引，就可以直接查找对称回文的串。  
此时复杂度是`O(n * L)`，降低一个复杂度。  



思考题：你能使用字典树实现这道题吗？  




《完》


-EOF-  



本文公众号：天空的代码世界  
个人微信号：tiankonguse  
QQ算法群：165531769（不止算法）  
知识星球：不止算法  
