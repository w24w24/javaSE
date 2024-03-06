# 数组转换为字符串

## 一、数组转换为字符串的方式有哪些？

1.toString（）：把数组转化为字符串，逗号分割每一项

```javaScript
// 数组转换为字符串
var num = [1,2,3];
console.log(num.toString()); // 返回 1 ，2，3
```

2.join（'分隔符'）：这个方法用于把数组中的所有元素转换为一个子符串，中间的隔开符号可以自定义

```javaScript
var num1 = [0,1,2,3];
console.log(num1.join('★'));
```

## 二、这两种方式有什么区别？

1.相同之处：

A、都可以将数组转化为字符串

2.不同之处：

A、toString()是直接将数组转换为字符串，中间是默认使用逗号隔开的

B、join('分隔符')：在将数组转化为字符串的时候，可以自定义中间的分隔符，假如不定义，则默认为逗号



## 三、额外的数组方法使用？

1.concat：连接两个及其以上数组数组

```javaScript
// concat连接两个及其以上数组
var num = [1,2,3];
var num1 = [4,5,6];
var num2 = [7,8,9];
var num3 = num.concat(num1,num2);
console.log(num3);
```

2.slice(begin，end)：数组截取，并且返回被截取的数组元素

```javaScript
// slice数组截取
var num = [1,2,3,4,5,6,7,8,9,10];
var num1 = num.slice(3,5);
console.log(num1); // 输出：因为遵循左闭右开原则，所以输出4，5
```

3.splice(begin,要删除的个数)：返回被删除项目的新数组，注意，这个会影响原数组

```javaScript
// splice数组截取
var num = [1,2,3,4,5,6,7,8,9,10];
var num1 = num.splice(3,5);
console.log(num1); // 从索引号为3开始，删除5个元素
```