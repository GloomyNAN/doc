---
title: 【转】htaccess语法之RewriteCond与RewriteRule指令格式详细解释
date: 2015-07-19
---

　　转发一篇技术文档，最近将公司的服务器调整了一下配置了web负载均衡，原来的思路是开443端口然后绑定ssl证书，用Apache自带的rewrite来做跳转，实现全站https，但是后来发现还是不方便，在流量暴增的情况下，一台服务器再强大肯定有宕机的风险，所以配置web负载均衡，随时用镜像建立服务器做内网轮训策略，后来将ssl证书绑定到负载均衡上，实现服务器只开启80端口，用负载均衡绑定的证书来监听80端口做转发，以前写的rewrite规则就会报循环过多，而且机器随时增加的情况下，后端设置过多，负载均衡绑定证书设置一次就好，查了资料现在亲测好用，所以留个记录；

>原后端绑定https，.htaccess文件内容


```
IfModule mod_rewrite.c>
　　Options +FollowSymLinks
　　IndexIgnore */*
　　RewriteEngine on
　　#将不带www的主域名跳转到带www的根域名上
　　#RewriteCond %{HTTP_HOST} ^webanking.com [NC]
　　#RewriteRule ^(.*)$ https://www.webanking.com/$1 [L,R=301]
　　#强制 HTTPS
　　#RewriteCond %{HTTPS} !=on
　　#RewriteRule ^(.*) https://%{SERVER_NAME}/$1 [L,R]
　　# if a directory or a file exists, use it directly
　　RewriteCond %{REQUEST_FILENAME} !-f
　　RewriteCond %{REQUEST_FILENAME} !-d
　　# otherwise forward it to index.php
　　RewriteRule . index.php
　　</IfModule>
```


>现在web负载均衡绑定证书，.htaccess文件内容

```conf
　<IfModule mod_rewrite.c>
　　Options +FollowSymLinks
　　IndexIgnore */*
　　RewriteEngine on
　　#RewriteRule ^(.*) https://%{SERVER_NAME}/$1 [L,R]
　　# if a directory or a file exists, use it directly
　　RewriteCond %{REQUEST_FILENAME} !-f
　　RewriteCond %{REQUEST_FILENAME} !-d
　　# otherwise forward it to index.php
　　RewriteRule . index.php
　　#强制 HTTPS 通过代理
　　RewriteCond %{HTTP:X-Forwarded-Proto} !https
　　RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
　　#判断端口
　　#RewriteCond %{SERVER_PORT} 80
　　# RewriteRule ^(.*)$ https://%{SERVER_NAME}/$1 [L,R]
　　</IfModule>
```

　　上文htaccess语法详细解释与用例分析中对RewriteCond和RewriteRule的用法进行了举例分析，本文将详细描述上述两个命令的使用格式，与所使用的变量和规则。这篇文章很长啊哈，请认真阅读，内容都很有用哦。
　　
　　　RewriteCond指令格式

　　【说明】定义重写发生的条件

　　【语法】RewriteCond TestString CondPattern [flags]

　　RewriteCond指令定义一条规则条件。在一条RewriteRule指令前面可能会有一条或多条RewriteCond指令，只有当RewriteCond的条件(CondPattern)匹配成功时，RewriteRule的重写规则才被应用于当前URL处理。

　　TestString是一个纯文本的字符串，除了包含普通的字符外，还可以包括下列的变量结构扩展：

　　RewriteMap扩展：引用方法是：${mapname:key|default} 细节请参见RewriteMap指令 。

　　TestString可以包含服务器变量 ，引用方法是：%{NAME_OF_VARIABLE}

　　NAME_OF_VARIABLE可以是下表列出的字符串之一：


