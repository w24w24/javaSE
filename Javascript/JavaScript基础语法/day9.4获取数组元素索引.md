# 获取数组元素索引

## 一、数组元素索引方法

1.indexOf()：数组中查找给定元素的第一个索引【即只返回第一个元素的索引号】，如果存在，则返回索引号，如果不存在，则返回-1

```javaScript
// 获取数组元素索引
var arr = ['red','blue','pink','brown'];
var arr1 = arr.indexOf('pink');
console.log(arr1);
```

A、为什么说只返回第一个元素的索引号？

解析：对于上述代码，数组元素中没有一个元素是重复的，但是对于数组元素中有重复的元素，我们在使用indexOf的时候，这个时候返回的也只是第一个出现的元素的索引号，如下：

```javaScript
// 获取数组元素索引
var arr = ['red','blue','pink','brown','red'];
var arr1 = arr.indexOf('red');
console.log(arr1);
```

B、什么时候会返回-1的情况？

解析：假设在数组元素中，没有我们想要寻找的元素，但是我们还是使用indexOf去寻找了，由于数组中没有，于是就会返回-1，如下：

```javaScript
// 获取数组元素索引
var arr = ['red','blue','gray','brown'];
var arr1 = arr.indexOf('pink');
console.log(arr1);
```

2.lastIndexOf()：在数组中的最后一个索引，如果存在，则返回索引号，如果不存在，则返回-1

解析：在上述我们使用indexOf的时候，查找数组中元素的索引号的时候，是从0开始查找的；但是在使用lastIndexOf的时候，它的数组元素索引方式是从最后一个元素开始查找的，这就是indexOf和lastIndexOf之间的区别

```javaScript
// 获取数组元素索引
var arr = ['red','blue','gray','brown','pink'];
var arr1 = arr.lastIndexOf('pink');
console.log(arr1);
```

