---   
layout:     post  
title:  IasS、PasS、SaaS都是啥？  
description: 总的来看，这些 XaaS 服务之间是有关系的。  
keywords: 程序人生  
tags: [程序人生]    
categories: [程序人生]  
updateData:  2019-06-27 21:30:00  
published: true  
wxurl: https://mp.weixin.qq.com/s/JCwMTqfeOdFEMcfNkf8mKQ  
---  

## 一、背景  


五六年前，在上学的时候就听说过 IaaS、Paas、SaaS、DaaS 这些概念。  
而最近几年，随着云服务的市场越来越大，这些概念总是不断的被提起。  


那这些概念到底是啥意思呢？  
这篇文章来解密一下这些不断炒作的概念吧。  


## 二、IaaS  


IaaS 全称是 `Infrastructure as a Service`，中文含义是`基础设施即服务`。  


这个类似于以前的 VPS。  
供应商提供操作系统、磁盘、网络流量，我们可以按需选择，这些合起来其实就是一个远程的电脑。  


然后我们在上面安装搭建各种软件，最终做出自己的服务。  
比如安装一套 LAMP（Linux、Apache/Nginx、Mysql、Php），一个网站就被搭建起来了。  


面对这种基础服务，难度非常大，一般人玩不来，必须雇佣开发人员来为自己搭建想要的系统。  


## 三、PaaS  


PaaS 全称是 `Platform as a Service`，中文含义是 `平台即服务`。  


很多本来需要自己做的事情，平台帮我们做好了。  


例如  
之前需要自己搭建数据库，现在有云数据库。  
本来需要自己搭建 CDN，现在有平台支持 CDN 分发。  
本来要自己安装 Apache 和 Php，现在 平台帮我们弄好了。  
本来要自己申请域名，现在平台直接卖给我们一个三级域名。  


这个有点类似于以前 网站主机。  
我在2011年大二的时候就买过，自己只需要实现 asp 或者 php 代码，上传上去就可以访问自己的网站了。  
至于数据库、apache、域名网站主机商都帮我搞定了。  


现在这几年，腾讯云、阿里云不仅支持基础服务，还都在大力支持云平台。  


## 四、SaaS  


SaaS 全称是 `Software as a Service`，中文含义是`软件即服务`。  


这个和 PaaS 的区别是，虽然 PaaS 提供了各种组件的功能，但是最终的产品还是需要自己去组装。  
这对于非专业人士来说，难度依旧太大了。  


所以软件即服务就出来了。  
比如现在的公众号、博客、微博、淘宝，其实都算 SaaS。  
那些 2B 的产品，大部分也属于这个范畴。  


## 五、DaaS  


DaaS 全称是 `Data as a Service`，中文含义是`数据即服务`。  


比如以前，对于数据库，纯粹的就是一个数据库，需要自己特有的协议才能读写数据。  
而现在，支持了 `云数据库`，通过一个网址 URL(HTTP) 协议就可以来读写数据库了（这里不谈数据安全）。  


比如现在的小程序，就可以直接接入腾讯云的服务，小程序直接访问接口就可以读写数据了。  


## 六、最后  


总的来看，这些 XaaS 服务之间是有关系的。  
IaaS 是基础设施。  
PaaS 和 DaaS 是在基础设施上进行了一定的包装，相当于一种中间件服务。  
而 SaaS 则是聚合各种 PaaS，实现了具体的产品，来对外服务。  


简单来说就是，IaaS 就是原材料、PaaS 就是半加工品、SaaS 就是完成可用的产品。  


实际上，这些 `XaaS` 形式的服务十几年前就存在了。  
只是前几年虚拟化随着 Docker 技术的推广，人们突然发现云服务与云计算竟然这么好用，各种概念便被炒作起来了。  


-EOF-  
