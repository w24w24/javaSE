# 函数的使用

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

## 1.函数在使用的时候分为两步：

1. 声明函数

   结构：

    	

   ```javaScript
   // 函数的使用
   function 函数名 () {
       // 函数体
   }
   // function是声明函数的关键字，全部小写
   // 函数是做某件事情，所以函数名一般是动词，如：getSum
   // 函数不调用，自己不执行
   ```

2. 调用函数

   结构：

   ```javaScript
   // 函数调用
   函数名字();
   
   // 调用函数的时候必须 要加小括号
   ```

## 函数的封装：把一个或者多个功能通过函数的方式封装起来，对外只提供一个简单的函数接口【即:封装类似于将电脑配件整合组装到机箱中(类似于快递打包)】

 

## 作业1：利用函数计算1—100之间的累加和

要求：必须使用函数来计算

```javaScript
// 利用函数计算1-100之间的累加和
function getSum(num1,num2) {
    var sum = 0;
    for (var i = num1; i <= num2; i++) {
        sum += i;
    }
    console.log(sum);
}
getSum(1,100);
```

## 问题回答？

1. 函数是做什么的？
2. 声明函数使用什么关键字？
3. 如何调用函数？
4. 封装是什么意思？
