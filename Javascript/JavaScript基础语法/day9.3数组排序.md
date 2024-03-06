# 数组排序

## 一、数组排序的两种方法

1.reverse() ：颠倒数组中元素的顺序，无参数；   该方法会改变原来的数组，返回新的数组

```javaScript
var arr = [1,5,4,8,3];
arr.reverse();
console.log(arr);
```

2.sort()：对数组的元素进行排序，该方法会改变原来的数组，返回新的数组

```javaScript
var arr = [1,5,4,8,3];
arr.sort();
console.log(arr);
```

## 二、sort的用法

解析；对于个位数的数字排序，sort是可以完成的，但是对于多位数的排序，sort就不那么好用了，如下:

```javaScript
// sort的用法和变化
var arr = [1,3,2,5,8,9,6,4];
arr.sort();
console.log(arr); // 对于个位数来说，sort是可以完成排序的

// 但是对于双位数，sort就不能解决排序方式了，需要添加函数
var arr1 = [1,5,44,54,58,52,844];
arr1.sort(function(a,b) {
    return a - b; // 使用a-b表示的是升序的排列方式;b-a是降序的排列方式
});
console.log(arr1);
```

解析：在sort里面添加函数，一个是a，一个是b，使用a-b表示的是升序排列；使用b-a表示的是降序排列