---
title: SSH
date: 2018-06-19 14:26:49
tags:
---

```
# 开启调试模式
ssh -vvT git@yourhost
```

用/etc/init.d/sshd restart
1. ps -ef|grep ssh
若只有ssh-agent ,则ssh-server 没有启动
2. 启动ssh
/etc/init.d/sshd start
若看到ssh.d 表示ssh server 已经启动

3. config
/etc/ssh/sshd_config
default is 22 #可以改成2222
/etc/init.d/sshd restart 

**更改密码**



# 命令行怎么重启ssh

    用/etc/init.d/sshd restart
    1） ps -ef|grep ssh
    若只有ssh-agent ,则ssh-server 没有启动
    2) 启动ssh
    /etc/init.d/sshd start
    若看到ssh.d 表示ssh server 已经启动
    3） config
    /etc/ssh/sshd_config
    default is 22
    可以改成2222
    /etc/init.d/sshd restart 


修改SSH-keygen密码

    ssh-keygen -p


