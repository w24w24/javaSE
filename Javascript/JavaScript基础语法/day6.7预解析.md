# 预解析（所有的代码都会出现预解析）

```javaScript
// 预解析四问：

// 第一问：直接输出
console.log(num); // 未定义 num，直接输出 num

//第二问：先输出 num，再定义 num 【坑1：undefined】
console.log(num);
var num = 10;

// 第三问：定义一个函数，然后变换输出的位置
fn(); // 也可以放置在此处（可以运行）
function fn() {
    console.log(11);
}

// 第四问：使用函数表达式，变换输出的位置
fn1(); // 放置在此处（不可以运行） 【坑2：报错】
var fn1 = function() {
    console.log(22);
}
```

## 一、为什么会出现上述情况？

javaScript代码是由浏览器中的javaScript解析器来执行的，javaScript解析器在运行javaScript代码的时候分为两步：预解析和代码执行

## 2.预解析：JS引擎会把JS里面所有的var 还有function提升到当前作用域的最前面

## 3.代码执行：按照代码的书写顺序从上往下执行

## 二、预解析分为：变量预解析（变量提升）和函数预解析（函数提升）

## 1.变量提升（变量预解析）：就是把所有的变量声明提升到当前作用域的最前面，不提升赋值

```javaScript
//第二问：先输出 num，再定义 num 【坑1：undefined】
console.log(num);
var num = 10;

// 上述这两行代码相当于是执行了以下操作：
var num;
console.log(num); // 所以在控制台会输出：undefined
num = 10;
```

```javaScript
// 第四问：使用函数表达式，变换输出的位置
fn1(); // 放置在此处（不可以运行） 【坑2：报错】
var fn1 = function() {
    console.log(22);
}

// 上述这两行代码相当于是执行了以下操作：
var fn1;
fn1();
fn1 = function {
    console.log(22); // 所以在控制台直接报错
}
```

## 2.函数提升（函数预解析）：就是把所有的函数声明提升到当前作用域的最前面，不提升函数

```javaScript
// 第三问：定义一个函数，然后变换输出的位置
fn(); // 放置在此处（可以运行）
function fn() {
    console.log(11);
}

// 上述代码相当于是执行了以下操作：
function fn() {
    console.log(11);
}
fn();
```





## 1.预解析案例：

```javaScript
// 预解析案例：
var num = 10;
fn();
function fn() {
    console.log(num);
    var num = 20;
}

// 相当于执行了以下操作：
var num;
function fn() {
    var num;
    console.log(num); // 输出：undefined
    num = 20;
}
num = 10;
fn();
```

## 2.经典预解析案例：

```javaScript
// 经典预解案例
fn();
console.log(c);
console.log(b);
console.log(a);
function fn() {
    var a = b = c = 9;
    console.log(a);
    console.log(b);
    console.log(c);
}



// 预解析后：
function fn() {
    // var a = b = c = 9;相当于是：
    // var a = 9, b = 9, c = 9【b和c没有声明当作全局变量来看】

    // 并不是：
    // var a = 9, var b = 9, var c = 9

    // 集体声明：
    // var a = 9, var b = 9, var c = 9【使用逗号隔开】
    
    var a;
    a = b = c = 9;
    // 或者是：
    // a = 9;局部变量
    // b = 9;全局变量
    // c = 9;全局变量
    console.log(a); // 输出：9
    console.log(b); // 输出：9
    console.log(c); // 输出：9
}
fn();
console.log(c); // 输出：9
console.log(b); // 输出：9
console.log(a); // 报错
```