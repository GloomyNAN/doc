---
title: Docker
date: 2017-12-01 16:46:54
tags:
---

1. 安装

```
brew cask install docker
```

### 命令记录

```bash
# 查看信息
docker info

# 查看版本信息
docker --version

# 下载镜像
docker pull

# 查找镜像
docker search

#更改镜像
docker commit -m="message" -a="autor" ID runoob/ubuntu:v2(name)

#查看镜像
docker images 

# 构建镜像
 docker build
 
 # 启动
 #  -d:让容器在后台运行。
 # -P:将容器内部使用的网络端口映射到我们使用的主机上。
 # docker run -d -P training/webapp python app.py
 docker run 
```


### 国内镜像

网易加速器：http://hub-mirror.c.163.com

官方中国加速器：https://registry.docker-cn.com

ustc的镜像：https://docker.mirrors.ustc.edu.cn

[daocloud：https://www.daocloud.io/mirror#accelerator-doc](https://www.daocloud.io/mirror#accelerator-doc)（注册后使用）

### 资源

[阮一峰-Docker 入门教程](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
[阮一峰-Docker 微服务教程](http://www.ruanyifeng.com/blog/2018/02/docker-wordpress-tutorial.html)

### 其他软件

* Docker Compose
* Docker Swarm

