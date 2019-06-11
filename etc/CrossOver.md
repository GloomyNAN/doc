# CrossOver容器过期处理

右键容器图标打开磁盘，删除.eval

## 关于crossover过期和bottle过期的解决方法

果你的crossover已过期不能够使用，可使用下面方法：

在目录“用户/资源库/Preferences/”中找到“com.codeweavers.CrossOver.plist”文件，将文件中firstrundate属性改成未来某一时间，就是如果你是2013年的，改为2023就行了。

现在你就可以继续试用了，可是：

又有一个问题出现了，当我点开以前的程序时，它弹出一个页面说bottle已经过期，无法继续使用。。。我了个去，于是乎我往上找了一下，还是能够解决的。

目录“用户/资源库/application support/crossover”中找到bottles文件夹，然后里面就有以前安装的应用程序了，它把程序分成了文件夹，在每个文件夹中找到隐藏文件.eval文件，拉到回收站，OK，搞定

借鉴网址：

http://www.wangchen.org/2010/10/crossover-bottle-%E8%BF%87%E6%9C%9F/

