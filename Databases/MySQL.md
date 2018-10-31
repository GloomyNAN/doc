---
title: 《MySQL必知必会》笔记
---


## 第三章

```SQL
use <table_name>;
show databases;
show tables;
show columns from <table_name>;
describe <table_name>; -- 同 show columns
show status;
show create database <database>;-- 建库语句
show create table <table_name>;-- 检表语句
show grants;-- 权限
show errors; 
show warnings;
```
tips: `\g`结尾或`;`

## 第九章

```SQL
regexp -- 正则表达式
regexp '1|2'
regexp '[123]'
regexp '[1|2|3]'
regexp '[0-9|a-z|A-Z]'
-- .匹配任意字符串
-- \\ 前导查找点
regexp '[\\.]'
-- 测试正则
select <table_name> regexp '[0-9]';
```

### 第十五章

inner join
内连接，等值链接，默认方式

left /right out join 外链接

```SQL

```

### 关键字

```SQL
select 
update 
delete 
insert

limit
having
order by
group by -- with rollup每个分组及每个分组及别的值，聚合函数必须使用
distinct --去重
from
where

null
is null

or
between and
in
and
not
like -- %多个字符 _单个字符 通配符搜索花费时间长

concat -- 拼接字段

as
countt -- *包含空值 column 有值统计

```

### function

rtrim
ltrim
trim
upper
now


### sqls


```SQL
select trim('abc ');
select now();
-- 不需要考虑闰年比对时间
select <column> from <table> where year(date) = 2005 and month(date) = 9;
```
### others

#### where 和having的区别

1. 前者过滤行，后者过滤分组
2. 前者分组前过滤，后者分组后过滤

>select子查询顺序为由内至外；


### 知识点记录

- [ ] MySQL数据类型
- [ ] 系统表
- [ ] 配置
- [ ] 权限
- [ ] 分库分表
- [ ] 大数据
- [ ] 主从同步
- [ ] 前一复制
- [ ] 读写分离
- [ ] 索引
- [ ] 优化
- [ ] 全文搜索
- [ ] 视图场景
- [ ] 视图、存储过程区别
- [ ] 函数

