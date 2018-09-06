---
title: Nginx
date: 2017-12-01 16:46:54
tags:
---

##常用命令
    nginx -s [stop|quit|reopen|reload]
    ps -ef|grep nginx //查看主进程号

**停止** 
 
```bash
1. 从容停止
kill - QUIT '/usr/local/nginx/nginx.pid'
2. 快速停止
kill - TERM Nginx主进程号
kill - TERM '/usr/local/nginx/nginx.pid'
kill - INT Nginx主进程号
kill - INT '/usr/local/nginx/nginx.pid'
3. 强制停止所有Nginx进程
kill -9 '/usr/local/nginx/nginx.pid'
```   

**查看Nginx配置是否正确（重启之前）**

```bash
/usr/local/nginx/sbin/nginx -t -c
/usr/local/nginx/cong/nginx.conf
```

**平滑重启，重新加载配置文件**

```bash
kill -HUP Nginx主进程号
kill -HUP '/usr/local/nginx/nginx.pid'
```

**Nginx的信号控制**

```bash
TERM|INT        快速关闭
QUIT            从容关闭
HUP             平滑重启，重新加载配置文件
USR1            重新打开日志文件，在切割日志时用途较大
USR2            平滑升级可执行程序
WINCH           从容关闭工作进程
```

**Nginx的平滑升级**
当需要升级正在运行的Nginx时，添加/删除服务器模块可以不中断服务，进行升级

1. 使用新的可执行程序替换旧的可执行程序，对于编译安装的Nginx，可以将新版本编译安装到旧版本的Nginx安装路径中。替换之前，最好备份一下可执行文件。
2. kill -USR2 旧版本的Nginx朱版本号
3. 旧版本Nginx的主进程将重命名他的.pid，文件为.lodbin(例如：/usr/local/nginx/logs/nginx.pid.oldbin)，然后执行新版本的Nginx可执行文件。依次移动新的主进程和新的工作进程。
4. 此时，新、旧版本的Nginx实例会同事云心，共同处理输入的请求。要逐步停止旧版本的Nginx实例，必须发送winch新号给旧的主进程，然后他的工作进程就将开始充容关闭；
    
        kill -WINCH 旧版本的Nginx主进程号
5. 一段时间后，旧的工作进程（working process）处理了所有的已连接的请求后退出，仅有新的工作进程来处理输入请求。
6. 这时候，我们可以决定是使用新版本，还是恢复到旧版本：

        kill -HUP 旧的主版本号：Nginx将在补充在配置文件的情况下启动他的工作进程；
        kill -QUIT 新的主版本号：从容关闭其工作进程（working process）;
        kill -TERM 新的主版本号：强制退出；
        kill 新的主进程号或旧的主进程号：如果因为某些原因新的工作进程不能退出，则向其发送kill新号。
        
ps:新的主进程退出后，旧的主进程会移除.oldbin前缀，恢复为他的.pid文件，这样，一切就都恢复到升级之前了。如果尝试升级成功，而你也希望保留新的服务器是，可发送QUIT信号给旧的主进程，时期推出而只留下信心的服务器运行。

##配置

```conf
# 使用的用户和组
user www www;

# 制定工作衍生进程数（一般等于CPU的总核数或者总核数的两倍，例如两个四核CPU，则综合书为8）
worker——processes 8;

# 指定错误日志存放的路径，错误日志记录级别可选项为：{debug | info | notice | warn | error | crit }
error_log /DIR/nginx_error.log crit;

# 指定文件描述符数量
worker_rlimit_nofile 52100;

events
{
    # 使用的网络I/O模型，Linux 系统推荐采用epoll模型，FreeBSD系统推荐采用kqueue模型
    use epoll;
    
    # 允许的连接数
    worker_connections 52100;
}

htt
{
    include mime.types;
    default_type application/octet-stream;
    
    # 设置使用的字符集，如果一个网站有多种字符集，请不要随意设置，应该在代码里通过Meta标签设置
    #charset gb2312;
    
    server_name_hash_bucker_size 128;
    clint_header_buffer_size 32k;
    large_client_header_buffer 4 32k;

# 设置客户端能够上传的文件大小
client_max_body_size 8m;

send file on;
tcp_nopush on;
keepalive_timeout 60;
tcp_nodelay on;

fastcgi_connect_timeout 300;
fastcgi_send_timeout 300;
fastcgi_read_timeout 300;
fastcgi_buffer_size 64k;
fastcgi_buffers 4 64k;
fastcgi_busy_buffers_size 128k;
fastcgi_temp_file_write_size 128k;

# 开启gzip压缩

gzip on;
gzip_min_length 1k;
gzip_buffers 4 16k;
gzip_http_version 1.1;
gzip_comp_level 2;
gzip_types text/plain application/x-javascript text/css application/xml;
gzip_vary on;

# limit_zone crawler $binary_remote_addr 10m;

server
    {
        listen 80;
        server_name www.yourdomain.con yourdomain.com;
        index index.html index.htm index.php;
        root /DIR;
        #limit_conn crawler 20;
    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
    {
        erpries 30d;        
    }
      location ~ .*\.(js|css)?$
    {
        erpries 1h;        
    }
    
    log_fromat access  '$remote_addr = $remote_user [$time_local] "$request" ' 
    '$status $body_bytes_sent "$http_referer" '
    '"$http_user_agent" $http-X_forwarded_for';
    access_log /DIR/logs/access.log access; 
    }
}

```

**自动列目录**
 
```conf
# 无index自动列目录
loction / {
    
    # 设定索引是文件大小的单位（B、KB、MB、GB）
    autoindex on;
auto_index_exact_size [on | off]
}

    #开启本地时间来显示文件时间的功能。默认为关，GMT时间。
    autoindex_localtime [ on | off]   
```

**浏览器本地缓存设置**
语法：expires [timelepochlmax | off ]
默认值：expires off
作用域：http server location

## 日志
```bash
log_formate制定日志格式
access_log制定日志文件存放路径

# access_log语法:
access_log path [format [buffer=size | off]]

# 使用默认的combined格式记录日志可以
access_log DIR/access.log;
或者
access_log DIR/access.log combined;

# 自定义格式日志记录

```
其他命令记录
    
```bash    
rpm -ivh *.rpm
mkdir -p
tar zvcf *.tra.gz
cp -rf
```

