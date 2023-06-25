---
title: 第五章 传输层
type: docs
weight: 5
---

# 传输层

> 面向通信的最高层，面向用户功能的最底层

物理层-数据链路层-网络层实现【主机到主机】的连接

但是通信实体是进程（多种应用都有通信需求），这叫端到端连接

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625184417324.png" alt="image-20230625184417324" style="zoom:80%;" />

通过端口区分不同应用：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625184632572.png" alt="image-20230625184632572" style="zoom:60%;" />

根据需求的不同提供了两种不同协议：TCP UDP

## 端口号

在操作系统中是PID区分进程，但是网络中的主机并不是使用相同的操作系统，于是有了在网络中的统一标识规则：端口号

端口号用16bit表示，分为几种：

- 服务器端：
  - 熟知端口号：{{<katex>}}0 \sim 2^{10}-1{{</katex>}}，分给最重要的一些应用
    - 比如 FTP(21/20) ，HTTP(80)，DNS(53)，SCP(22) 这些应用协议程序都有固定的端口号
  - 登记端口号：{{<katex>}}2^{10} \sim 49151{{</katex>}}
    - 供给没有熟知端口号的特定进程，需要在`IANA`登记

- 客户端：
  - 短暂端口号：{{<katex>}}49151 \sim 2^{16}-1{{</katex>}}
    - 客户进程运行时才动态选择，是临时的，通信结束被释放，并<u>不专属于某个程序</u>

端口号用以区分主机内的不同进程，它是本地的，而IP地址区分不同主机

套接字`Socket`就是IP地址+端口号，表示哪台主机上的哪个进程，如果只有端口号只能是本地主机上的哪个进程

A向B通信时也是把自己的源端口号一起发过去的，这样B才能发送回A

## 复用和分用概念

发送方复用：指的是使用同样的封装

接收方分用：同样的封装但是含义不同

比如最后都是打包成IP数据报，这叫复用，但是运输层的协议可能是TCP也可能是UDP，能进行区分（有协议字段），这叫分用

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625190238008.png" alt="image-20230625190238008" style="zoom:67%;" />



{{< details title="应用层常见协议所用的运输层协议和熟知端口号" open=false >}}
<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625190410787.png" alt="image-20230625190410787" style="zoom:67%;" />
协议字段区分是TCP还是UDP，端口号区分是哪个应用
{{< /details >}}

## TCP与UDP对比

`TCP/IP`协议族中：

- TCP：面向连接，需要三次握手才能通信
  - 开销比较大
- UDP：无连接，随时通信
  - 收到报文后无需返回确认信息

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625191628727.png" alt="image-20230625191628727" style="zoom: 50%;" />

UDP支持单播、多播和广播，而TCP只能单播（一对一）

UDP不对应用层报文处理，仅加上UDP头部，而TCP则是将其看成字节流

 <img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625192000099.png" alt="image-20230625192000099" style="zoom:50%;" />

 

UDP对应用层来说仍是提供的不可靠传输，而TCP是确保了可靠传输

