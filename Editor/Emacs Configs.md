---
title:  Emacs Configs
---


setq 当前buffer
setq-default 全局buffer值

```lisp
(load-theme `mokial-theme t) ;;启动皮肤
(add-hook 'emacs-list-mode-hook 'show-paren-mode) ;; 高亮对应括号
(blobal-hl-line-mode t);;显示当前行
(setq inhibit-startup-message t) ;关闭启动画面

(setq column-number-mode t) ;显示列号
;;; 括号匹配时显示另一个括号而不是跳到另一个括号

(show-paren-mode t)
(setq show-paren-style 'parentheses)
(setq frame-title-format "%b %I") ;显示文件名和大小

(auto-image-file-mode t) ;让Emacs可以直接打开、显示图片
(fset 'yes-or-no-p 'y-or-n-p) ;以Y/N代表yes/no
(setq auto-save-default nil) ;不生成名为#filename#的临时文件
(setq x-select-enable-clipboard t) ;支持和外部程序的拷贝
(global-font-lock-mode t) ;打开语法高亮
(electirc-indent-mode t) ;;自动缩进
注释用两个引号

(delete-selection-mode t) ;;delete键

```


![emacs配置](media/15308694159471.jpg)

<!--more-->
