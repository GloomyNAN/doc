---
title: java基础
---

## 前言

## JVM&JDK&JRE

### java虚拟机的内存划分

|区域名称|作用|
|---|---|
|寄存器|给CPU使用，和开发无关|
|本地方法栈|jvm在使用才做系统功能的时候使用，与开发无关|
|方法区|存储可以运行的class文件|
|堆内存|存储对象或者数组，new来创建的都存在堆内存。|
|方法栈|方法运行使用的内存，比如main方法运行进入方法栈中|

### 字节

位（bit）：一个数字0或者一个数字1，代表一位。

字节（Byte）：每逢8位是一个字节，这是数据存储的最小单位。

1 Byte = 8 bit

1 KB = 1024 Byte
1 MB = 1024 KB
1 GB = 1024 MB
1 TB = 1024 GB
1 PB = 1024 TB
1 EB = 1024 PB
1 ZB = 1024 EB

## 数据类型

- 基本数据类型：整数、浮点数、字符、布尔
- 引用数据类型：字符串、类、数组、接口、Lambd

### 四类八种数据类型

|数据类型| 关键字|内存占用|取值范围|
|---|---|---|---|
|字节型|byte|1个字节|-128~127|
|短整型|short|2个字节|-23768~23767|
|整型|in(默认)|4个字节|$-2^{31}$~$2^{31}-1$|
|长整型型|long|8个字节|$-2^{64}$~$2^{63}-1$|
|单精度浮点数|float|4个字节|1.4013E-45~3.4028E+308|
|双精度浮点数|double(默认)|8个字节|4.9E-324~1.7977E+308|
|字符型|char|2个字节|0~65535|
|布尔类型|boolean|1个字节|true,false|
	
注意事项：

1. 字符串不是基本类型，而是引用类型。
2. 浮点型可能只是一个近似值，并非精确的值。
3. 数据范围与字节数不一定相关，例如float数据范围比long更加广泛，但是float是4字节，long是8字节。
4. 浮点数当中默认类型是double。如果一定要使用float类型，需要加上一个后缀F。
5. 如果是整数，默认为int类型，如果一定要使用long类型，需要加上一个后缀L。推荐使用大写字母后缀。


### 类型转换

#### 强制类型转换

1. 特点：代码需要进行特殊的格式处理，不能自动完成。
2. 格式：范围小的类型 范围小的变量名 = (范围小的类型) 原本范围大的数据;

注意事项：

1. 强制类型转换一般不推荐使用，因为有可能发生精度损失、数据溢出。
2. byte/short/char这三种类型都可以发生数学运算，例如加法“+”.
3. byte/short/char这三种类型在运算的时候，都会被首先提升成为int类型，然后再计算。
4. boolean类型不能发生数据类型转换

    byte/short/char->int->long->float->double

### 包装类与基本类型

|基本类型|基本类型包装类|
|---|---|
|btye|Btye|
|short|Short|
|int|**Integer**|
|long|Long|
|float|Float|
|double|Double|
|char|**Character**|
|boolean|Boolean|

### 字符串

字符串的特点：

1. 字符串的内容永不可变。【重点】
2. 正是因为字符串不可改变，所以字符串是可以共享使用的。
3. 字符串效果上相当于是char[]字符数组，但是底层原理是byte[]字节数组。

#### 创建字符串的常见3+1种方式。

三种构造方法：

1. public String()：创建一个空白字符串，不含有任何内容。
2. public String(char[] array)：根据字符数组的内容，来创建对应的字符串。
3. public String(byte[] array)：根据字节数组的内容，来创建对应的字符串。

一种直接创建：
```java
String str = "Hello"; // 右边直接用双引号
```

注意：直接写上双引号，就是字符串对象。

### 数组

动态初始化（指定长度）：在创建数组的时候，直接指定数组当中的数据元素个数。
静态初始化（指定内容）：在创建数组的时候，不直接指定数据个数多少，而是直接将具体的数据内容进行指定。

静态初始化基本格式：
数据类型[] 数组名称 = new 数据类型[] { 元素1, 元素2, ... };

注意事项：
虽然静态初始化没有直接告诉长度，但是根据大括号里面的元素具体内容，也可以自动推算出来长度。

```java
// 静态初始化
         // 直接创建一个数组，里面装的全都是int数字，具体为：5、15、25
        int[] arrayA = new int[] { 5, 15, 25, 40 };

        // 创建一个数组，用来装字符串："Hello"、"World"、"Java"
        String[] arrayB = new String[] { "Hello", "World", "Java" };
        // 静态初始化的省略格式
        int[] array = { 10, 20, 30 };
        
        // 动态初始化一个数组
        int[] array = new int[3];
```

