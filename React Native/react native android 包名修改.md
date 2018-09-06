---
title:  react native android 包名修改
date: 2018-05-18 15:39:22
tags:
---

大家都知道通过 react native 的命令` react-native init DemoApp android`默认包名是`com.demoapp`,然而我们在接入第三方或者`release`版本的时候的时候是需要修改为自己的包名，直接开始上解决方案：

**步骤**

- 在`/DemoApp/android/app/src/main/java/com/`目录下新建你自己包名的文件夹，举个例子，假如你的包名是`com.bike.home`就在`/DemoApp/android/app/src/main/java/com/`目录下新建文件夹`bike`,然后在`bike`文件夹下新建`home`文件夹。
- 将`/DemoApp/android/app/src/main/java/com/demoapp/`目录下的文件`MainActivity.java`和`MainApplication.java`这两个`java`文件移到新建的包名目录下，然后删除  `demoapp`文件夹（不删也可以，我是强迫症所以我删了，😄 ），最后将两个java文件的第一行替换为 `package com.bike.home;`。
- 将`DemoApp/android/app/src/main/AndroidManifest.xml`文件第二行把`package`的替换成为`package="com.bike.home"`。
- 修改打包脚本文件`DemoApp/android/app/BUCK`
    - - `android_build_config`中的 `package`替换为 `package = "com.bike.home"`,
    - - `android_resource` 中的 `package`替换为 `package = "com.bike.home"`,
- `DemoApp/android/app/build.gradle`文件中`defaultConfig`配置项下的`applicationId替换成applicationId` `"com.bike.home"`。
- 修改完成后，命令`cd android/`进入`android`目录，`mac` 执行`./gradlew clean`清除缓存即可（windows上是 `gradlew.bat`）

