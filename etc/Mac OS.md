---
title: MacOS
date: 2017-12-01 16:46:54
tags:
---

[记录装软件](https://7449.github.io/2017/07/04/mac-reloading/)
杀死dock&launchpad
    
    defaults write com.apple.dock ResetLaunchPad -bool true;killall Dock

任何来源命令
    
    sudo spctl --master-disable
显隐隐藏文件

    Command+Shift+.
    
在苹果电脑设置最新Android Studio的JDK路径时，需要将路径指向由系统自带的JDK6路径/
    
    System/Library/Java/JavaVirtualMachines/1.6.0.jdk/转为我们自己从ORICAL下载的最新JDK8安装路径。
JDK8以及JDK7安装的默认路径为：
    
    /Library/Java/JavaVirtualMachines/jdk1.8.0.jdk

```
Ctrl+p shell中上一个命令,或者 文本中移动到上一行
Ctrl+n shell中下一个命令,或者 文本中移动到下一行
Ctrl+r 往后搜索历史命令
Ctrl+s 往前搜索历史命令
Ctrl+f 光标前移
Ctrl+b 光标后退
Ctrl+a 到行首
Ctrl+e 到行尾
Ctrl+d 删除一个字符,删除一个字符，相当于通常的Delete键
Ctrl+h 退格删除一个字符,相当于通常的Backspace键
Ctrl+u 删除到行首
Ctrl+k 删除到行尾
Ctrl+l 类似 clear 命令效果
Ctrl+y 粘贴
```


最新版的 Mac 不需要额外的程序了，在 Finder 里按「⌘+shift+.」就能显示隐藏文件，再按一次隐藏掉。╮(￣▽￣")╭

大概是从 macOS Sierra 开始有这个功能的。

