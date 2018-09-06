---
title:  Npm
date: 2018-06-19 14:26:49
tags:
---

查看全局安装的包
    
    npm list -g --depth 0
    查看模块：npm view react-native-swiper
    删除模块：npm rm react-native-swiper --save
    清理缓存：npm cache clean

```bash
npm install <name>#安装nodejs的依赖包
npm install express@3.0.6#安装指定版本
npm install <name> -g  #将包安装到全局环境中
但是代码中，直接通过require()的方式是没有办法调用全局安装的包的。全局的安装是供命令行使用的，就好像全局安装了vmarket后，就可以在命令行中直接运行vm命令
npm install <name> --save  
#安装的同时，将信息写入package.json中
#项目路径中如果有package.json文件时，
#直接使用npm install方法就可以根据
#dependencies配置安装所有的依赖包
这样代码提交到github时，就不用提交node_modules这个文件夹了。
npm init  #会引导你创建一个package.json文件，包括名称、版本、作者这些信息等
npm remove <name>#移除
npm update <name>#更新
npm ls #列出当前安装的了所有包
npm root #查看当前包的安装路径
npm root -g  #查看全局的包的安装路径
npm help  #帮助，如果要单独查看install命令的帮助，可以使用的npm help install
```

**项目用插件合集**

npm i react-native-swiper --save

https://segmentfault.com/a/1190000005857342


pm2

## node升级

查看当前node版本：`node –v`

安装n模块：`npm install -g n`

升级到指定版本/最新版本（该步骤可能需要花费一些时间）升级之前，可以执行n ls （查看可升级的版本）
如：n 6.9.1

或者你也可以告诉管理器，安装最新的稳定版本

n stable

安装完成后，查看Node的版本，检查升级是否成功
node -v


