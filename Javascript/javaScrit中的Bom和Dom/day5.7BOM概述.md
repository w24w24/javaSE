# BOM概述

## 一、什么是BOM

解析：BOM（Browser Object Model）即浏览器对象模型，提供了独立于内容而与浏览器窗口进行交互的对象，其核心是window。如：页面后退、窗口刷新、滚动条滚动等等

BOM的构成：BOM是由一系列的对象构成，并且每个对象都提供了很多的方法和属性。但是要注意，BOM是缺乏标准的，javaScript语法的标准化组织是ECMA，DOM的标准化是W3C，BOM最初是Netscape浏览器标准的一部分

所以BOM存在兼容性问题：所以接下来我们学习的是一些没有兼容性问题，使用比较好的BOM

## 二、DOM和BOM的区别

DOM：

1. 文档对象模型
2. DOM就是把文档当作一个对象来看待
3. DOM的顶级对象是document
4. DOM学习的主要是操作页面元素
5. DOM遵循W3C标准规范

BOM：

1. 浏览器对象模型
2. 把浏览器当作一个对象来看
3. BOM的顶级对象是window
4. BOM学习的是一些与浏览器窗口交互的一些对象
5. BOM是浏览器厂商在各自浏览器上定义的，兼容性差

## 三、BOM的构成

![Javascript学习之BOM介绍_干的漂亮的博客-CSDN博客](https://img-blog.csdnimg.cn/6cfa509367f7453e8e52a025d27832a9.png)

解析：BOM比DOM更大，包含了DOM

window对象是浏览器的顶级对象，具有双重角色：

1.是JS访问浏览器窗口的一个接口

2.是一个全局对象，定义在全局作用域中的变量、函数都会变成window对象的属性和方法

```javascript
var num = 10;
console.log(num);//以前的调用方式
console.log(window.num);//由于定义在全局作用域中的变量、函数都会变成window对象的属性和方法,所以标准是window.num
```

```javascript
function fn() {
    console.log(11);
}
fn();//原始的调用方法
window.fn();//使用window.fn()进行调用
```

解析：在调用的时候可以省略window，前面学习的对话框都属于window对象方法，比如alert（）、prompt（）等等

注意：window的下一个特殊属性：window.name【也就是说尽量不要使用var name = 10；这种方式来声明变量，因为name是一个特殊的保留字】