---
title: 6.2 DNS
type: docs
weight: 2
---

# 域名系统DNS

访问Web服务器（测试连通性命令：`ping`），经典的就是浏览器输入网址-得到网页的过程

Domain Name System, DNS 是一种命名系统，和IP地址对应，便于记忆

层次域名：一个DNS服务器显然装不下那么多的域名，所以是分层次的

## 域名命名规则

层次树状域名结构：低级在左，顶级在右

![image-20230625203753041](https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625203753041.png)

各级域名交由上一级的域名管理机构管理，最高的由`ICANN`管理

顶级域名`TLD`主要有三类：

- 国家地区：`.cn`, `.uk`, `.hk` 等等
- 通用顶级域名：`.com` 公司，`.org` 非盈利组织，`.gov`政府 等等
- 基础结构域名：只有一个`arpa`，用于反向域名解析，IP地址反向解析为域名

国家下面的就由国家自己管理，名称相等的等级未必相同

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230611192152640.png" alt="image-20230611192152640" style="zoom:67%;" />

## 域名服务器

服务器进行域名解析，一个服务器的管辖范围称之为`区`

- 根域名服务器：知道所有顶级域名服务器IP地址，因特网上有13“个”（实际是服务器集群），它不直接解析，而是返回所属顶级域名服务器的IP地址
- 顶级域名服务器：管理在其上注册的所有二级域名
- 权限域名服务器：管理某个区的域名，主机的域名在这里登记，这里有域名和IP地址的映射关系

![image-20230625205542454](https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625205542454.png)

`本地域名服务器`（默认）：本机的报文首先送往本地域名服务器，它起到代理的作用，将报文转发到上面等级结构中

## 域名解析过程

{{< columns >}} <!-- begin columns block -->
### 递归查询

![image-20230625210036246](https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625210036246.png)

<---> <!-- magic separator, between columns -->
### 迭代查询

![image-20230625210232448](https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625210232448.png)

{{< /columns >}}

一般是，主机以递归方式向本地服务器查询（因为之间可能也是有转发的），本地服务器以迭代方式向根服务器查询，服务器给出答案或者找答案的地方

同时，每个DNS服务器上有高速缓存，方便快速查找

DNS报文使用UDP服务
