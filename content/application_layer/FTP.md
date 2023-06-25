---
title: 6.3 FTP
type: docs
weight: 3
---

# 文件传输协议FTP

屏蔽了计算机的细节

交互式访问：指明文件的类型与格式，并有权限

仍是C/S模式：FTP客户可将文件上传至FTP服务器，客户也可从中下载 ，普通的PC也可以作为服务器

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625213213757.png" alt="image-20230625213213757" style="zoom:67%;" />

## 工作原理

客户向服务 器建立两个并行的TCP连接：

- 控制连接：客户用临时端口-服务器21号端口，传送控制命令
- 数据连接：另一个临时端口-服务器20号端口（主动模式才是），进行文件传送

<img src="https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625213621767.png" alt="image-20230625213621767" style="zoom:67%;" />

控制连接在会话期间一直保持打开，而数据连接只有需要文件传输时才建立，传输完就关闭

服务器上主进程负责接收请求，子进程负责处理单个请求

控制进程接到请求后创建数据传送进程和数据连接

两种数据传输模式：

- 主动模式：PORT
  - 客户端和服务器连接后，客户端自己开发一个端口，将端口号和PORT命令发送给服务器，服务器于是将20号端口和这个端口建立数据连接
- 被动模式：PASV
  - 服务器收到PASV命令后，随机开放一个端口并告知客户端，客户端与之建立数据连接

![image-20230625214033509](https://cdn.jsdelivr.net/gh/zvictorliu/typoraPics@main/img/image-20230625214033509.png)

FTP修改文件：先下载下来，修改后再传上去

网络文件系统NFS：能够远程操控，只复制一个小片段回来修改然后安装上去
