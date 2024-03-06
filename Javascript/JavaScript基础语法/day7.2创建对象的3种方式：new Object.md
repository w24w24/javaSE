# 创建对象的3种方式：第二种：new Object

## 一、利用new Object创建对象

```javaScript
// 利用new Object创建对象：

var obj = new Object(); // 利用new Object创建一个空的对象

// 之后对new Object创建的空的对象追加属性和方法：
obj.name = '可可';
obj.age = 10;
obj.sex = '男';
obj.sayHi = function() {
    console.log('hi~');
}
// 输出 
console.log(obj.name);
console.log(obj['age']);
obj.sayHi();
```

总结：

1.我们利用等号 = 赋值的方法，添加对象的属性和方法

2.每个属性和方法之间，使用分号结束

## 作业1：

![image-20221215155028422](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221215155028422.png)

```javaScript
// 作业
var obj = new Object();
obj.name = '鸣人';
obj.sex = '男';
obj.age = 18;
obj.skill = function() {
    console.log('影分身');
}
```