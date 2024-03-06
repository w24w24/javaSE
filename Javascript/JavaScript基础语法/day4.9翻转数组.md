# 翻转数组

## 将数组元素['pink','teacher','red','brown']进行翻转：

## 最后形成一个新数组：

```javaScript
// 翻转数组
var arr = ['pink','teacher','red','brown'];
var arr1 = [];
for (var i = arr.length - 1; i >= 0; i--) {
    arr1[arr1.length] = arr[i];
}
console.log(arr1);
```

注：在数组中，要注意的是arr.length和数组索引号是不一样的；arr.length表示的是数组的元素的个数，而索引号表示的是数组的下标，是从0开始的