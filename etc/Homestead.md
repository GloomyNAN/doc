---
title: Homestead
date: 2017-12-01 16:46:54
tags:
---

```bash
# >3.0
Homestead 3以上思想，无全局安装，仅有项目安装，废弃init edit up等命令，拥抱vagrant原生命令

初始化
php vendor/bin/homestead make

# 添加环境变量
function homestead() {
    ( cd ~/Homestead && vagrant $* )
}
#≈2.0
Homestead ≈2.0，有许多命令，但是需要手动改php-fpm路径

#初始化
homestead init

#编辑配置
homestead edit

带配置文件重启
homestead up --provision

#口令记录

数据库
DB_DATABASE=homestead
DB_USERNAME=homestead
DB_PASSWORD=secret

想通过你主机上的Navicat或Sequel Pro连接MySQL或Postgres，你应该使用端口33060（MySQL）或54320（Postgres）来连接“127.0.0.1”。这两个数据库的用户名和密码都是“homestead” / “secret”。
```


**代码链接3306端口 因为代码是在虚拟机运行，母机采用33060**

链接记录

[vagrant](https://www.vagrantup.com/)
[homestead](https://github.com/laravel/homestead)
[laravle-homestead](https://docs.golaravel.com/docs/5.0/homestead/)
[virtualBox](https://www.virtualbox.org/)

[vagrant 添加本地 box 安装 laravel homestead](https://zhuanlan.zhihu.com/p/25338468)
[Homestead包升级](https://segmentfault.com/a/1190000011781490)
