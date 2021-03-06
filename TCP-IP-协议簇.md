---
title: TCP/IP 协议簇
date: 2016-03-05 15:11:33
tags: 网络
---


## 1. TCP/IP参考模型
TCP/IP参考模型是一个抽象的分层模型，这个模型中，所有的TCP/IP系列网络协议都被归类到4个抽象的"层"中。每一抽象层创建在低一层提供的服务上，并且为高一层提供服务。

完成一些特定的任务需要众多的协议协同工作，这些协议分布在参考模型的不同层中的，因此有时称它们为一个协议栈。 TCP/IP参考模型为TCP/IP协议栈订身制作。其中IP协议只关心如何使得数据能够跨越本地网络边界的问题，而不关心如何利用传输媒体，数据如何传输。整个TCP/IP协议栈则负责解决数据如何通过许许多多个点对点通路（一个点对点通路，也称为一"跳", 1 hop）顺利传输，由此不同的网络成员能够在许多"跳"的基础上创建相互的数据通路。

如想分析更普遍的网络通信问题，ISO的OSI模型也能起更好的帮助作用。

因特网协议族是一组实现支持因特网和大多数商业网络运行的协议栈的网络传输协议。它有时也被称为TCP/IP协议组，这个名称来源于其中两个最重要的协议：传输控制协议（TCP）和因特网协议（IP），它们也是最先定义的两个协议。 同许多其他协议一样网络传输协议也可以看作一个多层组合，每层解决数据传输中的一组问题并且向使用这些低层服务的高层提供定义好的服务。高层逻辑上与用户更为接近，所处理数据更为抽象，它们依赖于低层将数据转换成最终能够进行实体控制的形式。

网络传输协议能够大致匹配到一些厂商喜欢使用的固定7层的OSI模型。然而这些层并非都能够很好地与基于ip的网络对应（根据应用的设计和支持网络的不同它们确实是涉及到不同的层）并且一些人认为试图将因特网协议组对应到OSI会带来混淆而不是有所帮助。

## 2. 互联网控制消息协议 ICMP
网络控制消息协定（英文：Internet Control Message Protocol，ICMP）是网路协议族的核心协议之一。它用于TCP/IP网络中发送控制消息，提供可能发生在通信环境中的各种问题反馈，通过这些信息，令管理者可以对所发生的问题作出诊断，然后采取适当的措施解决。
ICMP依靠IP来完成它的任务，它是IP的主要部分。它与传输协议，如TCP和UDP显著不同：它一般不用于在两点间传输数据。它通常不由网络程序直接使用，除了ping和traceroute这两个特别的例子。 IPv4中的ICMP被称作ICMPv4，IPv6中的ICMP则被称作ICMPv6。

ICMP是在RFC 792中定义的互联网协议族之一。通常用于返回的错误信息或是分析路由。ICMP错误消息总是包括了源数据并返回给发送者。 ICMP错误消息的例子之一是TTL值过期。每个路由器在转发数据报的时候都会把IP包头中的TTL值减一。如果TTL值为0，“TTL在传输中过期”的消息将会回报给源地址。

每个ICMP消息都是直接封装在一个IP数据包中的，因此，和UDP一样，ICMP是不可靠的。


虽然ICMP是包含在IP数据包中的，但是对ICMP消息通常会特殊处理，会和一般IP数据包的处理不同，而不是作为IP的一个子协议来处理。在很多时候，需要去查看ICMP消息的内容，然后发送适当的错误消息到那个原来产生IP数据包的程序，即那个导致ICMP讯息被传送的IP数据包。


很多常用的工具是基于ICMP消息的。traceroute是通过发送包含有特殊的TTL的包，然后接收ICMP超时消息和目标不可达消息来实现的。ping则是用ICMP的"Echo request"（类别代码：8）和"Echo reply"（类别代码：0）消息来实现的。


## 3. TCP - 传输控制协议
TCP 用于从应用程序到网络的数据传输控制。
TCP 负责在数据传送之前将它们分割为IP包，然后在它们到达的时候将它们重组。
## 4. IP - 网际协议
IP 负责计算机之间的通信。
IP 负责在因特网上发送和接收数据包。



