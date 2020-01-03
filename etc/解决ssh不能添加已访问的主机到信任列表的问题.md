---
title: 解决ssh不能添加已访问的主机到信任列表的问题(Failed to add the host to the list of known hosts) .
---

https://www.awaimai.com/2203.html

在ssh访问一个服务器的时候第一次会提示签名验证，只要同意之后就会将这个host添加到~/.ssh中的known_hosts中，以后再连接就不会再出现提示了。
   原来在ubuntu和freebsd下都没有这个问题。在Gentoo中就有点问题。今天解决了一下，在gentoo-user的mail list中找到了答案。
正常的情况应该是这样的：

```
rory@gentoo ~ $ ssh xxx.xxx.com
The authenticity of host 'xxx.xxx.com (218.xxx.xxx.xxx)' can't be established.
RSA key fingerprint is 6e:6b:0f:2a:b8:91:3f:c8:f0:39:e4:df:b4:d8:16:6b.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'xxx.xxx.com,218.xxx.xxx.xxx' (RSA) to the list of known hosts.
rory@xxx.xxx.com's password:  
```
可是Gentoo中每次都出现:

```
rory@gentoo ~ $ ssh xxx.xxx.com
The authenticity of host 'xxx.xxx.com (218.xxx.xxx.xxx)' can't be established.
RSA key fingerprint is 6e:6b:0f:2a:b8:91:3f:c8:f0:39:e4:df:b4:d8:16:6b.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts
rory@xxx.xxx.com's password:  
```

根据这位作者的回复:http://www.mail-archive.com/gentoo-user@lists.gentoo.org/msg55719.html
可能是因为使用root用户来移动过home目录，应该修改一下.ssh的用户和权限

```
chown username: /home/username/.ssh  
chown username: /home/username/.ssh/*  
chmod 700 /home/username/.ssh  
chmod 600 /home/username.ssh/*  
```


```
<span style="font-size:18px;">chown username: /home/username/.ssh  
chown username: /home/username/.ssh/*  
chmod 700 /home/username/.ssh  
chmod 600 /home/username.ssh/*</span>  
```

可是我看我的`/home/rory/.ssh`目录的用户和组都是正常的。所以就是因为目录的权限不对。对照作者说的我的.ssh没有x权限。所以我执行了` chmod 700 /home/rory/.ssh `。这样一切就正常了。


