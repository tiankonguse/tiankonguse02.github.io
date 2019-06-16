---
layout:     post
title:      性能调优
description: 很早之前收集的内容,现在放出来     
keywords: 后台服务
tags: [后台服务]
categories: [程序人生]
updateData:  23:52 2017/3/20
---
  
## 一、系统性能定义  
  
系统性能就是两个事:  
  
1. Throughput ，吞吐量。也就是每秒钟可以处理的请求数，任务数。  
2. Latency， 系统延迟。也就是系统在处理一个请求或一个任务时的延迟。  
  
* Throughput越大，Latency会越差。因为请求量过大，系统太繁忙，所以响应速度自然会低。  
*  Latency越好，能支持的Throughput就会越高。因为Latency短说明处理速度快，于是就可以处理更多的请求。  
  
## 二、系统性能测试  
  
我们知道要测试系统的性能，需要我们收集系统的Throughput和Latency这两个值。  
  
1. 首先，需要定义Latency这个值  
2. 其次，开发性能测试工具，一个工具用来制造高强度的Throughput，另一个工具用来测量Latency。  
3. 最后，开始性能测试。你需要不断地提升测试的Throughput，然后观察系统的负载情况，如果系统顶得住，那就观察Latency的值。这样，你就可以找到系统的最大负载，并且你可以知道系统的响应延时是多少。  
4. 关于Latency，如果吞吐量很少，这个值估计会非常稳定，当吞吐量越来越大时，系统的Latency会出现非常剧烈的抖动，所以，我们在测量Latency的时候，我们需要注意到Latency的分布，也就是说，有百分之几的在我们允许的范围，有百分之几的超出了，有百分之几的完全不可接受。也许，平均下来的Latency达标了，但是其中仅有50%的达到了我们可接受的范围。那也没有意义。  
5. 关于性能测试，我们还需要定义一个时间段。比如：在某个吞吐量上持续15分钟。因为当负载到达的时候，系统会变得不稳定，当过了一两分钟后，系统才会稳定。另外，也有可能是，你的系统在这个负载下前几分钟还表现正常，然后就不稳定了，甚至垮了。所以，需要这么一段时间。这个值，我们叫做峰值极限。  
6. 性能测试还需要做Soak Test，也就是在某个吞吐量下，系统可以持续跑一周甚至更长。这个值，我们叫做系统的正常运行的负载极限。  
  
## 三、定位性能瓶颈  
  
有了上面的铺垫，我们就可以测试到到系统的性能了，再调优之前，我们先来说说如何找到性能的瓶颈。  
  
### 1.查看操作系统负载  
  
首先，当我们系统有问题的时候，我们不要急于去调查我们代码，这个毫无意义。我们首要需要看的是操作系统的报告。看看操作系统的CPU利用率，看看内存使用率，看看操作系统的IO，还有网络的IO，网络链接数，等等。  
  
Linux下也有很多相关的命令和工具，比如：vmstat, sar, iostat, top, tcpdump等等 。通过观察这些数据，我们就可以知道我们的软件的性能基本上出在哪里。  
  
1）先看CPU利用率，如果CPU利用率不高，但是系统的Throughput和Latency上不去了，这说明我们的程序并没有忙于计算，而是忙于别的一些事，比如IO。  
2）然后，我们可以看一下IO大不大，IO和CPU一般是反着来的，CPU利用率高则IO不大，IO大则CPU就小。关于IO，我们要看三个事，一个是磁盘文件IO，一个是驱动程序的IO（如：网卡），一个是内存换页率。这三个事都会影响系统性能。  
3）然后，查看一下网络带宽使用情况，在Linux下，你可以使用iftop, iptraf, ntop, tcpdump这些命令来查看。  
  
4）如果CPU不高，IO不高，内存使用不高，网络带宽使用不高。但是系统的性能上不去。这说明你的程序有问题，比如，你的程序被阻塞了。可能是因为等那个锁，可能是因为等某个资源，或者是在切换上下文。  
  
通过了解操作系统的性能，我们才知道性能的问题，比如：带宽不够，内存不够，TCP缓冲区不够，等等，很多时候，不需要调整程序的，只需要调整一下硬件或操作系统的配置就可以了。  
  
### 2.使用Profiler测试  
  
接下来，我们需要使用性能检测工具，也就是使用某个Profiler来差看一下我们程序的运行性能  
  
使用这些Profiler工具，可以让你程序中各个模块函数甚至指令的很多东西，如：运行的时间 ，调用的次数，CPU的利用率，等等。这些东西对我们来说非常有用。  
  
  
我们重点观察运行时间最多，调用次数最多的那些函数和指令。这里注意一下，对于调用次数多但是时间很短的函数，你可能只需要轻微优化一下，你的性能就上去了  
  
使用Profiler有个问题我们需要注意一下，因为Profiler会让你的程序运行的性能变低.  
  
## 四、常见的系统瓶颈  
  
一般来说，性能优化也就是下面的几个策略：  
  
1. 用空间换时间。各种cache如CPU L1/L2/RAM到硬盘，都是用空间来换时间的策略。这样策略基本上是把计算的过程一步一步的保存或缓存下来，这样就不用每次用的时候都要再计算一遍，比如数据缓冲，CDN，等。这样的策略还表现为冗余数据，比如数据镜象，负载均衡什么的。    
2. 用时间换空间。有时候，少量的空间可能性能会更好，比如网络传输，如果有一些压缩数据的算法，这样的算法其实很耗时，但是因为瓶颈在网络传输，所以用时间来换空间反而能省时间。    
3. 简化代码。最高效的程序就是不执行任何代码的程序，所以，代码越少性能就越高。    
4. 并行处理。    
  
总之，根据2：8原则来说，20%的代码耗了你80%的性能，找到那20%的代码，你就可以优化那80%的性能。   
  
  
### 1.算法调优  
  
算法非常重要，好的算法会有更好的性能。  
  
### 2.代码调优  
  
1. 字符串操作（遍历与copy）    
2. 多线程调优（锁）    
3. 内存分配（内存申请释放，内存碎片）    
4. 异步操作 通常来说，异步操作会让性能的吞吐率有很大提升（Throughput），但是会牺牲系统的响应时间（latency）。    
5. 语言和代码库。我们要熟悉语言以及所使用的函数库或类库的性能。    
  
### 3.网络调优    
  
* TCP调优  
  
KeepAlive, 短连接与长连接, TIME_WAIT, RWIN  
  
```  
net.ipv4.tcp_tw_reuse=1  
net.ipv4.tcp_tw_recycle=1  
```  
如果网络质量非常好，基本不丢包，而业务上我们不怕偶尔丢几个包，那为什么不使用UDP呢？  
  
* UDP调优  
  
MTU, multi-cast多播  
  
* 网卡调优  
  
txqueuelen的尺寸, 网卡的缓冲区大小  
  
* 其它网络性能  
  
多路复用技术使用epoll, DNS Lookup的系统调用要小心.  
  
### 4.系统调优  
  
1. I/O模型  
2. 多核CPU调优 CPU0是很关键的 NUMA  
3. 文件系统调优  
4. 数据库调优  
5. 查看汇编代码  



