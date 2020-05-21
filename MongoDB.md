---
title:  mongo
date: 
tags:
---

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

