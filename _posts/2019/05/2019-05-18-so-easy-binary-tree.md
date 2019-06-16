---   
layout:     post  
title:  二叉树就是这么简单  
description: 基础的数据结构分享玩了  
keywords: 算法  
tags: [算法]    
categories: [算法]  
updateData: 2019-05-18 23:24   
published: true 
wxurl: https://mp.weixin.qq.com/s/WyU9lAzilCDF6t-037cGtw  
---  


## 一、背景  


本来之前写过《[数组](https://mp.weixin.qq.com/s/n_B38CXxmvsOl7FZxyPKgA)》、《[链表](https://mp.weixin.qq.com/s/SQCJWiG2HMhI8U-hVTvk7A)》、《[队列与栈](https://mp.weixin.qq.com/s/y9vQ5gUdUAfiZXZFHoVrKg)》、《[哈希](https://mp.weixin.qq.com/s/7x_N_84q2Lz7Q23Str-TqQ)》、《[二分查找](https://mp.weixin.qq.com/s/d5vqd4YHnZ4Opms1H-kpDg)》，后面就开始写树相关的文章了。  


结果上篇文章没介绍《二叉树》，直接介绍《[二叉搜索树](https://mp.weixin.qq.com/s/xgO36QdiQF30L981YSfKwA)》了。  
今天把《二叉树》的知识补上。  


## 二、基础知识  


树是一种经常用到的数据结构，用来模拟具有树状结构性质的数据集合。  


树里的每一个节点有一个根植和一个包含所有子节点的列表。  


二叉树是一种更为典型的树树状结构。  
如它名字所描述的那样，二叉树是每个节点最多有两个子树的树结构，通常子树被称作“左子树”和“右子树”。  


## 三、树的遍历  


二叉树一般有三种遍历：前序遍历、中序遍历、后续遍历。  


前序遍历首先访问根节点，然后遍历左子树，最后遍历右子树。  
中序遍历是先遍历左子树，然后访问根节点，然后遍历右子树。  
后序遍历是先遍历左子树，然后遍历右子树，最后访问树的根节点。  


通常来说，使用递归进行这三种遍历都是非常简单的事情。  
而使用迭代的方法实现这三种遍历，就需要使用自己维护栈这个数据结构了。  


二叉树的前序遍历相对还算简单，对于当前树根节点，直接输出答案。  
代码如下。  


![](http://res.tiankonguse.com/images/2019/05/18/001.png)  


而对于中序和后续遍历，则存在一个问题：当前树的根节点怎么保存。  
出栈的时候，我们怎么知道这是一个尚未处理的子树，还是已经处理的子树。  


如果可以修改树的节点值，那处理过的节点置为空即可。  


例如中序遍历的代码如下：  


![](http://res.tiankonguse.com/images/2019/05/18/002.png)


后续的代码和中序很类似，这里就不上代码了。  


有时候，我们需要一层层的遍历树。  
这个其实就是常见的 广度优先搜索，简称 BFS。  
我们一般使用队列这个数据结构来实现 BFS，在队列的系列中已经教过大家了。  


## 四、相关实践  


树的问题一般有两种：  
一种是递归到叶子节点就确定一个答案的。  
一种是根据两个儿子的状态，再加当前节点的状态，综合得到一个答案。  


比如树的最大深度，两种方法都可以。  


![](http://res/tiankonguse.com/images/2019/05/18/003.png)


对于判断树是否树对称二叉树，则只能使用第二种方法。  


![](http://res.tiankonguse.com/images/2019/05/18/004.png)


而对于是否存在一条根到叶子节点的路径和等于指定数字的问题，则使用第一种方法。  


![](http://res.tiankonguse.com/images/2019/05/18/005.png)


## 五、最后  


好了，二叉树的基础知识相信你了解的差不多了。  
随后我会把这些问题的题号留言放出来。  
另外，对于其他文章，如果你发现对应的题号没放出来，可以留言告诉我，可能我之前忘记了。  



-EOF-  

