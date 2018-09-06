---
title: 系统ping 命令time,TTL分析
date: 2018-06-19 14:26:49
tags:
---


## 1. PING (Packet Internet Grope)

因特网包探索器，用于测试网络连接量的程序。Ping发送一个ICMP回声请求消息给目的地并报告是否收到所希望的ICMP回声应答。


## 2. TTL：生存时间
　　
指定数据包被路由器丢弃之前允许通过的网段数量。
    
TTL 是由发送主机设置的，以防止数据包不断在 IP 互联网络上永不终止地循环。转发 IP 数据包时，要求路由器至少将 TTL 减小 1。

使用PING时涉及到的 ICMP 报文类型
一个为ICMR请求回显（ICMP Echo Request）

一个为ICMP回显应答（ICMP Echo Reply）
　　
TTL 字段值可以帮助我们识别操作系统类型。

UNIX 及类 UNIX 操作系统 ICMP 回显应答的 TTL 字段值为 255
Compaq Tru64 5.0 ICMP 回显应答的 TTL 字段值为 64
　　微软 Windows NT/2K操作系统 ICMP 回显应答的 TTL 字段值为 128
　　微软 Windows 95 操作系统 ICMP 回显应答的 TTL 字段值为 32
　　当然，返回的TTL值是相同的
　　但有些情况下有所特殊
　　LINUX Kernel 2.2.x & 2.4.x ICMP 回显应答的 TTL 字段值为 64
　　FreeBSD 4.1, 4.0, 3.4;
　　Sun Solaris 2.5.1, 2.6, 2.7, 2.8;
　　OpenBSD 2.6, 2.7,
　　NetBSD
　　HP UX 10.20
　　ICMP 回显应答的 TTL 字段值为 255
　　Windows 95/98/98SE
　　Windows ME
　　ICMP 回显应答的 TTL 字段值为 32
　　Windows NT4 WRKS
　　Windows NT4 Server
　　Windows 2000
　　Windows XP
　　ICMP 回显应答的 TTL 字段值为 128
　　这样，我们就可以通过这种方法来辨别操作系统

## 三，举例说明

C:\Documents and Settings>ping blog.51yip.com
Pinging blog.51yip.com [173.201.152.6] with 32 bytes of data:
Reply from 173.201.152.6: bytes=32 time=257ms TTL=45
Reply from 173.201.152.6: bytes=32 time=256ms TTL=45
Reply from 173.201.152.6: bytes=32 time=262ms TTL=45
Reply from 173.201.152.6: bytes=32 time=258ms TTL=45

Ping statistics for 173.201.152.6:
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 256ms, Maximum = 262ms, Average = 258ms

由此我们可以断定，blog.51yip.com是一台linux主机，经过了64-45=19次中转后到达本机，time=257ms，这个时间是一次请求的时间，这个时间越小，说明速度越快，越大说明速度越慢。

C:\Documents and Settings>ping 127.0.0.1

Pinging 127.0.0.1 with 32 bytes of data:
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128

Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 0ms, Average = 0ms
在这里的TTL=128是表示二个意思:

1,请求主机是一台WINDOWS系统的电脑
2,并且没有经过路由中转，也就是请求的是本机。每次请求的时间呢，小于百万份之一秒。


