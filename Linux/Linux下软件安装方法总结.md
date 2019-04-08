---
title:  Linux下软件安装方法总结
date: 2018-06-19 14:26:49
tags:
---

## 一、rpm包安装方式步骤：
1. 找到相应的软件包，比如soft.version.rpm，下载到本机某个目录；
2. 打开一个终端，su -成root用户；
3. cd soft.version.rpm所在的目录；
4. 输入rpm -ivh soft.version.rpm

## 二、deb包安装方式步骤：
1. 找到相应的软件包，比如soft.version.deb，下载到本机某个目录；
2. 打开一个终端，su -成root用户；
3. cd soft.version.deb所在的目录；
4. 输入dpkg -i soft.version.deb

## 三、tar.gz源代码包安装方式：

```
1. 找到相应的软件包，比如soft.tar.gz，下载到本机某个目录；
2. 打开一个终端，su -成root用户；
3. cd soft.tar.gz所在的目录；
4. tar -xzvf soft.tar.gz //一般会生成一个soft目录
5. cd soft
6. ./configure
7. make
8. make install
```

## 四、tar.bz2源代码包安装方式：

```
1、找到相应的软件包，比如soft.tar.bz2，下载到本机某个目录；
2、打开一个终端，su -成root用户；
3、cd soft.tar.bz2所在的目录；
4、tar -xjvf soft.tar.bz2 //一般会生成一个soft目录
5、cd soft
6、./configure
7、make
8、make install

```
## 五、apt方式安装：


```
1、打开一个终端，su -成root用户；
2、apt-cache search soft 注：soft是你要找的软件的名称或相关信息
3、如果2中找到了软件soft.version，则用apt-get install soft.version命令安装软件 注：只要你可以上网，只需要用apt-cache search查找软件，用apt-get install软件
六、bin文件安装：
如果你下载到的软件名是soft.bin，一般情况下是个可执行文件，安装方法如下：
1、打开一个终端，su -成root用户；
2、chmod +x soft.bin
3、./soft.bin //运行这个命令就可以安装软件了
```

关于本文档
*filename:Linux下软件安装方法总结
*purpose:总结了Linux下各种软件安装方法
*wrote by: zhoulifa(zhoulifa@163.com) 周立发(http://zhoulifa.bokee.com)
Linux爱好者 Linux知识传播者 SOHO族 开发者 最擅长C语言编程
*date time:2006-07-26 18:10:00
*Note: 任何人可以任意复制代码并运用这些文档，当然包括你的商业用途
* 但请遵循GPL。
*Hope:希望越来越多的人贡献自己的力量，为科学技术发展出力

## 七、不需要安装的软件：
有了些软件，比如lumaqq，是不需要安装的，自带jre解压缩后可直接运行。假设下载的是lumaqq.tar.gz，使用方法如下：
1、打开一个终端，su -成root用户；
2、tar -xzvf lumaqq.tar.gz //这一步会生成一个叫LumaQQ的目录
3、cd LumaQQ
4、chmod +x lumaqq //设置lumaqq这个程序文件为可运行
5、此时就可以运行lumaqq了，用命令./lumaqq即可，但每次运行要输入全路径或切换到刚才生成的LumaQQ目录里
6、为了保证不设置路径就可以用，你可以在/bin目录下建立一个lumaqq的链接，用命令ln -s lumaqq /bin/ 即可，以后任何时候打开一个终端输入lumaqq就可以启动QQ聊天软件了
7、 如果你要想lumaqq有个菜单项，使用菜单编辑工具，比如Alacarte Menu Editor，找到上面生成的LumaQQ目录里的lumaqq设置一个菜单项就可以了，当然你也可以直接到 /usr/share/applications目录，按照里面其它*.desktop文件的格式生成一个自己的desktop文件即可。
1、已经编译打包好的xxx.rpm

如果你的Linux系统带有安装程序，最好用系统自带的安装程序来安装。比如SuSE的 YaST2就带有安装程序，在KDE环境下只要是rpm，就可以在Konqueror里面点击再“Install with YaST2”，这样做的好处是YaST2会给你提示包的详细信息，自动检查信赖关系，而且以后可以方便地在YaST2里面卸载软件包。SuSE的Red- Carpet也提供了安装功能，也不错。

另一种方式是使用rpm命令，需要打开终端，切换到xxx.rpm所在目录，执行：
rpm -ivh xxx.rpm

如果需要还可以带上其他参数。不过在SuSE里面，用rpm命令安装的软件包，在YaST2的控制面板里面显示为“锁定状态”，我不知道这是什么意思，不过软件包是可用的，也可以在YaST2里面卸载。

2、打包好的源码包xxx.src.rpm

要用命令来重新生成一下：
rpm -rebuild xxx.src.rpm

3、安装程序xxx.bin

商业软件有不少以这种方式打包发行，其实就相当于Windows下的Setup.exe，不过你得先把xxx.bin改为可执行状态，可以用右键-->属性来修改，也可以用如下命令：
chmod +x xxx.bin

这样，就可以通过双击或在终端下执行xxx.bin了。

4、压缩方式的软件包xxx.tar.gz、xxx.bz2、xxx.z等等

      
对 于刚刚接触Linux的人来说，一定会给Linux下一大堆各式各样的文件名给搞晕。别个不说，单单就压缩文件为例，我们知道在Windows下最常见的 压缩文件就只有两种，一是,zip，另一个是.rar。可是Linux就不同了，它有.gz、.tar.gz、tgz、bz2、.Z、.tar等众多的压 缩文件名，此外windows下的.zip和.rar也可以在Linux下使用，不过在Linux使用.zip和.rar的人就太少了。本文就来对这些常 见的压缩文件进行一番小结，希望你下次遇到这些文件时不至于被搞晕.

在具体总结各类压缩文件之前呢，首先要弄清两个概念：打包和压 缩。打包是指将一大堆文件或目录什么的变成一个总的文件，压缩则是将一个大的文件通过一些压缩算法变成一个小文件。为什么要区分这两个概念呢？其实这源于 Linux中的很多压缩程序只能针对一个文件进行压缩，这样当你想要压缩一大堆文件时，你就得先借助另它的工具将这一大堆文件先打成一个包，然后再就原来 的压缩程序进行压缩。

Linux下最常用的打包程序就是tar了，使用tar程序打出来的包我们常称为tar包，tar包文件的命令通常都是以.tar结尾的。生成tar包后，就可以用其它的程序来进行压缩了，所以首先就来讲讲tar命令的基本用法：

tar命令的选项有很多(用man tar可以查看到)，但常用的就那么几个选项，下面来举例说明一下：

# tar -cf all.tar *.jpg
这条命令是将所有.jpg的文件打成一个名为all.tar的包。-c是表示产生新的包，-f指定包的文件名。

# tar -rf all.tar *.gif
这条命令是将所有.gif的文件增加到all.tar的包里面去。-r是表示增加文件的意思。
# tar -uf all.tar logo.gif
这条命令是更新原来tar包all.tar中logo.gif文件，-u是表示更新文件的意思。

# tar -tf all.tar
这条命令是列出all.tar包中所有文件，-t是列出文件的意思

# tar -xf all.tar
这条命令是解出all.tar包中所有文件，-x是解开的意思

以上就是tar的最基本的用法。为了方便用户在打包解包的同时可以压缩或解压文件，tar提供了一种特殊的功能。这就是tar可以在打包或解包的同时调用其它的压缩程序，比如调用gzip、bzip2等。

1) tar调用gzip

