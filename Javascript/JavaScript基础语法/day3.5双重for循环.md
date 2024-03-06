# 双重for循环

## 很多时候，单层for循环并不能满足我们的要求，比如我们要打印一个5行5列的图形，打印一个倒直角三角形，此时就可以通过嵌套for循环来实现

## 嵌套for循环：是指在一个循环语句中再定义一个循环语句的语法结构；例如在for循环中，再嵌套一个for循环，这样的for循环我们称之为双重for循环

## 1.双重for循环语法结构

```javascript
/双重for循环语法结构
for (外层的初始化变量;外层条件表达式;外层的操作表达式) {
    for (里层的初始化变量;里层的条件表达式;里层的操作表达式) {
        //里层的执行语句
    }
}
```

1. 我们可以把里面的循环看作是外层循环的语句
2. 外层循环一次，里层全部循环

```javaScript
//理解外层循环和里层循环
for (var i = 1; i <= 3; i++) {
    console.log('外层循环' + i + '次')
    for (var j = 1; j <= 3; j++) {
        console.log('里层' + j + '次')
    }
}
```

## 作业：打印5行5列星星：

```javaScript
//打印5行5列星星
var str = '';
//外层循环负责打印行数
for (var i = 1; i <= 5; i++) {
    //内层循环负责打印星星
    for (var j = 1; j <= 5; j++) {
        str = str + '★';
    }
    str = str + '\n';
}
console.log(str);
```

## 作业：打印n行n列的星星：

```javaScript
//打印n行n列的星星
//根据用户输入的行和列，在控制台打印相应数量的星星
var rows = Number(prompt('请用户输入行'));
var column = Number(prompt('请用户输入列'));
var str = '';
for (var  i = 1; i <= rows; i++) {
    for (var  j = 1; j <= column; j++) {
        str = str + '★';
    }
    str = str + '\n';
}
console.log(str);
```

## 作业：1.打印倒直角三角形

```javaScript
//打印倒直角三角形
var str = '';
for (var  i = 1; i <= 5; i++) {
    for (var j = i; j <= 5; j--) {
        str = str + '★';
    }
    str = str + '\n';
}
console.log(str);
```

解析：这里面积涉及的算法是：i=j

![image-20221201160511166](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221201160511166.png)

## 作业：2.打印倒直角三角形

```javaScript
//打印倒直角三角形
var str = '';
for (var i = 1; i <= 10 ; i++) {
    for (var j = 1; j <= i; j++) {
        str = str + '★';
    }
    str = str + '\n';
}
console.log(str);
```

解析：这里面涉及的算法是：j<=i

![image-20221201160603911](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221201160603911.png)

## 作业：3.打印9*9乘法表

```javaScript
//打印9*9乘法表
var str = '';
for (var i = 1; i <= 9; i++) //控制行数
{
    for (var j = 1; j <= i; j++) //控制每一行打印的个数
    {
        //1 x 2 = 2
        //str = str +'★';
        //str += '★';
        str += j + 'x' + i + '=' + i * j + '\t';
    }
    str = str + '\n';
}
console.log(str);
```

解析：其中需要注意的就是：j<=i。还有就是我们的公式一定要写对；当算的时候，一定更要让数字对齐，只需要更改j和i的位置即可

![image-20221201162444557](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221201162444557.png)