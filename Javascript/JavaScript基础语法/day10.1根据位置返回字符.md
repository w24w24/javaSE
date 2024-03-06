# 根据位置返回字符【重点】



![image-20221221202206024](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221221202206024.png)

## 一、和“根据字符返回位置”的区别？

1.charAt()：根据位置返回字符，如下：

```javaScript
// 根据位置返回字符
 var arr = 'andy';
console.log(arr.charAt(3));
// 遍历所有的字符
for (var i = 0; i < arr.length; i++) {
    console.log(arr.charAt(i)); // 这里的i是索引号
}
```

解析：

A.根据位置返回字符：返回的是字符，用的是charAt('索引号')

B.根据字符返回位置：返回的是索引号，用的是indexOf('字符'，索引号)

2.charCodeAt()：根据位置返回字符，返回的值是ASCII值【目的：判断用户按下的键是什么，后期可以用来监听键盘】

```javaScript
// 根据位置返回字符
 var arr = 'andy';
console.log(arr.charCodeAt(3)); // 返回的是ASCII值 目的：判断用户按了哪一个键
```

3.str[index]：根据位置返回字符，HTML5新增特性，可能浏览器不支持

```javaScript
// 根据位置返回字符
 var arr = 'andy';
console.log(arr.str[3]); // 由于是新特性，浏览器不支持
```