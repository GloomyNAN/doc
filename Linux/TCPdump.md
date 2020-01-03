---
title:  TCP dump
date: 2018-06-19 14:26:49
tags:
---

```shell
tcpdump -i eth0 -nnA port 80
```

```shell
tcpdump -s 0 -A 'tcp dst port 80 and (tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x504f5354)'
```

tcpdump -i 网卡  -A 以ASCII格式打印出所有分组，并将链路层的头最小化 -Ss 0 包的长度，0表示不限制  "port 端口 host域名 src 源域名 dst 目标域名" 

tcpdump -i eth0 -nnA port 80 host api.xiaoyinka.com

