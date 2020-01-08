---
title:  Emacs Configs
---

## kbd

```lisp
C-s b ;;切换buffer
C-x b /C-x C-b;切换buffer
M-x customize-group ;;定制配置
C-x C-e ;;scratch模式，执行lisp代码
M-n M-p;;选取补全内容
C-x r C-h ;列出所有C-x r前缀的命令
C-h C-h  ;给出帮助相关命令
M-x lisp-interaction-mode ;切换到lisp解释器模式
C-x C-e ;执行lisp程序to Minibuffer
C-x n ;分屏 1/0 关闭其他 2下 3 右
emacs -nw ;终端模式打开emacs
/sudo::/path ;提权编辑
;切换buffer  "C-x <left>" 和 "C-x <right>"
C-x C-w   ; 按提示输入文件名，另存为
M-x customize-variable 回;车 make-backup-files 回车     关掉文件备份
M-s ： ;新建一个buffer（缓冲区） 
C-x 3 ： ;把缓冲区（buffer）分为左右两个，新的一个缓冲区是复制当前的缓冲区 （可以执行多次，来分割出很多小窗口） 
C-x 2 ： ;把缓冲区（buffer）分为上下两个，新的一个缓冲区是复制当前的缓冲区 （可以执行多次，来分割出很多小窗口） 
M-w ： ;选中文字的情况是复制文字，而如果没有选中文字则是复制当前的一行 
C-w ： ;选中文字的情况是剪切文字，而如果没有选中文字则是剪切当前的一行 
M-x ： ;调出命令输入，可以在后面接命令，比如man，svn-status，等 
C-x C-v ：; 打开一个文件，取代当前缓冲区 
C-x k ： ;关闭当前缓冲区（buffer） 
C-x h ： ;全选 
C-@ ： ;标记开始区域 
C-x 5 2 ;新建frame
C-x 50  ;关闭frame 
M-> ： ;缓冲区尾部 M-g M-g，再输入数字 ： 跳转到文本的第几行 
C-x 0 ： ;关闭当前缓冲区 
; 野蛮点的方法，调用函数kill-emacs，即M-x kill-emacs，直接退出，不管是否修改。
;不过直接退出后，Emacs会在相同目录下保留一个以#号开头结尾的相同文件名文件，下次启动可以使用M-x recover-file来恢复。如果是多次保存后，还会有个以~结尾的文件，保存了上次信息。
;shell可以 M-x shell 或者 M-x term 进入 Shell.

;;Emacs在保存时就会运行write-file-hooks中的time-stamp, 从而加 入修改时间, 结果类似下面所示
;;Time-stamp: 
;;或者
;;Time-stamp: "jerry 12/17/2003 12:00:54 (unidevel.com)"
   
;要使用中文表示, 可以这样设置
(setq time-stamp-start "最后更新时间:[     ]+\\\\?")
(setq time-stamp-end: "\n")
(setq time-stamp-format: "%:y年%:m月%:d日")
;;上面设置了如果碰到"最后更新时间:"的字样, time-stamp就将其后 面的字符替换为当前时间的"XXXX年XX月XX日", 注意, time-stamp-end的结束符 为换行符, 所以"最后更新时间:"行后所有字符都将无条件被替换为"XXXX年XX月XX日" 格式的时间, 本文首页上的更新时间就是这样做出来的
   
;启动Emacs报错, ~/.emacs中有问题, 如何忽略错误
 (condition-case err
     (progn
     (require 'xxx) )
   (error
    (message "Can't load xxx-mode %s" (cdr err))))
   
;如上所示, 可以截获progn内部出错, 在mini-buffer下打出错误信息
```

![Emacs基本操作-w1000](media/14963272150143/Emacs%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C.png)

![e-nav](media/14963272150143/e-nav.png)

## urls

