---
title: 第六章 应用层
type: docs
weight: 6
---

# 应用层

> 解决应用进程的交互来实现特定的网络应用的问题

这里就是学经典的网络应用及使用的应用协议

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230618211139158.png" alt="image-20230618211139158" style="zoom:57%;" />

## 网络应用模型

> 网络应用程序通过彼此的通信共同完成某项任务，于是，开发一种新的网络应用程序应该考虑其在各自端系统的组织方式和之间的关系

### 客观-服务器方式 C/S

描述服务和被服务的关系，客户请求，服务器提供服务：

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625195225087.png" alt="image-20230625195225087" style="zoom:60%;" />

### 对等方式 P2P

没有中心服务器，或者说每个主机同时是客户机和服务器，直接相互通信(任意一对叫`Peer`)

比如Bittorrent、电驴这些就是基于P2P的，下载速度快

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625195516950.png" alt="image-20230625195516950" style="zoom:60%;" />

服务分散在多个计算机中

获取服务的同时也提供服务

![image-20230611191119745](https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230611191119745.png)