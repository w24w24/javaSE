# 拼接以及截取字符串

![image-20221221215421109](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221221215421109.png)

1.第一个就是concat拼接字符：

```javaScript
// concat拼接字符串
var num = [1,2,3];
var num1 = [4,5,6];
var num2 = [7,8,9];
var arr = num.concat(num1,num2);
console.log(arr);

// 或者是
console.log(num.concat(55,66));
```

2.第二个就是substr(start，length)：

```javaScript
var num = '改革春风吹满面';
console.log(num.substr(2,2)); // 注意：此处的substr只是针对字符串
```