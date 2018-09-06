---
title:  Composer
date: 2018-06-19 14:26:49
tags:
---


**问题列表**

* [ ] 如何进行高效的开发模式
        增加插件快速依赖，修改命名空间自动加载
        
**本地仓库命令**

```shell
composer config repositories.gloomynan path /Users/GloomyNAN/WorkArea/WWW/GloomyNAN/laravel-alipay 
composer require jcc/taxi:dev-master -vvv

```
[Composer本地包](https://segmentfault.com/a/1190000010891972)
[基于Composer的PHP模块化开发-by overtrue](https://laravel-china.org/articles/5333/modular-development-of-php-based-on-composer)

**使用git代替packgist**

```
"repositories":[ 
       { 
           "type":"git", 
           "url":"/var/www/gouki/test/" 
       }, 
   ] 
```

