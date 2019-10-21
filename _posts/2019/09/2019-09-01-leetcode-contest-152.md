---   
layout:     post  
title:  Leetcode 第152场比赛回顾  
description: 最后一道题我做了一个小时，最后一分钟秒杀了。  
keywords: 算法  
tags: [算法]    
categories: [算法]  
updateData:  2019-09-02 21:30:00  
published: true  
wxurl: https://mp.weixin.qq.com/s/vc-QsIJ7rcst_Ch1EG5R2A  
---  


## 零、背景  


上周日做了 Leetcode 第 152 场比赛，最后一题做了一个小时，最后两分钟竟然被我水过去了。
i

![](http://res.tiankonguse.com/images/2019/09/01/001.png)


赛后，很多人说自己同样的代码就没过，原来我的常数复杂度比较低，数据样例再复杂一点点我就过不了了。  


![](http://res.tiankonguse.com/images/2019/09/01/002.png)


下面来看看这四道题吧。  


## 一、质数排列  


题意：对`1`到`n`的数字进行排列，素数必须还在素数位置，求有多少种排列。  


思路：正常的排列数是`A!`个。  
题意要求素数位置还在素数位置，则代表非素数的位置也是只能在非素数位置。  
所以素数的排列和非素数的排列互相独立。  


这里只需要分别计算出素数的个数和非素数的个数，分别求阶乘即可。  


![](http://res.tiankonguse.com/images/2019/09/01/003.png)


## 二、健身计划评估  


题意：给一个健身计划表。  
如果连续`k`天消耗的卡路里之和低于`lower`认为不合格扣一分。  
如果连续`k`天消耗的卡路里之和高于`upper`认为优秀加一分。  
问这个健身计划表最终得分。  


这里题意有点坑的地方是中文把`k`翻译为一个周期。  
按照正常的逻辑，不同周期是不重叠的，于是我直接每`k`天求一次和，结果提示`WA`，并给出了下面的例子。  


```
[6,13,8,7,10,1,12,11]
k = 6
lower = 5
upper = 37
```


看到上面的数据，我赶紧看英文题意，发现翻译有重大问题。    


英文原意是`For every consecutive sequence of k days`，也就是任意的连续`k`天，翻译竟然成了`一份计划的周期通常是 k 天`。  
实际题意就是找出所有的连续`k`天，即有`T-k+1`个`k`天。 


思路：典型的区间和问题。  
区间每次右移一次，只需要左边减去对应的值，右边加上对应的值，就可以得到最新的区间和了。  


![](http://res.tiankonguse.com/images/2019/09/01/004.png)


## 三、构建回文串检测  


题意：给一个字符串，问这个字符串的某些字串能否在不超过 `k`次修改并重新排列组合组成回文串。  


思路：由于字串允许重新排列组合，那些两两相同的字母肯定可以放在回文串的对称位置。  
所以只有落单的字母才需要进行修改。  


这里假设有 `P` 个字母落单了。  
考虑对称性，这里只需要修改`P/2`个单词就可以两两相同了，从而排列为回文串。  


由于需要统计出一个子串有多少个字母落单，这个不做优化的话，统计就是 `O(m)`的复杂度。  
再加上 `n` 个子串询问，综合复杂度就是 `O(n*m)`了。  


所以这里需要对统计进行优化，比如预先统计好所有前缀子串。  
当需要查询某个子串时，两个前缀子串的统计结果相减，就得到当前子串的统计。  


有了前缀统计这个优化，这道题就可以过了。


## 四、猜字谜  


题意：给一些 word 和 一些 puzzle。  
当 puzzle 的第一个字母在 word 里面且 word 里所有字母都在 puzzle 里，则称 word 属于 puzzle.  
问对于每个 puzzle，有多少个 word 属于它。  


例如：puzzle 是 `aboveyz`， `aaaa` 是 word。  
`aboveyz` 的第一个字母 `a` 在`aaa`中可以找到。  
而`aaa`的所有单词都可以在`aboveyz`中找到。  
所以`aaa`属于`aboveyz`。  


思路：对于每个单词，是否属于一个 puzzle 只有判断了才知道。  
所以这里可以进行暴力计算。  


但是，默认是`O(n*m*len)`的复杂度，会超时。  
我们可以通过预处理，来提高计算速度。  


第一步是过滤无效的 word。因为 puzzle 长度是 7，那超过 7 的 word 都是无效的。  
第二步是位压缩。默认判断是否属于，需要使用集合运算。而通过 位压缩，一次位判断即可得到结果。  


综合这两个优化，这道题就可以水过了。   


but，数据样例大了这道题还是过不了。  
因为这个代码在即将超时的边缘。  


如果自己使用其他语言或者c++实现的话，需要注意一下优化，尽量使用基础的数组不要使用对象。


另外，看到有人不枚举 word，而是枚举 puzzle 的所有组合。
由于 puzzle 只有7位，所有组合也就 `2^7=128`，比 word 的数量少两个数量级，所以枚举 puzzle 更快，大家可以试试。


![](http://res.tiankonguse.com/images/2019/09/01/005.png)



## 五、最后  


这次比赛前三道题用了半个小时，最后一道题用了差不多一个小时。  
说明最后一题想法还是有问题的。  


做题的时候，看到 puzzle 的长度是 `7`，知道解决这道题的关键就在于 `7` 上面。  
但是没想到 `2^7` 枚举只有 `128`，甚至我把枚举想成 `7! = 5040` 了。  


以后，看到这些 `10` 以内的数字， 就需要考虑枚举了，毕竟 `2^10` 才只有 `1024`。  



-EOF-  


本文公众号：天空的代码世界  
个人微信号：tiankonguse  
QQ算法群：165531769（不止算法）  
知识星球：不止算法  
