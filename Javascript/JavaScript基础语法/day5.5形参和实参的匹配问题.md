# 实参和形参的匹配问题

## 在JS中，形参和实参的个数可以不一样，但是会出现一下问题：

1. 如果实参的个数多于形参：

   ```javaScript
   // 实参的个数多于形参
   function getSum(num1,num2) {
       console.log(num1 + num2);
   }
   getSum(1,2,3); // 传入的参数个数取决于形参的个数
   ```

2. 如果形式参数的个数多于实际参数：

   ```javaScript
   // 形式参数的个数多于实际参数
       function getSum(num1,num2) {
           console.log(num1 + num2);
       }
       // 由于实际参数的个数小于形式参数，所以只传入num1
       // 同时由于num2可以看作是一个没有声明的变量，且值为undefined
       // 所以num1 + num2 的值是NaN
       getSum(1); // 输出：NaN
   ```

## 注：

1. 尽量让实参的个数和形参的个数相匹配
2. 在JS中，形参的默认值是undefined
3. 函数可以带参数也可以不带参数
4. 声明函数的时候，函数名括号里面的是形参，形参的默认值是undefined
5. 形参的个数和实参的个数不匹配，但是结果不可预计，我们尽量要匹配

