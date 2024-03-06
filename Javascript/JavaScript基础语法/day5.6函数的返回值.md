# 函数的返回值

## 1.函数的返回值的定义：函数只是一个是实现某种功能的代码，输出语句一般不可以在函数的内部，我们希望谁调用这个函数，结果就给到谁【也就是说一个厨师（函数），只管将客人（调用者）点的菜炒了之后给到客人，而不是自己在厨房里面吃掉】

## 2.语法格式及其应用：

```javaScript
// 函数的返回值
function getResult() {
    return 666;
}
getResult(); // 这是调用者
console.log(getResult()); // 函数名字 + 小括号
```

```javaScript
// 函数的返回值
function arr() {
    return '大肘子'; // 返回的值
}
arr(); // 只是调用
console.log(arr()); // 在控制台打印
```

​	

```javaScript
// 求任意两个数的和
function getSum(num1,num2) {
    return num1 + num2;
}
console.log(getSum(1,2)); // 注意：这里面的实参要在这里进行传入
```







## 作业1：利用函数求两个数的最大值

```javaScript
// 利用函数求两个数的最大值
function num(num1,num2) {
    if (num1 > num2) {
        return num1;
    }else {
        return num2;
    }
}
console.log(num(3,10));
```

## 作业2：求数组元素的最大值

```javaScript
// l利用函数求数组[1,22,334,44,8,74,54,55,7784,232]中的最大值
function getSum(arr) {
    var max = arr[0]; // 需要在此处拿到数组的第一个值来进行比较
    for (var i = 0; i <= arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i]; // 替换两两比较后的最大值
        }
    }return max; // 属于是function的返回值，所以需要写在此处
}
var re = getSum([1,22,334,44,8,74,54,55,7784,232]);
console.log(re);
```

注：在使用函数的时候，需要特别注意函数只是一个求某个事件的模板，需要调用，而且在使用的时候，需要十分注意每一句语句的位置和作用，特别是在实际的开发中，我们经常使用一个变量来接收函数的返回结果，使用更加简单