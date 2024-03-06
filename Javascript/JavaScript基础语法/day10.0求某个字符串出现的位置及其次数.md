# 求某个字符出现的位置及其次数

## 一、作业1：

1.查找字符串：dasjdjadhajdaj

2.核心算法：先查找出第一个j的位置

3.然后，只要indexOf返回的结果不是-1，就继续往后查找

4.因为indexiOf只可以查找到第一个，所以后面的查找，一定是当前索引值加1，从而继续查找

```javaScript
// 返回字符的位置
var arr = 'dasjdjadhajdaj';
var arr1 = arr.indexOf('j'); //查询j并且返回位置的值
var num = 0;
while (arr1 !== -1) {
    console.log(arr1);
    num++;
    arr1 = arr.indexOf('j',arr1 + 1);
}
console.log('j出现的次数是:' + num);
```