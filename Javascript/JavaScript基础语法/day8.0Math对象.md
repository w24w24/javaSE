# Math对象

## 一、为什么要学习Math对象？

解析：因为在之后的实际开发中，我们经常用到求最大值、最小值、随机数等等

## 二、什么是Math？

解析：Math是一个数学对象，但是它不是一个构造函数（这是因为：构造函数需要new一个实例化对象，但是Math不用，直接使用即可），比如：

```javaScript
// Math是一个数学对象，但不是一个构造函数，所以直接调用就可以了
// 例如：我们想要输出PI的值
console.log(Math.PI); // 直接使用输出即可
```

```javaScript
// 使用数学方法中的Math.max方法
console.log(Math.max(1,2,44,4,415));
console.log(Math.max(-1,-25,-2,-35));
console.log(Math.max(1,52,'pink老师'));
console.log(Math.min()); // 输出的是：infinity
console.log(Math.max()); // 输出的是：-infinity
```

## 三、Math概述？

解析：Math对象不是构造函数，它具有数学常数和函数的属性和方法，跟数学的相关运算（求绝对值、取整、最大值等等）可以使用Math中的成员

```javaScript
// Math对象中的常用成员
Math.PI;// 圆周率
Math.max()/min();// 求最大值和最小值
Math.abs();// 绝对值
Math.round();// 四舍五入，就近取整【注意：-3.5，结果是：-3】
Math.ceil();// 向上去整【往最大了取值】
Math.floor();// 向下取整【往最小了取值】
```

解析：floor是地板的意思，也就是小；而ceil是天花板的意思，也就是大

### 注意：在实际的程序运行中，我们的`.5`是很特殊的，对于整数而言，是很遵循四舍五入的规则的；但是对于负数而言，只要是负数的`.5`就会往大了取值，对于不是负数`.5`的情况，依旧遵循四舍五入的情况

