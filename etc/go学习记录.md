---
title: go学习记录
---

1. go get命令不成功，需要关闭git-ssh验证
2. brew安装添加环境变量

```bash
#GOROOT
export GOROOT=/usr/local/Cellar/go/1.10.3/libexec

#GOPATH bin
export PATH=$PATH:$GOPATH/bin

#GOPATH
export GOPATH=$HOME/go

#GOPATH root bin
export PATH=$PATH:$GOROOT/bin
```


