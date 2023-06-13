---
title: UDP协议
type: docs
weight: 1
---

# UDP协议

适合一次性传输较少数据，虽然通信不可靠但是应用层还是有可靠性机制的

面向报文？？？

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230613221619827.png" alt="image-20230613221619827" style="zoom:50%;" />

## 报文格式

首部+数据：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230613221651943.png" alt="image-20230613221651943" style="zoom:50%;" />

其中校验和可选，不用时全为0，用来检查是否出错

根据目的端口号找应用进程，找不到就丢弃，有`ICMP`发送不可达报文给发送端

## 校验

增加一个12B的伪首部到首部前，然后进行计算：

这个计算过程有点不太好说清楚

发送端：

- 计算要填入校验和的内容：全设置为0，然后把每16位取反码求和...
- 发送（不包括伪首部和补零）

接收段：

- 加上伪首部，同样计算求和，正常的话应该全为1