## OOP-封装

### 访问权限

||public|protected|default|private|
|---|---|---|---|---|
|同一类中(我自己)|YES|YES|YES|YES|
|同一包中（我邻居）|YES|YES|YES||
|不同包中的子类（我儿子）|YES|YES|||
|不同包中的无关类（陌生人）|YES||||

注意事项：(default)并不是关键字“default”，而是根本不写。


使用建议：

- 成员变量使用`private`,隐藏细节。
- 构造方法使用`public`,方便撞见对象。
- 成员方法使用`public`，方便调用方法。


### 内部类

#### 成员内部类

```java
// 外部类，要访问内部类的成员，必须建立内部类对象
class A{
    // 内部类,可以访问外部类的成员，包括私有
    class B{
    }
}

A.B b = new A().newB();
/**
* 内部类仍然是一个独立的类，在编译之后内部类会被编译成独立的.class文件，文件名会带有$符号；
* 例如上面：A.class A$B.class
*/
```
### 匿名内部类

作用：简化一个父类的继承或接口的实现；

```java
public static void main(String[] args){
    // 创建匿名内部类，直接传递给showFly(FlyAble f)
    showFyl(new FlyAble(){
        public void fly(){
                system.out.println("我飞了~~~");
        }
    });
}

public static void ShowFly(Flyable f){
        f.fly();
}
```

### 静态代码块

静态代码块的格式是：

```java
public class 类名称 {
    static {
        // 静态代码块的内容
    }
}
```

特点：当第一次用到本类时，静态代码块执行唯一的一次。
静态内容总是优先于非静态，所以静态代码块比构造方法先执行。

静态代码块的典型用途：
用来一次性地对静态成员变量进行赋值。

### 局部变量和成员变量

1. 定义的位置不一样【重点】
局部变量：在方法的内部
成员变量：在方法的外部，直接写在类当中

2. 作用范围不一样【重点】
局部变量：只有方法当中才可以使用，出了方法就不能再用
成员变量：整个类全都可以通用。

3. 默认值不一样【重点】
局部变量：没有默认值，如果要想使用，必须手动进行赋值
成员变量：如果没有赋值，会有默认值，规则和数组一样

4. 内存的位置不一样（了解）
局部变量：位于栈内存
成员变量：位于堆内存

5. 生命周期不一样（了解）
局部变量：随着方法进栈而诞生，随着方法出栈而消失
成员变量：随着对象创建而诞生，随着对象被垃圾回收而消失

### 成员变量的默认值

||数据类型|默认值|
|基本类型|整数（byte/short/int/long）|0|
||浮点数（float/double）|0.0|
||字符(char)|'\u0000'|
||布尔（boolean）|false|
|引用类型|数组、类、接口|null|

### overload

对于功能类似的方法来说，因为参数列表不一样，却需要记住那么多不同的方法名称，太麻烦。

方法的重载（Overload）：多个方法的名称一样，但是参数列表不一样。
好处：只需要记住唯一一个方法名称，就可以实现类似的多个功能。

方法重载与下列因素相关：

1. 参数个数不同
2. 参数类型不同
3. 参数的多类型顺序不同

方法重载与下列因素无关：

1. 与参数的名称无关
2. 与方法的返回值类型无关

### java bean

```java
/*
一个标准的类通常要拥有下面四个组成部分：

1. 所有的成员变量都要使用private关键字修饰
2. 为每一个成员变量编写一对儿Getter/Setter方法
3. 编写一个无参数的构造方法
4. 编写一个全参数的构造方法

这样标准的类也叫做Java Bean
 */
public class Student {

    // 成员变量
    private String name; 
    private int age; 

    public Student() {
    }

    // 构造方法
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    // 成员方法
    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

/*测试类*/
public class TextStudent {
    public static void main(String[] args){
        // 无参构造使用
        Student s = new Student();
        s.setName("XX");
        s.segAge(18);
        System.out.println(s.getName()+"---"s.getAge());
        
        // 带参构造使用
        Student s2 = new Student("XXX2",19);
        System.out.println(s2.getName()+"---"s2.getAge());
    }
}
```
## OOP-多态

### 接口

1. 如果是Java 7，那么接口中可以包含的内容有：
    1. 常量
    2. 抽象方法
2. 如果是Java 8，还可以额外包含有：
    1. 默认方法
    2. 静态方法
3. 如果是Java 9，还可以额外包含有：
    1. 私有方法

1. 成员变量其实是常量，格式：
**[public] [static] [final] 数据类型 常量名称 = 数据值;**
注意：
	常量必须进行赋值，而且一旦赋值不能改变。
	常量名称完全大写，用下划线进行分隔。

