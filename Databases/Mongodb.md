---
title: Mongodb
date: 2018-06-19 14:26:49
tags:
---

```bash
mongod --dbpath=../db --logpath=../log/mongod.log --part=27017（默认）
mongod --config D:/MongoDB/conf/mongo.conf
configsvr 貌似是用默认配置启动
mongod --install --dbpath=D:/MongoDB/db --logpath=D:/MongoDB/log/mongod.log

# 创建数据库
use mydb;

# 插入
db.user.insert({name:'tompig'});
save 如有更新
insert插入新的

# 查看表
show collections;

# 查看库
show dbs

# 删除库
db.dropDatabase();

# 删除表 
db.mytable.drop();
```
<!--more-->

配置文件

    mongod --config /usr/local/etc/mongod.conf
    sc create MongoDB binPath= "D\MongoDB2.6.6\bin\mongod.exe --config=D: \MongoDB2.6.6\mongod.cfg --service" displayname= "MongoDB 2.6 Standard Server" start= auto 
    D:\MongoDB2.6.6\bin\mongod.exe --config D:\MongoDB2.6.6\mongod.cfg --install 
    D:\MongoDB2.6.6\bin\mongod" -dbpath  D:\MongoDB2.6.6\database\test  -logpath  D:\MongoDB2.6.6\log\mongo.log -auth -service

rockmongo https://github.com/iwind/rockmongo


```bash
## 备份
mongodump -h localhost -d yapi -o ./
## 恢复
mongorestore -h localhost:27017 -d yapi ./yapi

## 创建用户
show dbs
use yapi 
db.createUser({ user: "yapi", pwd: "yapiGolal", roles: [{ role: "dbOwner", db: "yapi" }] })
db.auth("yapi", "yapiGolal")
exit;

root/Yqlmongodbzp320
db.createUser({user: "root",pwd: "Yqlmongodbzp320",roles: [ "readWrite", "dbAdmin" ]})
db.createUser({user:"yql",pwd: "Yqlmongodb",roles: [ { role: "readWrite", db: "yqldb"}) 
 /usr/local/mongodb/bin/mongod --dbpath /usr/local/mongodb/data/db --fork --logpath /usr/local/mongodb/conf/mongdb.conf

# 启动
/usr/local/mongodb/bin/./mongod --config /usr/local/mongodb/conf/mongodb.conf

# 停止
/usr/local/mongodb/bin/./mongod --config /usr/local/mongodb/conf/mongodb.conf --shutdown

# 连接
/usr/local/mongodb/bin/mongo localhost:27000/yqldb
db.auth('yql','Yqlmongodb')
```
