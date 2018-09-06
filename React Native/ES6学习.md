---
title:   ES6学习
date: 2018-05-18 15:39:22
tags:
---

```
let  ///局部变量
var //全局变量
let [a,b,c] = [1,2,3];
```

**Class**

```
class demo {
    //构造方法
    constructor(){
    }
    //类内方法不需要function关键字
    foo() {
    
    }
    
}
typeof demo // "function"
demo === demo.prototype.constructor // true
```
上面代码表明，类的数据类型就是函数，类本身就指向构造函数。

使用的时候，也是直接对类使用new命令，跟构造函数的用法完全一致。


```
//类引用
var b = new Bar();
b.doStuff() // "stuff"
```
在子类的构造函数中，只有调用super之后，才可以使用this关键字，否则会报错

**Modules**
export default命令用于指定模块的默认输出。显然，一个模块只能有一个默认输出，因此export default命令只能使用一次。所以，import命令后面才不用加大括号，因为只可能对应一个方法。

    //Es6自定义函数方式
    getVcode = () => {
        Alert.alert('获取验证码成功');
    };


