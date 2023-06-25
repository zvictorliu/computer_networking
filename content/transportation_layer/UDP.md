---
title: UDP协议
type: docs
weight: 1
---

# UDP协议

适合一次性传输较少数据，虽然通信不可靠但是应用层还是有可靠性机制的

面向报文：不对传下来的应用层报文处理（而TCP会拆分），保留边界

> 应用层报文不可分割，是UDP数据报处理的最小单位

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230613221619827.png" alt="image-20230613221619827" style="zoom:50%;" />

UDP适合一次性传输少量数据、对可靠性要求不高的场景

## 报文格式

首部+数据：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230613221651943.png" alt="image-20230613221651943" style="zoom: 33%;" />

其中校验和可选，不用时全为0，用来检查是否出错

根据目的端口号找应用进程，找不到就丢弃，由`ICMP`发送不可达报文给发送端

## 校验

虽说可靠性机制在应用层，但校验还是UDP协议要做的，即宁差勿错

计算方法有点复杂。。。

