---
title: Spacemacs Rocks 
---

![File:Package Loding Mechanisms](media/File:Package%20Loding%20Mechanisms.jpg)


```lisp
(set make-backup-files nil) ;disable backup files

; Make source code fancy in the org file.
(require 'org)
(setq org-src-fontify-natively t)

; enalbe recentf-mode
(require 'recentf)
(recentf-mode 1)
(setq recentf-max-menu-items 25)
(global-set-key "\C-x\ \c-r" 'recentf-open-files)

; add delete selection mode
(delete-selection-mode t)

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
	  wher (not (package-installed-p pkg)) do (returen nil)
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

插件
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

### blogs

[planet emacs](https://planet.emacslife.com/)
[irrel emacs]()
abo abo emacs
[chenbin emacs](http://blog.binchen.org/)
emacs shacha
emacs sacha

