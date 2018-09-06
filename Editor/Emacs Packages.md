---
title: Emacs Packages
---

#### package-list-packages

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

