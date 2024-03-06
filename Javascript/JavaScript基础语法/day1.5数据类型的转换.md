# 数据类型的转换

## 含义：使用表单、prompt获取过来数据类型是默认是字符型的，这个时候就不可以进行简单的加减法运算，而需要转化变量的数据类型。通俗来说就是一种数据类型的变量转换为另一种数据类型

# 常用的三种数据类型的转化

## 转换为字符串类型：

## 1.var num = 10;num.toString();

```javaScript
//数字型转换为字符串
var num = 10;
console.log(typeof num);//输出：number

var str = num.toString();//使用toString转换为字符型
console.log(typeof str);//输出：string
```

## 2.强制转化：var num = 10;String(num);

```javaScript
//数字型转换为字符串
var num = 10;
var array = String(num);
console.log(typeof array);//输出：string
```

## 3.利用+号拼接字符串转换为字符型：var num = 10;alert(num+'pink老师');

```javaScript
//利用字符拼接字符串转换数据类型
var num = 25;
var array = num + '岁数的你已经毕业了';
console.log(typeof array);//输出：string
```

## 基于上述三种转化方式都是可以进行数据类型的转换的，但是在使用的时候我们更喜欢使用第三种，这种转换方式也是被称之为：隐式转换



## 转换为数字型

## 1.parseInt(string)函数：将string类型转换为整数数值型

```javaScript
//将string转换为整型数字类型
var num = '15';
console.log(typeof num);//输出：string
var num1 = parseInt(num);
console.log(typeof num1);//输出：number

//注意以下这几种也是可以的：
var num = prompt('请输入年龄');
console.log(parseInt(num));
console.log(parseInt('3.102'));//输出：3 取整
console.log(parseInt('3.902'));//输出：3 取整
console.log(parseInt('120px'));//输出：120 去掉单位px
console.log('rem120px');//输出：NaN
```

## 2.parseFloat(string)函数：将string类型转换为浮点数类型

### 使用方法同上述：parseInt(string)函数一致

## 3.number(变量名字)

```javaScript
//Number数字类型转换
var array = '15';
console.log(Number(array));
```

## 4.隐式转换

```javaScript
//隐式转换:利用算数运算 - * /
console.log('122' * 1);
console.log('12' - 0);
```

## 作业：

### 计算年龄要求：

1. 弹出一个输入框(prompt)，让用户输入出生的年份
2. 把用户输入的值用变量保存起来，然后使用今年的年份减去出生年份，就是用户的年龄
3. 弹出警示框(alert)，把计算结果输出

```javaScript
//弹出一个输入框(prompt),让用户输入出生年份
//把用户输入的值用变量保存起来，然后使用今年的年份减去变量值，就是年龄
//弹出警示框(alert)，把计算的结果输出

var year = prompt('请输入您的出生年份');
var age = 2022 - year;//year 取过来是字符串型 但是这里用的是减法 隐式转换
alert('您今年的年龄是：' +  age + '岁了！');
```

### 计算两个数值相加要求：

1. 弹出第一个输入框架，让用户输入值
2. 再弹出第二个输入框，让用户输入第二个值
3. 最后弹出警示框，将用户两次输入相加的值展现出来

```javaScript
//1.弹出第一个输入框
var num = prompt('请输入第一个值：');
//2.弹出第二个输入框
var num1 = prompt('请输入第二个值：');
//对两次输入的值进行相加操作
var num2 = Number(num) + Number(num1);
//输出两次输入的值的和
alert(num2);
```

## 转换为布尔型

## 1.直接使用boolean()函数【1.代表空、否定的值会被转换为false，如：""、0、NaN、null、undefined；2.其余都会被转换为true】

```javaScript
//转换为布尔型：以下情况是全部输出为false
console.log(Boolean(''));
console.log(Boolean(0));
console.log(Boolean(null));
console.log(Boolean(undefined));
console.log(Boolean());
```

