---
title: Org-mode
date: 2018-06-19 14:26:49
tags: [emacs,org]
---

[Org入门](https://www.cnblogs.com/qlwy/archive/2012/06/15/2551034.html#sec-4-4)
[ErgoEmacs](http://ergoemacs.org/)

```
M-RET 插入同级列表
```

快捷键	说明
S-TAB	循环切换整个文档的大纲状态（折叠、打开下一级、打开全部）
TAB	循环切换光标所在的大纲状态
大纲或者列表之间移动
快捷键	说明
C-c C-n/p	移动到下上一个标题（不断标题是哪一级）
C-c C-f/b	移动到同一级别的下/上标题
C-c C-u	跳到上一级标题
C-c C-j	切换到大纲预览状态
基于大纲/标题的编辑
快捷键	说明
M-RET	插入一个同级别的标题
M-S-RET	插入一个同级别的TODO标题
M-LEFT/RIGHT	将当前标题升/降级
M-S-LEFT/RIGHT	将子树升/降级
M-S-UP/DOWN	将子树上/下移动
C-c *	将本行设为标题或者正文
C-c C-w	将子树或者区域移动到另一个标题处（跨缓冲区）
C-c C-x b	在新缓冲区显示当前分支
C-c /	只列出包含搜索结果的大纲，并高亮，支持多种搜索方式

```org
#+BEGIN_SRC emacs-lisp
(setq make-backip-files nil)
#+END_SRC
```

C-c ' 打开buffer(emacs lisp)/返回
C-c C-k退出

```lisp
; org-mode语法高亮配置
(require 'org)
(setq org-src-fontify-natively t)

<+s+tab = ;;插入源代码
#+BEGIN_SRC
#+END_SRC
```
M-return 自动补全

## 归档操作

**内部归档**
打上ACHIVED标签或者移动到名为achived的子树中去并打上标签

`C-c C-x a`将某一个节点打上ARCHIVE标签。
`C-c C-x a`将当前节点归入一个名为Archive的子树中，并且这个子树是位于当前级别子树的最下方。

**外部归档**
外部归档是指把子树移动到另一个org文件中去。文件名可以自定义。默认情况下，归档的子树会被移动到名为“当年文件名_archived”的文件中去
`C-c C-x C-s`是把当前的节点移到archived文件中去

## todo

```lisp
C-c C-s ;; 设定开始时间
C-c C-d;;设定结束时间
C-c a +a ;;列表
d回到当前

; 文学编程
(require 'org-install)
(require 'ob-tangle)
(org-babel-load-file (expand-file-name "XXXX" user-enamcs-directory))

; 记笔记
(setq org-capture-templates
    '(("t" "Todo" entry (fileheadline "~/.emacs.d/gtd.org" "工作安排")
    "* TODO [#B] %?\n %i\n"
    :empty-lines 1)
    ("c" "Chrome" entry (fileheadline "~/.emacs.d/notes.org" "Quick notes")
      "* TODO [#C] %?\n %(XXX/retrieve-chrome-current-tab-url)\n %i\n %U"
      :empty-lines 1)
      ))
)
```

