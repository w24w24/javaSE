# 构造函数创建对象

## 一、我们为什么要使用构造函数创建对象？

解析：

1. 因为我们之前的两种创建对象的方式，一次只能创建一个对象
2. 我们一次创建一个对象，里面的很多属性和方法都是相同的，我们只能复制
3. 因此我们可以利用函数的方法，重复这些相同的代码，我们就把这个函数称之为构造函数【既然是函数，为什么不直接叫做函数，要叫做构造函数呢？】这是因为这个函数不一样，里面封装的不是普通的代码，而是对象

## 二、构造函数？

构造函数：是一种特殊的函数，主要是用来初始化对象的，即为对象成员变量赋初始值，它总是与new运算符一起使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这一个函数里面

## 三、构造函数的语法格式？

```javaScript
// 构造函数的语法格式
function 构造函数名() {
    this.属性;
    this.方法 = function() {}
}
new 构造函数名();
```

```javaScript
// 构造函数的语法格式
/* function 构造函数名() {
     this.属性;
     this.方法 = function() {}
 }
 new 构造函数名();
 */



// 创建四大天王的的对象：相同的属性：姓名、年龄、性别 相同的方法：唱歌
function Start(uname,age,sex) { // 这里是接收实参的形参
    this.name = uname; // 这里的 this 是指向形式参数中的实参的,下面的也是一样的
    this.age = age;
    this.sex = sex;
    this.sing = function(sang) {
        console.log(sang);
    }
}

var ldh = new Start('刘德华',18,'男'); // 这里是传递实参给到形参
console.log(ldh.name);
console.log(ldh['age']);
ldh.sing('冰雨');

// 想要再传递其他的参数，只需要使用再创建一个对象就可以了
var zxy = new Start('张学友',19,'男');
console.log(zxy.name);
console.log(zxy['age']);
zxy.sing('李香兰');
```

## 注意：

## 1.构造函数首字母要大写；

## 2.构造函数不需要return就可以返回结果；

## 3.我们在调用构造函数的时候，必须要使用new关键字；

## 4.我们只要new Start()调用函数就创建了一个对象 ：ldh {}或者对象 ：zxy {}

## 5.我们的属性和方法前面必须要加this







## 作业1：

![image-20221215163919723](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221215163919723.png)

```javaScript
// 利用构造函数创建两个英雄对象
function Hero(name,type,blood) {
    this.name = name;
    this.type = type;
    this.blood = blood;
    this.attack = function(attack) {
        console.log(attack);
    }
}

var hero1 = new Hero('英雄名字：后羿','英雄类型：射手型','基础血量：100血量');
console.log(name);
hero1.attack('远程');

var hero2 = new Hero('英雄名字：廉颇','英雄类型：坦克型','基础血量：200血量');
hero2.attack('近战');
```