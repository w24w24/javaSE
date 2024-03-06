# 检测是否为数组的两种方式

## 一、理解数组的实际参数传入？

```javaScript
// 翻转数组
function reverse(arr) {
    var newArray = []; // 先建立一个空的数组
    for (var i = arr.length - 1; i >= 0; i--) {
        newArray[newArray.length] = arr[i];
    }
    return newArray;
}
console.log(reverse([1,2,3,4,5])); // 但是这一个数组有缺陷，那就是传入的参数必须是数组
```

在上述代码中，参数的传入必须是数组，假如不是数组，就会返回空的数组形式

```javaScript
// 翻转数组
function reverse(arr) {
    var newArray = []; // 先建立一个空的数组
    for (var i = arr.length - 1; i >= 0; i--) {
        newArray[newArray.length] = arr[i];
    }
    return newArray;
}
console.log(reverse([1,2,3,4,5])); // 但是这一个数组有缺陷，那就是传入的参数必须是数组
console.log(reverse(1,2,3)); // 当前传入的不是数组的形式，所以在控制台输出的是空的数组形式
```

![image-20221218163137257](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221218163137257.png)

## 二、怎么解决送入的参数必须是数组的形式这一问题呢？

### 1.检测是否为数组：

#### 一、第一种方式（使用instanceof来进行判断，然后使用if语句进行设计）：

1. instanceof 运算符【instanceof（实例）：翻译成中文就是一个判断词语，即A是类B的实例】

2. 但是我们应该怎么使用instanceof呢？如下：

   ```javaScript
   var num = []; // 由于我们定义了一个数组 所以输出：true
   var num1 = {}; // 由于这是一个对象，所以输出：false
   console.log(num instanceof Array);
   console.log(num1 instanceof Array);
   ```

   ```javaScript
   // 翻转数组
   function reverse(arr) {
       if (arr instanceof Array) {
           var newArray = []; // 先建立一个空的数组
           for (var i = arr.length - 1; i >= 0; i--) {
               newArray[newArray.length] = arr[i];
           }
           return newArray;
       }else {
           return 'error:返回的参数必须是数组形式，例如：[1,2,3]';
       }
   }
   ```



解析：使用instanceof判断是否属于数组形式，假如属于，就执行相应的操作，假如不属于，就提示用户输入正确的数组格式

#### 三、第二种方式：（使用MDN提供的关键字：Array.isArray(参数名)来进行判断是否是数组）：

1. 首先，这是Array里面提供的一个判断方法，使用的语法是：Array.isArray(参数名)来进行判断是否属于数组，如果属于，就返回true，如果不属于，就是返回false
2. 但是具体我们应该怎么使用这一个方法呢？如下：

```javaScript
// 使用：Array.isArray(参数名)来进行判断是否是数组

var num = []; // 由于我们定义了一个数组 所以输出：true
var num1 = {}; // 由于这是一个对象，所以输出：false
console.log(Array.isArray(num));
console.log(Array.isArray(num1));
```

```javaScript
// 翻转数组
function reverse(arr) {
    if (Array.isArray(arr)) {
        var newArray = []; // 先建立一个空的数组
        for (var i = arr.length - 1; i >= 0; i--) {
            newArray[newArray.length] = arr[i];
        }
        return newArray;
    }else {
        return 'error:返回的参数必须是数组形式，例如：[1,2,3]';
    }
}
```

## 四、insatanceof和isArray的区别？

解析：

1.当在检测Array实例的时候，`Array.isArray`是要优先于`instanceof`的，因为`Array.isArray`可以检测iframes

2.Array.isArray是可靠准确的方法，是ES5新增的方法，兼容IE9和IE9以上浏览器。IE9以下浏览器是不支持的
