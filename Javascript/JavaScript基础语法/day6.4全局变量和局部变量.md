# 全局变量和局部变量

## 1.根据作用域的不同，我们的变量也分为两种：

1. 全局变量：在全局作用域下的变量，就是全局变量

   ```javaScript
   var num = 10; // 这里的num就是全局变量
   console.log(num); // 输出：10
   ```

   

2. 局部变量：在局部作用域(函数)下的变量，就是局部变量

   ```javaScript
   function getSum() {
       var num = 20; // num就是局部变量
       console.log(num); // 输出：20
   }
   getSum();
   ```

   ## 解析：在函数内部，没有声明直接赋值的变量也属于全局变量，如：

   ```javaScript
   // 在函数的内部 没有声明直接赋值的变量属于是全部变量
   function getSum() {
       var num1 = 10;
       num = 20;
   }
   getSum();
   console.log(num1); // 无法在外部输出：因为num1是局部变量
   console.log(num); // 可以在外部输出，因为num没有定义全局，直接赋值，是全局变量
   ```

## 2.我们的形参也可以看作是一个局部变量，而且这个局部变量只允许在函数的内部执行，在外部无法进行调用

```javaScript
// 这是全部变量
var num2 = 30;
console.log(aru); // 由于是aru是getSum函数的形参，因为无法在此处被调用

// 函数的形参也可以看作是一个局部变量
function getSum(aru) {
    var num = 10;
    num1 = 20;
}
getSum();
console.log(num1);
```





## 3.全局变量和局部变量的执行效率：

1. 全局变量，只有在浏览器关闭的时候，这个变量才会被销毁
2. 局部变量，只要在函数执行完成或者模块完毕时，就会直接销毁

# 注意：JS中没有块级作用域

块级作用域的含义：就是使用{}括号括起来的区域叫做块级作用域

```javaScript
// 注：在javaScript中没有块级作用域
if (3 < 5) {
    var num = 10;
}
console.log(num); // 由于javaScript中没有块级作用域，所以这里是可以调用num的
```