gzip是GNU组织开发的一个压缩程序，.gz结尾的文件就是gzip压缩的结果。与gzip相对的解压程序是gunzip。tar中使用-z这个参数来调用gzip。下面来举例说明一下：

# tar -czf all.tar.gz *.jpg
这条命令是将所有.jpg的文件打成一个tar包，并且将其用gzip压缩，生成一个gzip压缩过的包，包名为all.tar.gz

# tar -xzf all.tar.gz
这条命令是将上面产生的包解开。

2) tar调用bzip2

bzip2是一个压缩能力更强的压缩程序，.bz2结尾的文件就是bzip2压缩的结果。与bzip2相对的解压程序是bunzip2。tar中使用-j这个参数来调用gzip。下面来举例说明一下：

# tar -cjf all.tar.bz2 *.jpg
这条命令是将所有.jpg的文件打成一个tar包，并且将其用bzip2压缩，生成一个bzip2压缩过的包，包名为all.tar.bz2

# tar -xjf all.tar.bz2
这条命令是将上面产生的包解开。
3)tar调用compress

compress也是一个压缩程序，但是好象使用compress的人不如gzip和bzip2的人多。.Z结尾的文件就是compress压缩的结 果。与 compress相对的解压程序是uncompress。tar中使用-Z这个参数来调用gzip。下面来举例说明一下：

# tar -cZf all.tar.Z *.jpg
这条命令是将所有.jpg的文件打成一个tar包，并且将其用compress压缩，生成一个uncompress压缩过的包，包名为all.tar.Z

# tar -xZf all.tar.Z
这条命令是将上面产生的包解开

有了上面的知识，你应该可以解开多种压缩文件了，下面对于tar系列的压缩文件作一个小结：

1)对于.tar结尾的文件

tar -xf all.tar

2)对于.gz结尾的文件

gzip -d all.gz
gunzip all.gz

3)对于.tgz或.tar.gz结尾的文件

tar -xzf all.tar.gz
tar -xzf all.tgz

4)对于.bz2结尾的文件

bzip2 -d all.bz2
bunzip2 all.bz2

5)对于tar.bz2结尾的文件

tar -xjf all.tar.bz2

6)对于.Z结尾的文件

uncompress all.Z

7)对于.tar.Z结尾的文件

tar -xZf all.tar.z

另外对于Window下的常见压缩文件.zip和.rar，Linux也有相应的方法来解压它们：

