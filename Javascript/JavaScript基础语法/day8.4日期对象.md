# Date日期对象

## 一、首先来了解一下构造函数和对象之间的关系？

```javaScript
// 构造函数和数组、对象之间的关系
var arr = new Array(); // 创建了一个数组对象
var obj = new Object(); // 创建了一个对象实例
```

解析：由于Array代表的是数组的意思，所以在上述的代码中表示的就是创建了一个`数组对象`；又因为Object代表的对象的意思，所在上述中的代码代表的是创建`对象实例`

## 二、Date方法的使用？

### 1.获取当前时间必须实例化：

```javaScript
// 日期对象的实例化
var now = new Date();
console.log(now);
```

解析：在Date(这里没有参数)中的时候，返回的是当前的时间；返回的这个时间并不会实时变化，而是固定死的

### 2.Date(参数)中，参数的几种参数书写形式？

1. 数字型：

   ```javaScript
   // 日期中的数字型
   var now = new Date(2019,10,1); 
   console.log(now); // 为什么返回的月份是 11月
   ```

2. 字符型：

   ```javaScript
   // 日期中的字符型
   var now = new Date('2019-10-1 8:8:8'); 
   console.log(now); // 返回的日期和参数里面的是一致的
   ```

