# 作用域

## 一、JS作用域定义：就是代码名字(变量)在某个范围内起作用和效果，目的是为了提高和程序的可靠性，更重要的是减少命名冲突

## 二、JS的作用域(es6之前)：全局作用域、局部作用域

1. 全局作用域：整个Script标签，或者是整个JS文件中

   ```javaScript
   var num = 10; // 这就是全局作用域下的num变量
   ```

2. 局部作用域(函数作用域)：在函数内部的就是局部作用域，这个代码的名字只在函数的内部起作用或效果

   ```javaScript
   function getSum() {
       // 局部作用域
       var num = 10;
       console.log(num);
   }
   getSum();
   ```

   ```javaScript
   // 全局作用域
   var num = 10;
   console.log(num);
   
   // 局部作用域
   function getSum() {
       var num = 20;
       console.log(num);
   }
   getSum();
   
   // 输出的结果互不影响，全局作用域和局部作用域的名字话互不影响
   ```

解析：由于局部作用域和全局作用域的的范围不同，即使是名字冲突，也不会相互影响

