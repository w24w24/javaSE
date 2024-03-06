# 数组转化为字符串

## 在进行数组的元素的变化的时候，这个例子是非常重要的

```javascript
// 数组转化为分割字符串
var arr = ['blue','red','black','brown'];
var str = '';
for (var i = 0; i < arr.length; i++) {
    str +=  arr[i] + '|';
}
console.log(str);
```

解析：使用过一个空的变量str，然后在遍历数组之后，将所需要变化的部分变化就可以了