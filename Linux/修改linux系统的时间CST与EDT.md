---
title: 修改linux系统的时间CST与EDT
date: 2018-06-19 14:26:49
tags:
---


初始时间：2012年 09月 14日 星期五 18:15:33 EDT

```
[root@test ~]# mv /etc/localtime /etc/localtime.bak
[root@test ~]# ln -s /usr/share/zoneinfo/Asia/Shanghai  /etc/localtime
[root@test ~]# date
```
修改后的时间：
2012年 09月 15日 星期六 18:25:00 CST


```
tzselect
```