2. 接口中最重要的就是抽象方法，格式：
**[public] [abstract] 返回值类型 方法名称(参数列表);**
注意：实现类必须覆盖重写接口所有的抽象方法，除非实现类是抽象类。

3. 从Java 8开始，接口里允许定义默认方法，格式：
**[public] default 返回值类型 方法名称(参数列表) { 方法体 }**
注意：默认方法也可以被覆盖重写

4. 从Java 8开始，接口里允许定义静态方法，格式：
**[public] static 返回值类型 方法名称(参数列表) { 方法体 }**
注意：应该通过接口名称进行调用，不能通过实现类对象调用接口静态方法

5. 从Java 9开始，接口里允许定义私有方法，格式：
**普通私有方法：private 返回值类型 方法名称(参数列表) { 方法体 }**
**静态私有方法：private static 返回值类型 方法名称(参数列表) { 方法体 }**
注意：private的方法只有接口自己才能调用，不能被实现类或别人使用。

接口使用步骤：

1. 接口不能直接使用，必须有一个“实现类”来“实现”该接口。
格式：
public class 实现类名称 implements 接口名称 {
    // ...
}
2. 接口的实现类必须覆盖重写（实现）接口中所有的抽象方法。
实现：去掉abstract关键字，加上方法体大括号。
3. 创建实现类的对象，进行使用。

注意事项：
如果实现类并没有覆盖重写接口中所有的抽象方法，那么这个实现类自己就必须是抽象类。

#### 使用接口的时候，需要注意：

1. 接口是没有静态代码块或者构造方法的。
2. 一个类的直接父类是唯一的，但是一个类可以同时实现多个接口。
格式：
public class MyInterfaceImpl implements MyInterfaceA, MyInterfaceB {
    // 覆盖重写所有抽象方法
}
3. 如果实现类所实现的多个接口当中，存在重复的抽象方法，那么只需要覆盖重写一次即可。
4. 如果实现类没有覆盖重写所有接口当中的所有抽象方法，那么实现类就必须是一个抽象类。
5. 如果实现类锁实现的多个接口当中，存在重复的默认方法，那么实现类一定要对冲突的默认方法进行覆盖重写。
6. 一个类如果直接父类当中的方法，和接口当中的默认方法产生了冲突，优先用父类当中的方法。

####  类、接口、抽象方法

1. 类与类之间是单继承的。直接父类只有一个。
2. 类与接口之间是多实现的。一个类可以实现多个接口。
3. 接口与接口之间是多继承的。

注意事项：

1. 多个父接口当中的抽象方法如果重复，没关系。
2. 多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，【而且带着default关键字】。

### 多态

```java
/*
代码当中体现多态性，其实就是一句话：父类引用指向子类对象。

格式：
父类名称 对象名 = new 子类名称();
或者：
接口名称 对象名 = new 实现类名称();
 */
public class Demo01Multi {

    public static void main(String[] args) {
        // 使用多态的写法
        // 左侧父类的引用，指向了右侧子类的对象
        Fu obj = new Zi();

        obj.method();
        obj.methodFu();
    }
}
```

使用规则

1. 看new的是谁，就优先用谁，没有则向上找。
2. 口诀：编译看左边，运行看右边。
3. 父子都有，优先用子
4. 子类没有，父类有，向上找到父类
        
#### 引用类型转换

向上转型：多态本身是子类类型向父类类型向上转换的过程，这个过程是默认的。

父类类型 变量名 = new 子类类型()；
如：Animal a = new Cat();

向下转型：父类类型向子类类型向下转型的过程，这个过程是强制的。

子类类型 变量名 = (子类类型)父类变量名；
如：Cat c = (Cat) a;

ps:instanceof校验


## idea

|快捷键|功能|
|---|---|
|Alt+Enter|导入包，自动修正代码|
|C+Y|删除光标所在行|
|C++D|复制光标所在行的内容，插入光标位置下面|
|C+Alt+L|格式化代码|
|C+/|单行注释|
|C+shift+/|选中代码注释，多行注释，再按取消注释|
|Alt+ins|自动生成代码，toString/get/set等方法|
|Alt+Shift+上下箭头|移动当前代码行|

快捷键修改`Ctrl+Space`:`File->settings->keymay->main->code->complation->basic`

## packages

java.lang包下的所有类无需导入

|包名|作用||
|---|---|---|
|java.util.Scanner|文字输入|
|java.util.Random|随机生成器|
|java.util.ArrayList|可变数组|
|java.lang.String|字符串|
|java.tuil.Arrays|数组|
|java.lang.Math|数学|