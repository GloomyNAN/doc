---
title:  RN ES6规范插件-eslint
date: 2018-06-19 14:26:49
tags:
---

## 资料

[JavaScript Style Guide By Airbnb](https://github.com/airbnb/javascript)
[npmjs:eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb)
[视频教学地址](https://v.youku.com/v_show/id_XMTg0MzgyOTQ5Mg==.html?spm=a2hzp.8253869.0.0)

## 一、安装eslint插件
```bash
# 安装
(
  export PKG=eslint-config-airbnb;
  npm info "$PKG@latest" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs npm install --save-dev "$PKG@latest"
)
```
## 二、建立配置文件
[.eslintrc配置文件](https://gist.github.com/sunnylqm/819173a40c7b2097b0c0c7c74ecab5a5#file-eslintrc)

## 三、安装babel-eslint


```bash
yarn add 
babel-eslint --dev
```


