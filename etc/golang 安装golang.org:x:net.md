---
title: golang 安装golang.org/x/net
---


下载安装golang.org/x/net其实网上有很多的文章，但总的归来是有两种：

为了使包的导入方式不变，我们需要在src目录下面构造目录结构

```
$mkdir -p $GOPATH/src/golang.org/x/
$cd $GOPATH/src/golang.org/x/
$git clone https://github.com/golang/net.git net
$go install net
```
执行go install之后没有提示，就说明安装好了。

