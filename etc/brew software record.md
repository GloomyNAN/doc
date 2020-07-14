---
title: brew software record
---


```bash

# uninstall
brew tap beeftornado/rmtree

brew rmtree git
brew cleanup

emacs

# Lang
go python3

# Gun
telnet tig tree htop wget

# Others
node docker git-lfs

# IOS 
carthage - SnaKit依赖

# package manager
dep //go

# 命令提示工具
tldr

```
cask

- virtualbox
- visual-studio-code
- ngrok-反向代理
- vagrant


brew deps --tree --installed

brew leaves | xargs brew deps --installed --for-each | sed "s/^.*:/$(tput setaf 4)&$(tput sgr0)/"