# arguments的用法及其规则

## 一、当我们不知道有几个参数传递的时候，就可以使用arguments来获取，在JS中，arguments实际上是当前函数的一个内置对象，所有函数都内置了一个arguments对象，arguments对象中存储了传递的所有实参

## 二、arguments的展示形式是一个伪数组，因此可以进行遍历，为数组具有以下特点：

1. 具有length属性

   ```javaScript
   // arguments的使用及其规则
   function getSum() {
       console.log(arguments.length);
   }
   getSum(1,2,3,4,5,6,7);
   ```

2. 按照索引方式存储数据、可以使用数组的遍历属性

   ```javaScript
   // arguments的使用及其规则
       function getSum() {
           for (var i = 0; i < arguments.length; i++){
               console.log(arguments[i]);
           }
           console.log(arguments[i]);
       }
       getSum(1,2,3,4,5,6,7);
   ```

3. 不具有数组的push和pop等方法

## 1.arguments的语法使用

```JavaScript
// arguments的使用规则及其语法
function getSum() { // 由于我们不知道需要传递几个实参，于是就不好定义形参的个数
    console.log(arguments); // 为了解决形参个数的定义问题，我们使用arguments
}
getSum(1,2,3,4,5); // 传递了5个实际的参数
```

解：在arguments中存储了所有传递过来的实参

## 2.arguments的使用，只有函数才有，而且每个函数都内置好了arguments对象





## 1.利用函数求任意个数字的最大值

```javaScript
// 利用函数求解任意个数的最大值
function getMax() {
    var max = arguments[0];
    for (var i = 0; i < arguments.length; i++) {
        if (arguments[i] > max) {
            max = arguments[i];
        }
    }
    return max;
}
getMax(1,2,4,8,4,84,562,65,62,322,6);
```

## 2.利用函数封装的方法，翻转任意一个数组

```javaScript
// 利用函数封装的方法 翻转任意一个数组
// [1,2,3,4,5]=====>[5,4,3,2,1]
function getRe(arr) {
    var re = [];
    for (var i = arr.length - 1; i >= 0; i--) {
        re[re.length] = arr[i];
    }return re;
}
var arr1 = getRe([1,2,3,4,5]);
console.log(arr1);
```

## 3.利用函数封装的方法，对数组进行排序（冒泡排序）

```javaScript
// 利用函数封装的方法 对数组进行排序（冒泡排序）
function getSum(num) {
    for (var i = 0; i < num.length-1; i++) {
        for (var j = 0; j < num.length-i-1; j++) {
            if (num[j] > num[j+1]) {
                var change = num[j];
                num[j] = num[j+1];
                num[j+1] = change;
            }
        }
    }return num;
}
var arr1 = getSum([12,75,66,57,5,442,52,0]);
console.log(arr1);
```

## 4.利用函数判断闰年

```javaScript
// 利用函数封装的思想，判断是否是闰年
function getYear(year) {
    if (year % 4 === 0 && year % 100 !== 0) {
        alert(year + '年是闰年');
    }else {
        alert('今年是平年');
    }return year;
}
var years = getYear(Number(prompt('请输入年份：')));
console.log(years);
```

```javaScript
// 利用函数封装的思想，判断是否是闰年
function isYear(year) {
    var flag = false;
    if  (year % 4 === 0 && year % 100 !== 0) {
        flag = true;
    }return flag;
}
console.log(isYear(2008)); // 判断2008年是闰年
```
