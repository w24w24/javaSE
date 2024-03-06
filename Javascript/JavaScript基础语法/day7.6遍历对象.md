# 遍历对象

```javaScript
// 对象的遍历
var obj = {
    name: '谭磊',
    age: 18,
    sex: '男'
}
console.log(obj.name);
console.log(obj.age);
console.log(obj.sex);
```

## 一、什么遍历？

解析：就是对创建的对象或者数组红的值进行全部输出打印

## 二、除了传统的for循环遍历之外，还有什么是可以快速遍历对象的？

解析：使用for....in

```javaScript
// for...in的语法格式：
for(变量名字 in 对象) {}
```

```javaScript
// 对象的遍历
var obj = {
    name: '谭磊',
    age: 18,
    sex: '男'
}
// console.log(obj.name);
// console.log(obj.age);
// console.log(obj.sex);


// 使用for...in来解决对象的遍历问题：
// for...in的语法格式：
// for(变量名字 in 对象) {}
for(var key in obj) {
    console.log(key); // 输出变量，得到的是 属性名
    
    console.log(obj[key]); // 输出对象，得到的是属性值
}
```

## 三、总结？

1.对象可以让代码结构清晰

2.对象复杂数据类型object

3.对象本质：对象就是一组无序的相关属性和方法的集合

4.构造函数：构造函数泛指某一大类，比如：青苹果、红苹果，但是不管红苹果还是青苹果都是苹果

5.对象实例化特指一个事物，比如：这个苹果、你的爸爸和妈妈

6.for...in用于对对象的属性进行循环操作





## 四、作业？

1.创建一个电脑对象，该对象要有颜色、重量、品牌、型号，并且可以看电影、听音乐、打游戏和敲代码

2.创建一个按钮对象，该对象中要包含宽、高、背景颜色和点击行为

3.创建一个车的对象，该对象要有重量、颜色、牌子，可以载人、拉货、耕田

4.写一个函数，实现翻转任意数组

5.写一个函数，实现对数字、数组的排序

6.制作一个简易计算器：要求如下图：

![image-20221216145045958](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221216145045958.png)