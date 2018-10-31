---
title: 使Homestead支持thiknphp框架
---

好吧，很多公司是laravel和thinkphp一起用，环境处理就很麻烦，因为tp的重写规则，每次更改配置文件或重启就会失效,所以给作者提交了一个pull request[#952](https://github.com/laravel/homestead/pull/952)增加了tp的配置。

## 使用方法如下：

1、更新你的homestead为[v7.18.0](https://github.com/laravel/homestead/releases/tag/v7.18.0)；
2、更改Homestead.yaml中站点配置的类型为thiknphp；

```yaml
    -   
        map: web.thinkphp
        to: /WWW/thinkphp/public 
        type: thinkphp
        php: "7.1"
```

3.、执行`homestead reload --provision`即可。

## 补充

如暂时不想更新homestead,可以下载[thiknphp配置文](https://gist.github.com/GloomyNAN/9b032f9465b6256de79d50ece1aa810b)件到`/laravel/homestead/scripts`下

