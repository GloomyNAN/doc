---
title: 制作deb包的三种方法
---

我所知道的制作deb包有三种方法，一种是将现有的文件打包，安装该包就像将打包的文件释放到某个目录；第二种是用deb源码打包; 
      第三种是用makefile源码打包,安装这种包就相当于用源码编译安装软件。

      1. 第一种方法-----将现有的文件打包：
      比如你要打包你当前debian系统的/usr/src/soft目录，然后在另一个debian系统上安装
      改包时这些文件也释放到/usr/src/soft目录下：
      在随便一个目录，比如是root下创建一个工作目录，比如是work
      #cd /root
      #mkdir work
      #cd work
      因为安装包的时候默认是将文件释放到根目录下，所以我们设定好它的路径：
      #mkdir -p usr/src
      #cp -a /usr/src/soft usr/src
      #mkdir DEBIAN
      用如下的方法在DEBIAN目录下创建一个control文件，并用加入内容：
      #cat >DEBIAN/control<<EOF
      Package: soft
      Version: 1.0.1
      Section: utils
      Priority: optional
      Architecture: i386
      Depends:
      Installed-Size: 512
      Maintainer: [url=mailto:sunwill_chen@hotmail.com]sunwill_chen#hotmail.com
      Description: soft package
      EOF
      #dpkg -b . /root/soft_1.0.1_i386.deb
      这样便已经在/root目录下生成一个soft_1.0.1_i386.deb的包了。
      2. 第二种方法，用deb源码包构建：
      该方法摘自 
      http://debian.linuxsir.org/doc/inthedebianway/debian_build_package.html
      下载源码包
      APT提供了一套简便的方法帮你获得发布版中众多程序的源代码以及创建一个.deb所需的所有文件。
      首先, 在 /etc/apt/sources.list 文件中加入 deb-src 条目. 详细参阅 APT HOWTO
      然后, 运行命令

          # apt-get update 或# aptitude update

      就可以用下面的命令下载源码包：

          # apt-get source packagename 或 # aptitude source packagename

      通常会下载三个文件：.orig.tar.gz，.dsc 和 .diff.gz。对于 Debian 
      专用的软件包，最后一个文件不会下载，第一个文件的文件名中没有“orig”项。
      dpkg-source 读取 .dsc 文件信息，将源码包解包到 packagename-version 目录，下载下来的源码包中有一个 
      debian/ 目录，里面是创建 .deb 包所需的文件。
      例如:

          $ apt-get source nano
          Reading package lists... DoneBuilding dependency tree...
          DoneNeed to get 1199kB of source archives.
          Get:1 http://ftp.us.debian.org testing/main nano 1.3.11-2 (dsc) [706B]
          Get:2 http://ftp.us.debian.org testing/main nano 1.3.11-2 (tar) 
      [1173kB]
          Get:3 http://ftp.us.debian.org testing/main nano 1.3.11-2 (diff) 
      [25.4kB]
          Fetched 1199kB in 3m46s (5287B/s) ... ...
          dpkg-source: extracting nano in nano-1.3.11
          dpkg-source: unpacking nano_1.3.11.orig.tar.gz
          dpkg-source: applying ./nano_1.3.11-2.diff.gz


      做相应调整后, 在源代码的根目录 nano-1.3.11 下运行:

          # dpkg-buildpackage -rfakeroot -uc -b

      将代码编译成为软件包.
      想要下载的源码包自动编译成软件包，只需在命令行中加上 -b，例如:

          # apt-get -b source packagename

      请在下载包所在的目录中运行上面的命令。

          # dpkg -i file.deb

      apt-get的source命令与它的其它命令有所不同，普通用户权限就可以运行source命令，指定文件被下载到用户调用 apt-source 
      package 命令时所处的目录中。

      3.第三种方法,用makefile的源码打包

      在源码所在的目录下用make命令来编译,然后用checkinstall命令来打包. 若没有checkinstall命令则可以先安装
      apt-get install checkinstall.
      -
www.ubuntusoft.com



