---
title:  Pod
date: 2018-06-19 14:26:49
tags:
---


```
# 安装
$ sudo gem install cocoapods

# CocoaPods 会将第三方的podspec索引文件更新到本地的~/.cocoapods/repos目录下
$ pod setup
sudo gem update --system

gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/
gem sources -l

```


## 常见问题

> pod报错:Automatically assigning platform `ios` with version `10.0` on target `CloudLive` because no pl

解决：指定平台版本

>使用cocoapods导入第三方类库后头文件没有代码提示？

解决办法： 选择`Target -> Build Settings`菜单，找到`User Header Search Paths`设置项，新增一个值`${SRCROOT}`，并且选择`Recursive`

## 附：资料

[CSDN教学](https://blog.csdn.net/jiankeufo/article/details/79362660)
[CocoaPods 的安装以及一些常见安装错误解决办法
](https://blog.csdn.net/wyz670083956/article/details/51537632)


