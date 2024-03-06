# 构造函数和对象的区别

```javaScript
// 构造函数：
function Start(uname,age,sex) { 
    this.name = uname;
    this.age = age;
    this.sex = sex;
    this.sing = function(sang) {
        console.log(sang);
    }
}
// 实例化对象：
var ldh = new Start('刘德华',18,'男');
```



## 一、构造函数和对象的区别？

1.构造函数：如Star()，抽象了对象的公共部分，封装到函数里面，它泛指某一大类

2.创建对象：如new Star()，特指某一个，通过new关键字创建对象的过程我们称之为实例化

如：下图就是构造函数和实例化对象的例子：



![image-20221216110201547](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221216110201547.png)