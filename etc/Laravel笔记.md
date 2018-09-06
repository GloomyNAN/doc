---
title:  Laravel笔记
date: 2018-06-19 14:26:49
tags: 
---

## 安装

### 1、创建项目

    composer create-project laravel/laravel weixin-public_account --prefer-dist "5.1.*"

### 安装工具

    composer global require "laravel/installer"

### 添加环境变量
    
    export PATH=$PATH:~/.composer/vendor/bin/

### hemostead box
    
    https://atlas.hashicorp.com/laravel/boxes/homestead/versions/2.1.0/providers/parallels.box
    https://atlas.hashicorp.com/laravel/boxes/homestead/versions/2.1.0/providers/virtualbox.box

<!-- more -->
### Laravel创建表迁移+model
    
    php artisan make:model --migration Post

运行迁移

    php artisan migrate

插入数据库

    php artisan db:seed

生成一个空的控制器

    php artisan make:controller BlogController --plain

建立多对多关系

    php artisan make:migration --create=post_tag_pivot create_post_tag_pivot

清除配置缓存

    php artisan config:cache

composer更新自动加载

    composer dump-autoload


> 问题描述：
> 查询数据不能save();因为主键为ID，我 设置成了id
> isDirty getDirty


##  查询构造器

### 使用查询构造器插入数据

返回布尔类型

```
DB::table('as_admin')->insert(array('name' => jason,'age' => 18));
```

返回插入的id

```
DB::table('as_admin')->insertGetId(array('name' => jason,'age' => 18)); 
```

插入多条数据


```
DB::table('as_admin')->insert(array(array('name' => jason,'age' => 18),array('name' => jason2,'age' => 18))); 
```


###使用查询构造器更新数据

返回影响的行数

```
DB::table('as_admin')->where('id', 12)->update(array('age' => 18));
```

字段自增3写，默认为1法 返回影响的行数

```
DB::table('as_admin')->where('id', 12)->increment('age', 3);
```

字段自减3写，默认为1法 返回影响的行数

```
DB::table('as_admin')->where('id', 12)->decrement('age', 3); 
```

自增或自减的

```
DB::table('as_admin')->where('id', 12)->decrement('age', 3, array('name' => '张佳宁'));
``` 

###使用查询构造器删除数据

返回删除的行数

```
DB::table('as_admin')->where('id', 12)->delete();
```

删除id>=12的数据

```
DB::table('as_admin')->where('id', '>=', 12)->delete(); 
```

get() 获取表中所有数据

```
$students = DB::table('student')->get();
```

first() 获取第一条数据（随机）,配合orderBy 一起使用

```
$students =  DB::table('student')->orderBy('id','asc')->first();
```

where 多条件查询

```
$students = DB::table('student')
      ->whereRaw('id >= ? and age > ?',[18,20])
      ->get();
```

pluck 取结果集中一列特定列，返回字符串类型

```
$students = DB::table('student')->pluck('id','name','age');
```

lists 按照Key=>value 对 的方式返回数组；最多两个参数，第一个参数作为value,第二个做为key。一个参数时与pluck用法一样

```
$students = DB::table('student')
      ->whereRaw('id >= ? and age > ?',[18,20])
      ->lists('id','name','age');
```

select() 指定查询的字段

```
$students = DB::table('student')
        ->select('id','name','age')
        ->get();
```

chunk() 方法 指定一次返回多少条，后跟闭包（匿名函数）

```
echo '<pre>';	//预格式化
DB::table('student')->chunk(2,function($students){
  var_dump($students);
});
dd($students);
```

##聚合函数

返回记录数

```
DB::table('as_admin')->select('id','name','age')->count();
```

最大值，min同理

```
DB::table('as_admin')->select('id','name','age')->max('age');
```
      
返回平均值      

```
DB::table('as_admin')->select('id','name','age')->avg('age');
```

返回指定字段数据

```
DB::table('as_admin')->select('id','name','age')->sum('sum');
```

##数据库操作 - Eloquent ORM 查询数据

1.创建Model类型 方法里面声明两个受保护属性:$table(表名)和\$primaryKey(主键)

```<?php
namespace App;
use Illuminate\Database\Eloquent\Model;
class Student extends Model{
  protected $table = 'student';
  protected $primaryKey = 'id';
}
?>
```

2.Controller里面以 类名::方法 (静态方法)的风格进行操作数据库

```
<?php
namespace App\Http\Controllers;
use Illuminate\Support\Facades\DB;
use App\Student;
class StudentController extends Controller{
  public function orm1() {
    echo '<pre>';
    // all 通过orm获取所有数据
    // $result = Student::all();

    // find 通过主键返回指定的数据
    // $result = Student::find(1001);

    // findOrFail 通过主键返回指定的数据 未查找到到则抛出异常
    // $result = Student::findOrFail(1001);

    // 获取符合条件的数据
    // $student = (Student::where('age', '<', 20)->get())['tables'];

    // 分段式(分页)获取数据递交给闭包函数循环处理
    // Student::chunk(2, function($student) {
    // 	var_dump($student);
    // });

    // 查询构造器之聚合函数
    $result = Student::count();
    dd($result);
  }
}
?>
```

## 视频课程记录

```
// 新增
$bool = DB::insert（'insert into student(name,age) values(?,?) ['imooc',19]'）
var_dump($bool);

// 更新
$num = DB::update('update student set age = ? where name = ?',[20,'sean]);
var_dump($num);

// 查询 
$students = DB::select('select * from student where id > ?',[1001]);
dd（$students）;

// 删除
$bool = DB::delete('delete from student where id >?',[1001]);
dd($bool)
```



