---
title: Redis
date: 2018-06-19 14:26:49
tags:
---

Redis是用C语言开发的一个开源的高性能键值对（key-value）数据库，官方提供测试数据，50个并发执行100000个请求,读的速度是110000次/s,写的速度是81000次/s ，且Redis通过提供多种键值数据类型来适应不同场景下的存储需求，目前为止Redis支持的键值数据类型如下：

1. 字符串类型 string
2.  哈希类型 hash
3. 列表类型 list
4. 集合类型 set
5. 有序集合类型 sortedset

## redis的应用场景

- 缓存（数据查询、短连接、新闻内容、商品内容等等）
- 聊天室的在线好友列表
- 任务队列。（秒杀、抢购、12306等等）
- 应用排行榜
- 网站访问统计
- 数据过期处理（可以精确到毫秒
- 分布式集群架构中的session分离
		
##  redis的数据结构：

1. 字符串类型 string
2. 哈希类型 hash ： map格式  
3. 列表类型 list ： linkedlist格式。支持重复元素
4. 集合类型 set  ： 不允许重复元素
5. 有序集合类型 sortedset：不允许重复元素，且元素有顺序

## 其他		
```bash
# 启动服务：
redis-server /usr/local/redis/etc/redis.conf

# 查看
pid:sudo cat /usr/local/redis/redis.pid
```

**String类型**

```
# 写数据-覆盖更新
set key value

# 设置key对应的value为string类型的value，如果key已经存在，返回0，否则返回1，nx是not exist的意思
# 不覆盖更新
setnx key value

# 设置值有效期-返回1
setex key timeout value

# 设置key下value第N位替换value1,为返回字符串长度
setrange key n value1

# 批量设置,成功返回1，失败返回0-覆盖更新
mset key1 value1 key2 value2

# 批量设置,成功返回1，失败返回0,不覆盖更新
msetnx key1 value1 key2 value2

# 获取旧value设置新vaule
getset key value

# 获取key值
get key

# 从m到n个字符返回
getrange key m n

# 批量获取值
mget key1 key2 key2

# 对key的值自增，返回value
incr key

# 自增n次(-n自减)，key不存在则认为为0
incrby key n

# 自减一次
decr key

# 自减法n次(-n自增)，key不存在则认为为0
decrby key n

# 给key追加value,返回新value长度
append key value

# 获取key-value的长度
strlen key
```

**hashex类型**

```
# 设置hash field为指定值，如不存在则创建-覆盖更新
hset table name value

# 设置hash field 为指定值，如果key不存在，则先创建，如存在返回0-不覆盖更新
hsetnx table key value

# 批量设置
hmset table key1 value1 keyn valuen

# 获取
hget

# 批量获取
hmget

hincrby

# 获取字段数量
hlen 

# 删除制定hash的field
hdel

# 返回所有字段
hkeys

# 返回所有value
hvalue

# 获取所有key-value
hgetall
```
**list类型（链表）**

```
# 从头部压入一个元素
lpush key value

# 从头部取出N个元素
lrange key 0 -N

# 从尾部压入一个元素
rpush key value

# 在value1之前压入value2
linsert key before value1 value2
 
# 覆盖指定key的值为value
lset key value

# 从key中删除N个值为value的值，n<o从尾删除，n=0全部删除
lrem key n value

# 保留指定key的范围内的值
ltrim key 1 -1

# 从list头部删除元素，并返回删除元素
lpop key

# 从list尾部删除元素，并返回删除元素
rpop key

# 从list1尾部移除元素并添加到list2头部
ropolpush list1 list2 key


# 从尾部取出N个元素
rrange key 0 -N

# 返回名称为key的list中index位置的元素
lindex key [int]index

# 返回链表元素个数
llen list
```
**set无序集合**

```
# 向set集合添加value
sadd set value

# 查看set下所有元素
smember set

# 删除集合元素
srem set value

# 随机（set为无序集合）返回并删除set下的value
spop set

# 返回差集
sdiff set1(标准) set2

# 将ste2和set3的差集存储到set1
sdiffstore set1 set2 set3

# 返回交集
sinter set1 set2

# 将ste2和set3的交集存储到set1
sinterstore set1 set2 set3

# 并集
sunion set1 set2

# 将ste2和set3的并集存储到set1
sunionstore set1 set2 set3

# 移动元素（不是复制）
smove set1 set2 value

# 查看元素集合个数
scard set 

# 判断元素是否为set元素
sismember set value

# 随机返回元素
srandmember set
```
**zset(集合)**

```
# 添加元素-覆盖更新
zadd set order value

# 读取元素
zrange set 0-n withscores(带顺序号)

# 删除
zrem set value

# 增加value为N个顺序号
zincrby set N value

# 返回索引值-升序
zrank set value

# 返回索引值-降序
zrevrank set value

# 返回2到3的值
zrangebystore set 2 3 withscores

# 返回范围内元素数量
zcount set n n 

# 返回set所有元素个数
zcard set

# 删除索引区间value
zremrangebyrank set n n

# 删除顺序区间value
zremrangebyscore set n n
```
**Redis常用命令**

```
# 键值相关命令
keys *
exists key
del key
expire key # 设置生命周期
persist key # 销毁生命周期
ttl key # 键生命周期
randomkey # 随机返回key
rename key newkey
move key db # 移动数据到指定数据库
type key 

# server相关命令
ping 测试相应
echo 
quit
select # 选择数据库 0~15 共16个
dbsize # 返回key数量
info # 信息&统计
config get # 实时存储收到的的请求
flushdb # 清空当前数据库数据
flushall #删除所有数据库数据

HGET KEY
```

**事务**

```
redis事务即使有错误也不会回滚，正确的会正常执行

#建立将语句先放到队列里
multi #事务开始
语句巴拉巴拉巴拉
discard # 取消事务
exec #事务commit

# 乐观锁
# exec discard unwatch 都会清除监视
watch # 监控是否有修改
```
**持久化**

```
1.快照。备份数据

# 300秒内10个key被修改则备份
save 300 10 

2.aof,备份操作
 
```
![](media/14972331198142/15007395437999.jpg)

**发布订阅**

```
#发布消息
publish chanel msg
#订阅频道
subscribe chanel1 chanel2
psubscribe
```
**虚拟内存**

![](media/14972331198142/15007400719658.jpg)


notify-keyspace-events
stop-writes-on-bgsave-error


