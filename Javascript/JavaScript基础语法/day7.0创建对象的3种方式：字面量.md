# 创建对象的3种方式：第一种：字面量创建

## 一、在javaScript中，现阶段我们采用3种方式创建对象(Object)：

1. 利用字面量创建对象
2. 利用new Object创建对象
3. 利用构造函数创建对象

注：再引入字面量：小括号()是运算符字面量，中括号[]是数组字面量，花括号{}是对象字面量

## 二、创建对象：

```javaScript
// 创建对象：
var obj = {
    uname: '张三疯',
    age: 18,
    sex: '男',
    sayHi: function() {
        console.log('Hi');
    }
}

// 注：在创建对象的时候，要使用花括号；而且每个值之间采用键值对的形式；每个值之间使用逗号隔开
```

### 三、调用对象（2种方式）：

```javaScript
// 第一种调用方式：
// 调用对象的属性，我们采用 对象名.属性名
console.log(obj.uname);
console.log(obj.age);

// 第二种调用方式：
// 对象['属性名']，注意方括号里面的属性值必须加引号
console.log(obj['uname']);
console.log(obj['age']);

// 解析：其中的 . 我们理解为...的
// 如：obj.uname 为 obj的uname
```

## 四、调用函数方法：

```javaScript
// 调用函数方法：
// 对象里面的方法调用：对象.方法名()，注意方法名后
obj.sayHi();
```

解析：函数的调用和属性的调用是一样的逻辑，但是在由调用的是函数，所以需要在函数名后面添加小括号【注：小括号是必须要添加的】





## 作业1：使用字面量创建一个对象:

![image-20221215133458758](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221215133458758.png)

```javaScript
// 请使用字面量的形式创建一个名字为可可的狗的对象
var obj = {
    dogName: '可可',
    dogType: '阿拉斯加',
    dogAge: '5岁',
    dogColor: '棕红色',
    bark: function() {
        console.log('汪汪汪');
    },
    showFilm: function() {
        console.log('演电影');
    }
}
// 随机打印几个信息：
console.log(obj['dogName']);
obj.bark();
obj.showFilm();
```

## 注意：花括号{}采取键值对的形似：

1. 键：相当于属性名
2. 值：相当于属性值，可以是任意类型的值（数字类型、字符串类型、布尔类型、函数类型）