## 5. HTTP - 超文本传输协议
HTTP 负责 web 服务器与 web 浏览器之间的通信。
HTTP 用于从 web 客户端（浏览器）向 web 服务器发送请求，并从 web 服务器向 web 客户端返回内容（网页）。
## 6. HTTPS - 安全的 HTTP
HTTPS 负责在 web 服务器和 web 浏览器之间的安全通信。
作为有代表性的应用，HTTPS 会用于处理信用卡交易和其他的敏感数据。


## 7. SSL - 安全套接字层
SSL 协议用于为安全数据传输加密数据。
## 8. SMTP - 简易邮件传输协议
SMTP 用于电子邮件的传输。
## 9. MIME - 多用途因特网邮件扩展
MIME 协议使 SMTP 有能力通过TCP/IP网络传输多媒体文件，包括声音、视频和二进制数据。
## 10. IMAP - 因特网消息访问协议
IMAP 用于存储和取回电子邮件。

## 11. POP - 邮局协议
POP 用于从电子邮件服务器向个人电脑下载电子邮件。
## 12. FTP - 文件传输协议
FTP 负责计算机之间的文件传输。
## 13. NTP - 网络时间协议
NTP 用于在计算机之间同步时间（钟）。
## 14. DHCP - 动态主机配置协议
DHCP 用于向网络中的计算机分配动态 IP 地址。
## 15. SNMP - 简单网络管理协议
SNMP 用于计算机网络的管理。
## 16. LDAP - 轻量级的目录访问协议
LDAP 用于从因特网搜集关于用户和电子邮件地址的信息。
## 17. ICMP - 因特网消息控制协议
ICMP 负责网络中的错误处理。
## 18. ARP - Address Resolution Protocol
ARP - 用于通过 IP 来查找基于 IP 地址的计算机网卡的硬件地址。
## 19. RARP - Reverse Address Resolution Protocol
RARP 用于通过 IP 查找基于硬件地址的计算机网卡的 IP 地址。
## 20. BOOTP - Boot Protocol
BOOTP 用于从网络启动计算机。
## 21. PPTP - 点对点隧道协议
PPTP 用于私人网络之间的连接（隧道）。


## 22. Secure Shell - SSH
SSH为一项创建在应用层和传输层基础上的安全协议，为计算机上的Shell（壳层）提供安全的传输和使用环境。

SSH协议框架中最主要的部分是三个协议：

- 传输层协议（The Transport Layer Protocol）：传输层协议提供服务器认证，数据机密性，信息完整性等的支持。
- 用户认证协议（The User Authentication Protocol）：用户认证协议为服务器提供客户端的身份鉴别。
- 连接协议（The Connection Protocol）：连接协议将加密的信息隧道复用成若干个逻辑通道，提供给更高层的应用协议使用。
同时还有为许多高层的网络安全应用协议提供扩展的支持。
各种高层应用协议可以相对地独立于SSH基本体系之外，并依靠这个基本框架，通过连接协议使用SSH的安全机制。

## 23. DNS 域名系统
域名系统（英文：Domain Name System，缩写：DNS）是因特网的一项服务。它作为将域名和IP地址相互映射的一个分布式数据库，能够使人更方便地访问互联网。DNS使用TCP和UDP端口53。当前，对于每一级域名长度的限制是63个字符，域名总长度则不能超过253个字符。
DNS系统中，常见的资源记录类型有：

* 主机记录（A记录）：RFC1035定义，A记录是用于名称解析的重要记录，它将特定的主机名映射到对应主机的IP地址上。
* 别名记录（CNAME记录）:RFC1035定义，CNAME记录用于将某个别名指向到某个A记录上，这样就不需要再为某个新名字另外创建一条新的A记录。
* IPv6主机记录（AAAA记录）: RFC 3596定义，与A记录对应，用于将特定的主机名映射到一个主机的IPv6地址。
* 服务位置记录（SRV记录）: RFC 2782定义，用于定义提供特定服务的服务器的位置，如主机（hostname），端口（port number）等。
* NAPTR记录：RFC 3403定义，它提供了正则表达式方式去映射一个域名。NAPTR记录非常著名的一个应用是用于ENUM查询。
