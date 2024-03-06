# 函数的定义

## 使用场景：在JS中，可能会定义非常多相同功能或者功能相似的代码，这些代码可能需要大量重复使用；虽然for循环也可以实现一些重复性的操作，但是比较局限，此时就可以使用JS中的函数

## 目的：让大量代码重复使用

## 函数：就是封装了一段可以被重复执行调用的代码块

```javaScript
// 函数演示
function getSum(num1,num2) {
    var sum = 0;
    for (var i = num1; i <= num2; i++) {
        sum += i;
    }
    console.log(sum);
}
// 直接调用即可
getSum(1,100);
getSum(10,50);
```