[MetaKeyProblems](https://www.emacswiki.org/emacs/MetaKeyProblems)
[王垠笔记](https://docs.huihoo.com/homepage/shredderyin/emacs.html)
[emacs wiki](https://www.emacswiki.org)
[The very unofficial dotemacs home](http://dotemacs.de)
[Emacs Lisp 简明教程](http://smacs.github.io/elisp/)
[Emacs China](https://emacs-china.org)
[解决Mac下emacs中alt键不能使用问题](https://www.jianshu.com/p/7432c3bfcc99)


### blogs

[planet emacs](https://planet.emacslife.com/)
[irrel emacs]()
abo abo emacs
[chenbin emacs](http://blog.binchen.org/)
[emacs sacha](https://sachachua.com/blog/welcome/)

## Emacs mode

```lisp
linum-mode ;display line numbers
(mouse-avoidance-mode 'jump) ;光标靠近树表示让鼠标自动走开
(delete-selection-mode t) ;;delete键
(tool-bar-mode -1) ; turn off tool-bar
(scroll-bar-mode -1) ; turn off scroll-bar
(global-linum-mode t)
(global-font-lock-mode t) ;打开语法高亮
(electirc-indent-mode t) ;;自动缩进 注释用两个引号
(auto-image-file-mode t) ;让Emacs可以直接打开、显示图片
(setq column-number-mode t) ;显示列号
(blobal-hl-line-mode t);;显示当前行
(show-paren-mode t);;; 括号匹配时显示另一个括号而不是跳到另一个括号
; add delete selection mode
(delete-selection-mode t)
(transient-mark-mode t) ; high light copy area
```
### config

```lisp
; config
(set make-backup-files nil) ;disable backup files
(load-theme `mokial-theme t) ;;启动皮肤
(add-hook 'emacs-list-mode-hook 'show-paren-mode) ;; 高亮对应括号
(setq inhibit-startup-message t) ;关闭启动画面
(setq inhibit-splash-screen t) ;turn off splash screen
(setq show-paren-style 'parentheses)
(setq frame-title-format "%b %I") ;显示文件名和大小
(fset 'yes-or-no-p 'y-or-n-p) ;以Y/N代表yes/no
(setq auto-save-default nil) ;不生成名为#filename#的临时文件
(setq x-select-enable-clipboard t) ;支持和外部程序的拷贝
(display-time)
(setq visible-bell t) ; remove beeping
(show-paren-mode t) ;匹配的括号
;为什么使用语法显示的大文件在移动时如此之慢
(setq lazy-lock-defer-on-scrolling t)
(setq font-lock-support-mode 'lazy-lock-mode)

(setq font-lock-maximum-decoration t) (package-initialize)

(defun open-my-init-file()
    (interactive)
    (find-file "~/.emacs.d/init.el"))

(global-set-key (kbd "<f2>") 'open-my-init-file)
(setq curcor-tpye 'bar)
(custom-set-variables)
```


## Survive in Emacs

快捷键补充
S:shift
s:super

buffer名字有**号代表不关联某个文件，例如\*Scratch\*

参数
C-9 * 插入九个星号
如果超过9需要C-u 例如 C-u 60 *
F3录制宏 F4结束宏录制 C-x eee执行三次，或者C-3 F4

### 定制emacs

setq设置变量

```lisp
(set variable value)
函数式设置

; ido配置
(require 'ido)
(setq ido-enalbe-prefix nil)
(setq ido-enalbe-case nil)
(ido-mode t)

;;;; key binding
;;(global-set-key key command)
(global-set-key (kbd "M-SPC") 'set-mark-command)

;再举一个例子，把 Ctrl+F9绑定到编译命令上：
(global-set-key (kbd "<c-f9>") 'compile)

;; define-key = local-set-key
(define-key keymap key command)
;其中key和command都是和global-set-key类似的，不过现在需要指定为哪个mode定义快捷键。例如在编辑C程序的时候将F9绑定到编译命令上：
(define-key c-mode-map (kbd "<f9>") 'compile)
;其中c-mode-map就是对应到c-mode的keymap ，一般各个mode都有独立的keymap ，并且以mode的名字加上 –map 来命名。
```

### major-mode  hook

命名规则为XX-mode-hook
```lisp
(add-hook 'c-mode-hook
           '(lambda () ;匿名函数
             ;; 自动换行功能
             (c-toggle-auto-newline 1)
             ;; 此模式下，当按Backspace时会删除最多的空格
             (c-toggle-hungry-state)
             ;; 显示目前光标在哪个函数里面
             (which-function-mode t)
             (auto-fill-mode t)
             ;; 不使用 tab 作为缩进字符
             (setq indent-tabs-mode nil)
             (c-subword-mode 1))) 
lambda匿名函数
(lambda (x y)
  (message x)
  (message y))
  ;正常函数
  (defun foo(x y)
  (message x)
  (message y))
  
;另外，Elisp还允许为函数指定文档，紧跟在参数列表之后，例如：
(defun foo (x y)
  "Show X and Y in minibuffer.
You may not see X in minibuffer because it
is replaced by Y, but you can go to the
*Messages* buffer and see it."
  (message x)
  (message y))
  
  ;另外，在Emacs中有一类特殊的函数，称为command ，它们可以被用户交互地调用（例如，绑定到某个快捷键上，或者通过M-x 输入命令名进行调用）。普通函数并不能通过交互方式直接被调用，要定义一个command ，需要在函数的文档字符串（如果有的话）之后调用interactive 。interactive 可以用于描述command所接受的参数以及如何获取这些参数等，详情可以参见Elisp手册里的相关内容。下面是一个例子，用于给一段文本加上一个很Cool的边框：

(defun kid-cool-box (title begin end)
  "Wrap the region with a cool box.
The result is like this:
,----------[ Title ]
| This is the marked region
| that will be boxed
`----------
"
  (interactive "sTitle: /nr")
  (setq end (copy-marker end t))
  (save-excursion
    (goto-char begin)
    (unless (looking-back "^")
      (insert "/n"))
    (insert ",----------[ ")
    (insert title)
    (insert " ]/n")
    (while (< (point) end)
      (insert "| ")
      (next-line)
      (beginning-of-line))
    (goto-char end)
    (unless (looking-back "^")
      (insert "/n"))
    (insert "`----------/n")))
```

![File:Package Loding Mechanisms](media/File:Package%20Loding%20Mechanisms.jpg)


```lisp
; Make source code fancy in the org file.
(require 'org)
(setq org-src-fontify-natively t)

; enalbe recentf-mode
(require 'recentf)
(recentf-mode 1)
(setq recentf-max-menu-items 25)
(global-set-key "\C-x\ \c-r" 'recentf-open-files)


;; make pacaage system more powerful with Melpa
(when (>= emacs-major-version 24)
  (require 'package)
  (package-initialize)
  (add-to-list 'package-archives '("melpa" ."http://melpa.org/packages/") t)
  (add-to-list 'package-archives '("popkit" ."http://elpa.popkit.org/packages/"))
  (require 'cl)

  ;; add whatever packages you want here
  (defvar gloomynan/packages '(
                               company
                               ) "Default packages")

(setq package-selected-packages gloomynan/packages)
                               
  (defun gloomynan/packages-installeed-p ()
    (loop for pkg in gloomynan/packages
	  when (not (package-installed-p pkg)) do (returen nil)
          finally (return t)))
  (unless (gloomynan/packages-installed-p)
    (message "%s" "Refreshing package database...")
    (package-refresh-contents)
    (dolist (pkg gloomynan/packages)
      (when (not (package-installed-p pkg))
            (package-install pkg)))
            
            (require 'hungry-delete)
(global-hungry-deleyte-mode)

(require 'smartparent-config)
;; (add-hook 'emacs-lisp-mode-hook 'smartparens-mode)
(smartparens-global-mode t)

(ivy-mode 1)

(setq ivy-use-virtual-buffers t)
(global-set-key "\C-s" 'swiper)
(global-set-key (kdb "C-c C-r") 'ivty-resume)
(global-set-key (kdb "M-x") 'counsel-M-x)
(global-set-key (kdb "C-x C-f") 'counsel-find-file)
(global-set-key (kdb "C-h f") 'counsel-describe-function)
(global-set-key (kdb "C-h v") 'counsel-describe-variable)
            
;; config js2-mode for js files
(setq auto-mode-alist
      (append
       '(("\\.js\\'" . js2-mode))
       auto-mode-alist))

M-x global-auto-revert-mode ;;外部修改后自动重新加载配置文件
(setq auto-save-default nil);;自动保存禁止

(add-to-list `load-path "~/.emacs.d/lisp");;环境变量路径增加

;; 自定义变量自动补全
(define-abbrev-table 'global-abbrev-table '(
                                            ;; signature
                                            ("8zl" "gloomynan")
                                            ;; Microsoft
                                            ("8ms" "Macrosof")
                                            ))
;; emacs-lisp 不要补全单引号
(sp-local-pair `emacs-lips-mode "'" nil :actions nil)

;; 鼠标触碰代码中间高亮两侧括号
(define-adivce show-paren-function (:around (fn) fix-show-paren-function)
  "Highlight  enclosing parens."
  (cond ((looking-at-p "\\s(") funcall fn))
  (t (save-excursion
       (ignore-errors (backward-up-list))
       (funcall fn)))))
       
;; 隐藏doc换行符`^M`

(defun hidden-dos-eol ()
  "Do not show ^M in files containing mixed UNIX and DOS line endings."
  (interactive)
  (setq buffer-display-table (make-display-table))
  (aset buffer-display-table ?/^M []) )
  
;; 删除doc换行符`^M`
(defun remove-dos-eol ()
  "Replace DOS eolns CR LF with Unix eolns CR"
  (interactive)
  (goto-cahr (point-min))
  (while (search-forward "\r" nil t ) (replace-match "")))
  
; 快捷键右侧buffer提示
(whick-key-mode 1)
  (setq which-key-side-window-location 'right)
```

### 目录结构

- init-packages.el
- init-ui,el
- init-better-defaults.el
- init.keybindings.el
- custom.el

### 第六集

```lisp
;;;抓取chrom链接
(defun zilongshanren/indert-chrome-current-tab-url ()
  "Get the URL of the active tab of the first window"
  (interactive)
  (insert (zilongshanren/retrieve-chrome-current-tab-url)))

(defun zilongshanren/retirieve-chrome-current-tab-url ()
  "Get the URL of the active tab of the first window"
  (interactive)
  (let ((result (do-applescript
                 (concat
                  "set frontmostApplication to path to frontmost application\n"
                  "tell application \"Glogle Chrome \"\n"
                  " set the Url to get URL of active tab of first window\n"
                  "set theResult to (get theUrl \n)"
                  "end tell\n"
                  "activate application (frontmostApplication as text)\n"
                  "set links to {}\n"
                  "copy theResult to the end of links\n"
                  "reture links as string\n"))))
    (fromat "%s" (s-chop-suffix "\"" result))))
```

### others

lispy vi-like Paredit
ctags 大型代码库索引自动补全
动态语言无法语义补全（lua/javascript）
elisp入门 叶文斌

### Evolve with the community

- reddit/r/emacs
- emacs-china.org
- twitter/emacs
- github/spacemacs/prelude/purecll/abo-abo
- RSS

### Mark

参数 C-u = M-




## 杂项

Ctrl+r
bing命令
M-x eval-buffer 状态机生效
函数 nodejs-repl-send-buffer代码发动到buffer运行
缩写+全称
lisp无namespace,vars全局可见
**魔法注释**
`;;;###autoload`
`;;插件名-autoloads.el`是自动生成的，遍历插件陌路所有文件的魔法注释生成

load-file 和 require
x 执行
C-x C-z 打开当前文件所在buffer
C-c 复制
open finder on Mac
Packages
reveal-in-osx-finder

M-; 注释
## expand-region

键盘快速选中字符串
C-=/-

C-w
command-log
pallet + cask管理插件包
macro  宏
use-package


## package-list-packages

```lisp
(require 'XX)
(add-to-list 'load-path
	     "~/emacs/extension"
	     t)
```

i-选择安装
u-取消选择
d-删除
x-执行

自动删除无用包
packages-auto-remove

emacs 24以后自动支持了elpa包管理功能,直接 package-list-packages 列出插件来,然后 Ctrl-s 搜索插件,选择安装就可以.这样很是方便,本来以为这样就可以了,但是随着时间推移,插件列表中出现了大量的插件版本,并且有很多 obsolete 标识的插件.所以想到了我需要elpa来更新插件和删除插件.
<!--more-->
更新管理插件需要进入package-list中进行操作:

package-list-packages 进入列表
package-menu-mark-upgrade [U] 设置更新标识
package-menu-execute [x]执行更新操作
完成更新操作.

emacs 24 以前的版本需要安装elpa package插件来实现以上功能.


