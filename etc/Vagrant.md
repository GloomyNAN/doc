---
title: Vagrant
date: 2018年06月19日18:15:04
tags:
---

```bash
#添加
vagrant box add {作者/系统名} {box文件路径}  
vagrant box add base 远端的box地址或者本地的box文件名

# 初始化-如果添加box名称不是base，需要指定名称
vagrant init "CentOS 6.3 x86_64 minimal"
vagrant init {作者/系统名}

# 启动
vagrant up

# 查看状态
vagrant global-status
vagrant status 

# 删除虚拟机
vagrant box remove {作者/系统名} 

# 列出现有的虚拟机
vagrant box list

# 关闭指定虚拟机
vagrant halt {作者/系统名}  

# 当修改完配制后只要执行一下此命令就可以对虚拟机进行相关修改
vagrant provision 

# 重启虚拟机
vagrant reload 
# 带配置文件重启
vagrant reload --provision


#使用ssh的方式连接虚拟机 
vagrant ssh 

#查看版本信息
vagrant version

#安装插件
vagrant plugin {插件}

#打包
vagrant package {作者/系统名} 

#恢复虚拟机
vagrant resume  

#暂停虚拟机
vagrant suspend 
 
#销毁当前虚拟机
vagrant destroy 
vagrant destroy --force 
```

既然是开发环境，那么开发工作肯定还是需要在本地完成，而不是都要进到虚拟机中去完成，虚拟机就好好在后台运行服务就好了，不然就本末倒置了，所以这里就需要使用目录映射功能，将本地的目录映射到虚拟机的对应目录。

默认情况下，当前的工作目录，会被映射到虚拟机的 /vagrant 目录，当前目录下的文件可以直接在 /vagrant 下进行访问，当然也可以在通过 ln 创建软连接，如

    ln -fs /vagrant/wwwroot /var/www
来进行目录映射，当然，从自动化配置的角度，能不进系统就不需要进系统，所以在Vagrant也可以进行目录映射的操作：

    config.vm.synced_folder "wwwroot/", "/var/www"
前面的参数 “wwwroot/”  表示的是本地的路径，这里使用对于工作目录的相对路径，这里也可以使用绝对路径，比如： “d:/www/”

后面的参数 “/var/www” 表示虚拟机中对应映射的目录。

vagrant
	|---config
	|---provision
	|---nginx



