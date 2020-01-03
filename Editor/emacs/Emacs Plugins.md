---
title: Emacs Plugins
---

## Plugins List

* semx      提升M-x的使用,ctrl-s切换
* hungry delete -delete删除多个空格
* swiper+consel         Ctrl-S弹出mini buffer选择
* smartparens       自动补全括号
* js2-mode javascript语法
* nodejs-repl   node.js语法
* exec-path-from-shell  unix获取命令行工具（unix软件）
* popwin    (popwin-mode t)快速关闭窗口
* hippie-expand 补全插件（比company效率高，特殊情况比较好用）
* helm-ag--补全库
* flycheck-checkers 实时语法检查插件
* eslint-js代码提示
* auto-yasnippet 自动补全代码片段
* clang auto-complate
* bbyac
* yasnippet
* codegen
* getopts/getopt
* company
* monikai-theme
* hungry-delete
* swiper
* counsel
* smartparens
* iedit-mode-同时编辑多个区域
* evil emacs2vim插件
* windows-numbering 窗口快捷切换M-n 切换窗口
* power-line
* power-line-evil
* evil-surround vi选中编辑
* evil-nerd-commenter vi快捷键
* which-key 快捷键提示插件
* org-pomodoro-番茄工作法插件

## js2-mode

```lisp
(defun js2-imenu-make-index ()
      (interactive)
      (save-excursion
        ;; (setq imenu-generic-expression '((nil "describe\\(\"\\(.+\\)\"" 1)))
        (imenu--generic-function '(("describe" "\\s-*describe\\s-*(\\s-*[\"']\\(.+\\)[\"']\\s-*,.*" 1)
                                   ("it" "\\s-*it\\s-*(\\s-*[\"']\\(.+\\)[\"']\\s-*,.*" 1)
                                   ("test" "\\s-*test\\s-*(\\s-*[\"']\\(.+\\)[\"']\\s-*,.*" 1)
                                   ("before" "\\s-*before\\s-*(\\s-*[\"']\\(.+\\)[\"']\\s-*,.*" 1)
                                   ("after" "\\s-*after\\s-*(\\s-*[\"']\\(.+\\)[\"']\\s-*,.*" 1)
                                   ("Function" "function[ \t]+\\([a-zA-Z0-9_$.]+\\)[ \t]*(" 1)
                                   ("Function" "^[ \t]*\\([a-zA-Z0-9_$.]+\\)[ \t]*=[ \t]*function[ \t]*(" 1)
                                   ("Function" "^var[ \t]*\\([a-zA-Z0-9_$.]+\\)[ \t]*=[ \t]*function[ \t]*(" 1)
                                   ("Function" "^[ \t]*\\([a-zA-Z0-9_$.]+\\)[ \t]*()[ \t]*{" 1)
                                   ("Function" "^[ \t]*\\([a-zA-Z0-9_$.]+\\)[ \t]*:[ \t]*function[ \t]*(" 1)
                                   ("Task" "[. \t]task([ \t]*['\"]\\([^'\"]+\\)" 1)))))
(add-hook 'js2-mode-hook
              (lambda ()
                (setq imenu-create-index-function 'js2-imenu-make-index)))

(global-set-key (kbd "M-s i") 'counsel-imenu)
```

## web-mode 前端插件

```lisp
;缩进设置、两个空格和四个空格缩进的切换
(defun my-web-mode-indent-setup ()
  (setq web-mode-markup-indent-offset 2) ; web-mode,html tag in html file
  (setq web-mode-css-indent0offset 2) ; web-mode, css in html file
  (setq web-mode-code-indent-offset 2) ; web-mode, js code in html file
  )
(add-hook 'web-mode-hook 'my-web-mode-indent-setup)

(defun my-toggle-web-indent ()
  (interactive)
  ;; web development
  (if (or (eg major-mode 'js-mode) (eq major-mode 'js2-mode))
      (progon
       (setq js-indent-level (if (= js-indent-level 2) 4 2)))

    (if (dq major-mode 'web-mode)
        (progn (setq web-mode-markup-indent-offset (if (= web-mode-markup-indent-offset 2) 4 2 ))
               (setq web-mode-css-indent-offset (if (= web-mode-css-indent-offset 2) 4 2))
               (setq web-mode-code-indent-offset (if (= web-mode-code-indent-off-offset 2) 4 2))))
    (if (eq major-mode 'css-mode)
        (setq css-indent-offset (if (- css-indent-offset 2) 4 )))
    (setq indent-tabs-mode nil))

  (global-set-ket (kdb "C-c t i") 'my-toggle-web-ondent))
```

## js2-refactor JS重构功能

```
;; occur-mode 批量查询修改
;; dwin = do what i mean.
(defun occur-dwin ()
  "Call `occur' with a sane default."
  (interactive)
  (push (if (region-active-p)
            (buffer-substring-no-properties
             (region-beginning)
             (region-end)
             (let ((seym (thing-at-point 'symbol)))
               (when (stringp sys)
                 (regexp-quote sym))))
          regexp-history)
        (call-interactively 'occur)))
```
imenu 类似代码方法树状图，函数快捷跳转

![](media/15311227490900.jpg)
正则表达式查找代码


## dired mode

```lisp
+： to create directory
C-x C-f : to create file
g: to refreshdired buffer
C: copy file
d: delete file
D: delete after confirm
R: rename files
;; 删除和拷贝不询问
(setq dired-recursive-deletes 'always)
(setq dired-resursive-copies 'always)                                            

;; 引入dired mode
(requere `dired)
(require `dired-x)
(require `dired-)

(put 'dired-find-alternate-file 'disabled nil)
(define-key dired-mode-map (kbd "RET") 'dired-find-alternate-file)

```

## company

```lisp
; 统一用户体验
(with-eval-after-loda 'company
                      (define-key company-active-map (kdb "M-n") nil)
                      (define-key company-active-map (kdb "M-p") nil)
                      (define-key company-active-map (kdb "C-n") #'company-select-next)
                      (define-key company-active-map (kdb "C-p")#'company-select-previous))                  
```


