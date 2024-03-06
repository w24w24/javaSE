# 数据类型分类

## JS中把数据类型分为两类：

1. 简单数据类型：Number、String、Boolean、Undefined、Null
2. 复杂数据类型：Object

## 1.number数字型：

```javaScript
var num = 10;//数字型
var PI =3.1415926535;//数字型

//八进制：我们使用在数字前面使用0来表示八进制
//八进制：0~7
var num = 012;//表示10
var num = 015;//表示13

//十六进制：我们在数字前面加0x来表示十六进制
//0~9 a~f
var num = 0x9;//表示9
var num = 0x13;//表示19
```

## JS中的数字型的最大值和最小值

```javaScript
//概念：
alert(Number.MAX_VALUE);//1.7976931348623157e+308
alert(Number.MIN_VALUE);//5e-324

//实际表示：
//数字的最大值
console.log(Number.MAX_VALUE);
//数字的最小值
console.log(Number.MIN_VALUE);
```

## 数字型的3个特殊值

```javaScript
//概念：
alert(Infinity);//代表无穷大，大于任何数字
alert(-Infinity);//代表无穷小，小于任何数字
alert(NaN);//NOt a Number 代表一个非数值

//实际表示：
//由于上述已经是数字的最大值了，那么再想要它再大，已经是不可能的了，所以是无穷大
console.log(Number.MAX_VALUE * 2);//表示无穷大
//假设在无穷大之前加上负号，那么就会让我们的数字出现无穷小的情况
console.log(-Number.MAX_VALUE * 2);//表示无穷小
```

## 非数值

```javaScript
//非数值
console.log('pink老师'-100);//输出：NaN【由于我们的字符串和数值是无法计算的，所以得出的结果就是非数值】
```

## isNaN

```javaScript
//isNaN 这个方法是用来判断是否是数字的，如果不是数字，那么就返回true，如果是，就返回false
console.log(isNaN(12));//返回false
console.log(isNaN('pink老师'));//返回true
```

## 2.String字符串类型

```javaScript
//JS中的字符串类型无非就是单引号和双引号
var str = 'pink老师';
var str1 = 'Hello';
```

### 注意：在JS中是可以进行单引号和双引号嵌套的，但是一定要注意规则；

```javaScript
//正确写法：
var str = '我是一个"高富帅"程序员';
var str = "我是一个'高富帅'程序员";

//错误写法：
var str = '我是一个'高富帅'程序员';
var str = "我是一个"高富帅"程序员";
var str = '我是一个高富帅程序员";//直接报错，不可以单双引号搭配

```

### 由于JS中对于不加字符串的语法会默认为JS语法，假设你写的是字符串，但是没加引号，就会默认为JS语法，但是JS中又没有这种语法，所以会直接报错

