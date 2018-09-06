---
title: 修改Ubuntu的aptget源为阿里源的方法
date: 2018-06-19 14:26:49
tags:
---

1、复制原文件备份

    sudo cp /etc/apt/source.list /etc/apt/source.list.bak

2、编辑源列表文件

    sudo vim /etc/apt/source.list

3、将原来的列表删除，添加如下内容


    deb http://mirrors.aliyun.com/ubuntu/ vivid main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ vivid-security main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ vivid-updates main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ vivid-proposed main restricted universe multiverse
    deb http://mirrors.aliyun.com/ubuntu/ vivid-backports main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ vivid main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ vivid-security main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ vivid-updates main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ vivid-proposed main restricted universe multiverse
    deb-src http://mirrors.aliyun.com/ubuntu/ vivid-backports main restricted universe multiverse

4、运行`sudo apt-get update`
5、运行`sudo apt-get upgrade`

