---
title: 服务器 SSH KEY 无效的问题
date: 2018-06-19 14:26:49
tags:
---

使用GitLab或者Gogs突然SSH无效问题解决

>git push，git pull 的时候，却提示验证失败。无法识别SSH KEY，尝试过删除了，然后重新添加SSH KEY也不行。


原因：是因为.ssh目录没有ssh_home_t标签！！

解决：

1. 检查目录`ls -laZ .ssh`
2. 重置标签`restorecon -r -vv .ssh`
3. 修改相关目录权限：

>文件~/.ssh/authorized_keys的权限必须为600，目录~/.ssh/权限为700，用户家目录权限也必须是700，否者信任会失效。

参考
[一次由SELinux引起的ssh公钥认证失败问题](https://www.linuxidc.com/Linux/2013-07/87267.htm)
[建立Linux ssh信任及常见问题解决办法](https://www.linuxidc.com/Linux/2015-02/113622.htm)
[GitLab 迁移服务器后 SSH KEY 无效的问题](https://www.linuxidc.com/Linux/2017-04/143072.htm)


