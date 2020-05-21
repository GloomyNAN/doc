---
title: Redis相关
---

##  Java客户端 Jedis

* Jedis: 一款java操作redis数据库的工具.

```java
	//1. 获取连接
    Jedis jedis = new Jedis("localhost",6379);
    // 2. 操作
    jedis.set("username","zhangsan");
    //3. 关闭连接
    jedis.close();
```
## jedis连接池： JedisPool

* 使用：
	1. 创建JedisPool连接池对象
	2. 调用方法 getResource()方法获取Jedis连接
  
  ```java
        JedisPoolConfig config = new JedisPoolConfig();
        config.setMaxTotal(50);
        config.setMaxIdle(10);

        //1.创建Jedis连接池对象
        JedisPool jedisPool = new JedisPool(config,"localhost",6379);

        //2.获取连接
        Jedis jedis = jedisPool.getResource();
        //3. 使用
        jedis.set("hehe","heihei");


        //4. 关闭 归还到连接池中
        jedis.close();
```

* 连接池工具类
	
	```java
	public class JedisPoolUtils {

	    private static JedisPool jedisPool;
	
	    static{
	        //读取配置文件
	        InputStream is = JedisPoolUtils.class.getClassLoader().getResourceAsStream("jedis.properties");
	        //创建Properties对象
	        Properties pro = new Properties();
	        //关联文件
	        try {
	            pro.load(is);
	        } catch (IOException e) {
	            e.printStackTrace();
	        }
	        //获取数据，设置到JedisPoolConfig中
	        JedisPoolConfig config = new JedisPoolConfig();
	        config.setMaxTotal(Integer.parseInt(pro.getProperty("maxTotal")));
	        config.setMaxIdle(Integer.parseInt(pro.getProperty("maxIdle")));
	
	        //初始化JedisPool
	        jedisPool = new JedisPool(config,pro.getProperty("host"),Integer.parseInt(pro.getProperty("port")));
	    }
	
	    /**
	     * 获取连接方法
	     */
	    public static Jedis getJedis(){
	        return jedisPool.getResource();
	    }
	}
```













	