1)对于.zip

linux下提供了zip和unzip程序，zip是压缩程序，unzip是解压程序。它们的参数选项很多，这里只做简单介绍，依旧举例说明一下其用法：

# zip all.zip *.jpg
这条命令是将所有.jpg的文件压缩成一个zip包
# unzip all.zip
这条命令是将all.zip中的所有文件解压出来

2)对于.rar

要在linux下处理.rar文件，需要安装RAR for Linux，可以从网上下载，但要记住，RAR for Linux
不是免费的；可从http://www.rarsoft.com/download.htm下载RAR for Linux 3.2.0，然后安装：

# tar -xzpvf rarlinux-3.2.0.tar.gz
# cd rar
# make

这样就安装好了，安装后就有了rar和unrar这两个程序，rar是压缩程序，unrar是解压程序。它们的参数选项很多，这里只做简单介绍，依旧举例说明一下其用法：

# rar a all *.jpg
这条命令是将所有.jpg的文件压缩成一个rar包，名为all.rar，该程序会将.rar 扩展名将自动附加到包名后。

# unrar e all.rar
这条命令是将all.rar中的所有文件解压出来

到此为至，我们已经介绍过linux下的tar、gzip、gunzip、bzip2、bunzip2、compress、uncompress、 zip、unzip、rar、unrar等程式，你应该已经能够使用它们对.tar、.gz、.tar.gz、.tgz、.bz2、.tar.bz2、. Z、.tar.Z、.zip、.rar这10种压缩文件进行解压了，以后应该不需要为下载了一个软件而不知道如何在Linux下解开而烦恼了。而且以上方 法对于Unix也基本有效。

本文介绍了linux下的压缩程式tar、gzip、gunzip、bzip2、bunzip2、 compress、uncompress、zip、 unzip、rar、unrar等程式，以及如何使用它们对.tar、.gz、.tar.gz、.tgz、.bz2、.tar.bz2、.Z、. tar.Z、.zip、.rar这10种压缩文件进行操作。

压缩：
压缩： tar调用bzip2
bzip2是一个压缩能力更强的压缩程序，.bz2结尾的文件就是bzip2压缩的结果。与bzip2相对的解压程序是bunzip2。tar中使用-j这个参数来调用gzip。下面来举例说明一下：
# tar -cjf all.tar.bz2 *.jpg

解压缩： 对于.bz2结尾的文件

bzip2 -d all.bz2
bunzip2 all.bz2

其实既然可以tar -cjf all.tar.bz2 *.jpg,当然也可以tar -xjf all.tar.bz2的。
我试过了，没有问题，完全可以用tar命令实现，而不是bunzip2



这种软件包又分两种形式：

(1)已经编译好的软件包，使用安装脚本来安装：

你最好先看一下软件包的说明文件，如readme、install、xxx.htm等。

再找一下有没有xxx.sh、xxx.pl这种文件，一般是install.sh或install.pl，也可能不是这种名字，具体情况具体分析。

打开终端，切换到软件包所在目录，运行如下命令：
./xxx.sh 或 ./xxx.pl 即可。

(2)需要自行编译的源码压缩包，先解压缩：

同样地，你最好先看一下软件包的说明文件，如readme、install、xxx.htm等。

一般安装形式为：

打开终端，切换到软件包所在目录，运行如下命令：

./configure （做一下自动配置，一般会花不少时间。配置程序会检查你的系统信息，作出相应配置，肯定会检查你的编译器(如gcc)和库文件(如glib)等信息，所以你必须保证你的系统上有这些软件）

make （开始编译，一般会花不少时间）

make check （检查一下结果是否正确。这步不是必须，但建议做一下）

make install （运行安装程序）

这样，就完成了软件安装过程。

如果你想删除源代码文件的话，可以在原目录运行命令：
make clear

如果你想卸载该软件包的话，可以在原目录下运行命令：
make uninstall

5、使用java编译的安装程序xxx.jar

首先，你的系统上必须有java虚拟机软件，如果没有，到Sun公司的网站上下载一个装上（http://www.java.com或者http://java.sun.com）。

要安装xxx.jar形式的软件包，先打开终端，切换到xxx.jar所在目录，执行：
java -jar xxx.jar

这样就启动了安装程序。

make check （检查一下结果是否正确。这步不是必须，但建议做一下）
make clear

如果你想卸载该软件包的话，可以在原目录下运行命令：
make uninstall

6.使用portage，敲指令：

# emerge packagename (从源码编译或安装某些已编好了的包)
# emerge -k packagename (自己编译好摆在硬盘上的包)


## apt卸载

sudo apt-get remove <package> #-----(package 删除包)。
sudo apt-get purge <package> # ----(package 删除包，包括删除配置文件等) 　　
sudo apt-get -y autoremove 卸载不需要的依赖关系。
sudo apt-get -y autoclean 清理安装软件时留下的缓存程序软件包/只清理过时的包 　　。
sudo apt-get -y clean 清理下载文件的存档。

