---
title: Emacs
date: 2018-06-19 14:26:49
tags: emacs
---

## 快捷键


```bash
Ctrl+p shell 中上一个命令，或者文本中移动到上一行
Ctrl+n shell 中下一个命令，或者文本中移动到下一行
Ctrl+r 往后搜索历史命令
Ctrl+s 往前搜索历史命令
Ctrl+f 光标前移
Ctrl+b 光标后退
Ctrl+a 到行首
Ctrl+e 到行尾
Ctrl+d 删除一个字符，删除一个字符，相当于通常的 Delete 键
Ctrl+h 退格删除一个字符，相当于通常的 Backspace 键
Ctrl+u 删除到行首
Ctrl+k 删除到行尾
Ctrl+l 类似 clear 命令效果
Ctrl+y 粘贴
M-x lisp-interaction-mode //切换到lisp解释器模式
C-x C-e //执行lisp程序to Minibuffer
C-h f  //查看帮助
C-h k  //关闭buffer
C-g //退出当前命令
C-x n //分屏 1/0 关闭其他 2下 3 右
emacs -nw //终端模式打开emacs
C-h t//进入新手教程
/sudo::/path //提权编辑
切换buffer  "C-x <left>" 和 "C-x <right>"
cC-x C-f     按提示输入文件名，如果文件不存在则新建文件，如果文件存在则打开文件
C-x C-s    保存
C-x C-w    按提示输入文件名，另存为
M-x customize-variable 回车 make-backup-files 回车     关掉文件备份
M-s ： 新建一个buffer（缓冲区） 
C-x O ： 注意是大写的O，不是零，所以需要按住shift键再按o键。用于在缓冲区之间切换 
C-g ： 取消当前操作 
C-x u ： 回到上一步，相当于Undo 
C-x 3 ： 把缓冲区（buffer）分为左右两个，新的一个缓冲区是复制当前的缓冲区 （可以执行多次，来分割出很多小窗口） 
C-x 2 ： 把缓冲区（buffer）分为上下两个，新的一个缓冲区是复制当前的缓冲区 （可以执行多次，来分割出很多小窗口） 
M-w ： 选中文字的情况是复制文字，而如果没有选中文字则是复制当前的一行 
C-w ： 选中文字的情况是剪切文字，而如果没有选中文字则是剪切当前的一行 
M-x ： 调出命令输入，可以在后面接命令，比如man，svn-status，等 
C-y ： 黏贴
C-x C-s ： 保存文本 
C-x C-f ： 打开文件，如果文件不存在，则新建文件 
C-x C-v ： 打开一个文件，取代当前缓冲区 
C-x k ： 关闭当前缓冲区（buffer） 
C-s ： 向前搜索 
C-r ： 向后搜索 
C-x h ： 全选 
C-v ： 向下翻页 
M-v ： 向上翻页 
C-f ： 前进一个字符 
C-b ： 后退一个字符 
M-f ： 前进一个单词 
M-b ： 后退一个单词 
C-@ ： 标记开始区域 
C-a ： 移到行首 
C-e ： 移到行尾 
M-a ： 移到句首 
M-e ： 移到句尾 
M-< ： 缓冲区头部 
M-> ： 缓冲区尾部 M-g M-g，再输入数字 ： 跳转到文本的第几行 C-x 0 ： 关闭当前缓冲区 
C-x C-c ： 退出Emacs
#切换buffer    
C-x b /C-x C-b
# 退出  
C-x C-c #会问你是否保存。
# 野蛮点的方法，调用函数kill-emacs，即M-x kill-emacs，直接退出，不管是否修改。
#不过直接退出后，Emacs会在相同目录下保留一个以#号开头结尾的相同文件名文件，下次启动可以使用M-x recover-file来恢复。如果是多次保存后，还会有个以~结尾的文件，保存了上次信息。
```

```lisp
Emacs在保存时就会运行write-file-hooks中的time-stamp, 从而加 入修改时间, 结果类似下面所示
Time-stamp: 
或者
Time-stamp: "jerry 12/17/2003 12:00:54 (unidevel.com)"
   
要使用中文表示, 可以这样设置
(setq time-stamp-start "最后更新时间:[     ]+\\\\?")
(setq time-stamp-end: "\n")
(setq time-stamp-format: "%:y年%:m月%:d日")
   
上面设置了如果碰到"最后更新时间:"的字样, time-stamp就将其后 面的字符替换为当前时间的"XXXX年XX月XX日", 注意, time-stamp-end的结束符 为换行符, 所以"最后更新时间:"行后所有字符都将无条件被替换为"XXXX年XX月XX日" 格式的时间, 本文首页上的更新时间就是这样做出来的

(fset 'yes-or-no-p 'y-or-n-p)
(display-time)
(setq visible-bell t) ; remove beeping
(column-number-mode t)
(transient-mark-mode t) ; high light copy area
(show-paren-mode t) ;匹配的括号
;为什么使用语法显示的大文件在移动时如此之慢
(setq lazy-lock-defer-on-scrolling t)
(setq font-lock-support-mode 'lazy-lock-mode)
(setq font-lock-maximum-decoration t)

;不要那个如此大的工具条
(tool-bar-mode -1)

;在mozilla, openoffice等拷贝的中文文字无法正确粘贴在Emacs中(Emacs 21.3 发布版有此问题, 至少在我的FreeBSD下是这样的)
(set-clipboard-coding-system 'ctext)
   
;启动Emacs报错, ~/.emacs中有问题, 如何忽略错误
 (condition-case err
     (progn
     (require 'xxx) )
   (error
    (message "Can't load xxx-mode %s" (cdr err))))
   
;如上所示, 可以截获progn内部出错, 在mini-buffer下打出错误信息
;不要生成临时文件
(setq-default make-backup-files nil)
```

![Emacs基本操作-w1000](media/14963272150143/Emacs%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C.png)
Emacs Tutorial
![e-nav](media/14963272150143/e-nav.png)

