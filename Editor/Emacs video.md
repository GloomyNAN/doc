---
title: Emacs 视频笔记
---

## 两小时10年linux emacs分享

* shell交互式补齐

![](media/15308446883555.jpg)


### pulgins

* clang auto-complate
![](media/15308489127005.jpg)

Ctrl+r
bing命令


## Spacemacs Rocks 第二季

### 第一集
[Learn X In Y Minutes](https://learnxinyminutes.com)


**补充**

major mode and minor mode
``

### 第二集

![](media/15308700557888.jpg)

**进入编辑模式，修改代码**

M-x eval-buffer 状态机生效

![packects扩充](media/15308708194275.jpg)


![](media/15308724094924.jpg)

<!--js2-mode-->
![](media/15308725417716.jpg)

函数 nodejs-repl-send-buffer代码发动到buffer运行

org剩余10分钟

### 第三集


```lisp
M-x global-auto-revert-mode ;;外部修改后自动重新加载配置文件
(setq auto-save-default nil);;自动保存禁止
```

**魔法注释**
`;;;###autoload`
`;;插件名-autoloads.el`是自动生成的，遍历插件陌路所有文件的魔法注释生成

![](media/15311065918200.jpg)

自定变量自动补全
![](media/15311068271696.jpg)
缩写+全称
lisp无namespace,vars全局可见

![](media/15311071540437.jpg)

```lisp
(add-to-list `load-path "~/.emacs.d/lisp");;环境变量路径增加
```

**minor mode or major mode**

![](media/15311139261360.jpg)

### 第四集

load-file 和 require

**dired mode**

![](media/15311202400113.jpg)
x 执行

删除和拷贝不询问
![](media/15311202753131.jpg)

![](media/15311203123182.jpg)

引入dired mode
`(requere `dired)`

**dired-x**

`(require `dired-x)

C-x C-z 打开当前文件所在buffer

`(require `dired-)
C-c 复制

open finder on Mac
Packages
reveal-in-osx-finder


### 第五集

emacs-lisp 不要补全单引号

```lisp
(sp-local-pair `emacs-lips-mode "'" nil :actions nil)
```

鼠标触碰代码中间高亮两侧括号
![](media/15311212653710.jpg)

1、隐藏doc换行符`^M`
![](media/15311214351828.jpg)

2、删除doc换行符`^M`
![](media/15311214821441.jpg)

**前端插件：web-mode**

缩进设置、两个空格和四个空格缩进的切换
![](media/15311217699842.jpg)


M-; 注释

**js2-refactor JS重构功能**
occur-mode 批量查询修改

![](media/15311226011797.jpg)

imenu 类似代码方法树状图，函数快捷跳转


![](media/15311227490900.jpg)
正则表达式查找代码


**expand-region**
键盘快速选中字符串
C-=/-

**iedit-mode**
同时编辑多个区域

### 第六集

抓取chrom链接
![](media/15311238939663.jpg)

org-mode 模板
![](media/15311239397162.jpg)

统一用户体验
![](media/15311241229430.jpg)

### 第七集

![镜像](media/15311250484111.jpg)
C-w

evil emacs2vim插件
windows-numbering 窗口快捷切换M-n 切换窗口
power-line
power-line-evil
evil-surround vi选中编辑
evil-nerd-commenter vi快捷键
which-key 快捷键提示插件
![](media/15311285526387.jpg)
快捷键右侧buffer提示

command-log
pallet + cask管理插件包
macro  宏
use-package

### space emacs

**buffer**
![](media/15312012446891.jpg)

![](media/15312013458628.jpg)


### others

插件

lispy vi-like Paredit
ctags 大型代码库索引自动补全
动态语言无法语义补全（lua/javascript）


elisp入门 叶文斌

![](media/15311316220717.jpg)

**blogs**
planet emacs
irrel emacs
abo abo emacs
chenbin emacs
emacs shacha
emacs sacha

<!--more-->

