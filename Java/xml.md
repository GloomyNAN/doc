---
title: XML
---

##  DTD：

- 引入dtd文档到xml文档中
  - 内部dtd：将约束规则定义在xml文档中
  - 外部dtd：将约束的规则定义在外部的dtd文件中
- 本地：<!DOCTYPE 根标签名 SYSTEM "dtd文件的位置">
- 网络：<!DOCTYPE 根标签名 PUBLIC "dtd文件名字" "dtd文件的位置URL">


## Schema:

### 引入

1. 填写xml文档的根元素
2. 引入xsi前缀.  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
3. 引入xsd文件命名空间.  xsi:schemaLocation="http://www.itcast.cn/xml  student.xsd"
4. 为每一个xsd约束声明一个前缀,作为标识  xmlns="http://www.itcast.cn/xml" 

```xml
<students   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xmlns="http://www.itcast.cn/xml"
		xsi:schemaLocation="http://www.itcast.cn/xml  student.xsd">
```

### 解析

操作xml文档，将文档中的数据读取到内存中

#### 操作xml文档

1. 解析(读取)：将文档中的数据读取到内存中
2. 写入：将内存中的数据保存到xml文档中。持久化的存储

#### 解析xml的方式：

1. DOM：将标记语言文档一次性加载进内存，在内存中形成一颗dom树
   - 优点：操作方便，可以对文档进行CRUD的所有操作
   - 缺点：占内存
2. SAX：逐行读取，基于事件驱动的。
   - 优点：不占内存。
   - 缺点：只能读取，不能增删改
	
## xml常见的解析器：

1. JAXP：sun公司提供的解析器，支持dom和sax两种思想
2. DOM4J：一款非常优秀的解析器
3. Jsoup：jsoup 是一款Java 的HTML解析器，可直接解析某个URL地址、HTML文本内容。它提供了一套非常省力的API，可通过DOM，CSS以及类似于jQuery的操作方法来取出和操作数据。
4. PULL：Android操作系统内置的解析器，sax方式的。

### Jsoup
 
jsoup 是一款Java 的HTML解析器，可直接解析某个URL地址、HTML文本内容。它提供了一套非常省力的API，可通过DOM，CSS以及类似于jQuery的操作方法来取出和操作数据。

#### 快速入门：

步骤：

1. 导入jar包
2. 获取Document对象
3. 获取对应的标签Element对象
4. 获取数据

#### 代码：

```java
//2.1获取student.xml的path
String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
//2.2解析xml文档，加载文档进内存，获取dom树--->Document
Document document = Jsoup.parse(new File(path), "utf-8");
//3.获取元素对象 Element
Elements elements = document.getElementsByTag("name");
		
System.out.println(elements.size());
//3.1获取第一个name的Element对象
Element element = elements.get(0);
//3.2获取数据
String name = element.text();
System.out.println(name);
```

#### 对象的使用：

1. Jsoup：工具类，可以解析html或xml文档，返回Document
	- parse：解析html或xml文档，返回Document
	- parse​(File in, String charsetName)：解析xml或html文件的。
	- parse​(String html)：解析xml或html字符串
	- parse​(URL url, int timeoutMillis)：通过网络路径获取指定的html或xml的文档对象
2. Document：文档对象。代表内存中的dom树
	- 获取Element对象
	- getElementById​(String id)：根据id属性值获取唯一的element对象
	- getElementsByTag​(String tagName)：根据标签名称获取元素对象集合
	- getElementsByAttribute​(String key)：根据属性名称获取元素对象集合
	- getElementsByAttributeValue​(String key, String value)：根据对应的属性名和属性值获取元素对象集合
3. Elements：元素Element对象的集合。可以当做 ArrayList<Element>来使用
4. Element：元素对象
	1. 获取子元素对象
		- getElementById​(String id)：根据id属性值获取唯一的element对象
		- getElementsByTag​(String tagName)：根据标签名称获取元素对象集合
		- getElementsByAttribute​(String key)：根据属性名称获取元素对象集合
		- getElementsByAttributeValue​(String key, String value)：根据对应的属性名和属性值获取元素对象集合
	2. 获取属性值
		- String attr(String key)：根据属性名称获取属性值
	3. 获取文本内容
		- String text():获取文本内容
		- String html():获取标签体的所有内容(包括字标签的字符串内容)
5. Node：节点对象
	- 是Document和Element的父类
	- 快捷查询方式：
6. selector:选择器
	- 使用的方法：Elements	select​(String cssQuery)
	- 语法：参考Selector类中定义的语法
7. XPath：XPath即为XML路径语言，它是一种用来确定XML（标准通用标记语言的子集）文档中某部分位置的语言
	- 使用Jsoup的Xpath需要额外导入jar包。
	- 查询w3cshool参考手册，使用xpath的语法完成查询
	- 代码：

``` java
// 1.获取student.xml的path
String path = JsoupDemo6.class.getClassLoader().getResource("student.xml").getPath();
// 2.获取Document对象
Document document = Jsoup.parse(new File(path), "utf-8");

// 3.根据document对象，创建JXDocument对象
 JXDocument jxDocument = new JXDocument(document);

// 4.结合xpath语法查询
// 4.1查询所有student标签
List<JXNode> jxNodes = jxDocument.selN("//student");
for (JXNode jxNode : jxNodes) {
    System.out.println(jxNode);
}

System.out.println("--------------------");

// 4.2查询所有student标签下的name标签
List<JXNode> jxNodes2 = jxDocument.selN("//student/name");
for (JXNode jxNode : jxNodes2) {
    System.out.println(jxNode);
}

System.out.println("--------------------");

// 4.3查询student标签下带有id属性的name标签
List<JXNode> jxNodes3 = jxDocument.selN("//student/name[@id]");
for (JXNode jxNode : jxNodes3) {
    System.out.println(jxNode);
}
System.out.println("--------------------");
// 4.4查询student标签下带有id属性的name标签 并且id属性值为itcast

List<JXNode> jxNodes4 = jxDocument.selN("//student/name[@id='itcast']");
for (JXNode jxNode : jxNodes4) {
    System.out.println(jxNode);
}
```