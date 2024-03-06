# 替换字符串以及转换为数组

## 一、字符替换：replace

```javaScript
// 字符串替换 replace
var str = 'andy';
console.log(str.replace('a','b')); // 第一个a是要被替换的参数，第二个要替换成的参数
```

```javaScript
// 字符串替换 replace
var str = 'andy';
console.log(str.replace('andy','baby')); // 第一个a是要被替换的参数，第二个要替换成的参数
```

解析：替换单一字符和多字符都是支持的

## 1.作业1：要求把字符abcoefoxyoozzopp，要求把里面所有的o替换为*

```javaScript
// 字符替换
var str = 'abcoefoxyoozzopp';
while (str.indexOf('o') !== -1) {
    str = str.replace('o','*');
}
console.log(str);
```

## 二、字符转换为数组：split('分隔符')【前面学习的join是将数组转换为字符】

```javaScript
// 字符转换为数组
var arr = 'red,pink,brown,blue';
console.log(arr.split(',')); // split(',')表达的是原字符用的什么符号，这里就使用什么符号
```

解析：注意使用的时候，需要十分注意分隔符是什么意思？它的意思是原字符串使用什么符号，这里就是用什么符号

## 三、课下

![image-20221223144756808](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221223144756808.png)

## 四、作业

![image-20221223144816597](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221223144816597.png)