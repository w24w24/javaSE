# 简单数据类型、复杂数据类型传参

## 1.简单数据类型传参：

## 首先，函数的形参数也可以看作是一个变量，当我们把一个值类型变量作为参数传递给函数的形参时，其实是把变量在栈空间里面的值复制一份给形参，那么在方法内部对于形参做任何修改，都不会影响到外部变量

![image-20221223153221143](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221223153221143.png)

```javaScript
// 简单数据类性传参
function fn(a) {
    a++;
    console.log(a);
}
var x = 10;
fn(x);
console.log(x);
```

## 2.复杂数据类型传参：

![image-20221223153915515](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221223153915515.png)