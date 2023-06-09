---
title: 第二章 物理层
type: docs
weight: 2
---

# 物理层

首先需要明确物理层并不是真的物理实体（传输线），它是**考虑如何传输比特流**的一层

它为数据链路层屏蔽了不同介质的差异

## 物理层任务

- 机械上：规定物理连接的接口规格、引线数量等等
- 电气上：规定电压范围、速率等等
- 功能上：规定某一电平代表上面含义
- 过程上：规定工作时序等等

## 物理层设备

### 中继器

由于信号会逐渐衰减，所以需要中继器进行放大，专业叫再生和还原

### 集线器

就是多口中继器

## 数据交换

交换设备存在的意义就相当于云，不必每两台设备之间都建立一条通路，只需要向交换中心建立通路

交换设备具有信号集中、分发的功能

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230610164829828.png" alt="image-20230610164829828" style="zoom:50%;" />

可以通过电路交换，也可以是存储-转发方式，分为报文交换和分组交换

分组交换又可分为数据报方式和虚电路方式

