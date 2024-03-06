# 数组中新增元素

## 在JS中有两种方法可以新增元素：

1. 一种就是修改我们的length长度来新增元素
2. 索引号增加数组元素

## 1.修改length长度来新增数组元素

```javaScript
// 修改length长度来新增数组元素
var arr = ['red','blue','black'];
console.log(arr.length); // 一定是含有 3 个元素
arr.length = 5; // 手动给元素长度增加到 5
console.log(arr);
console.log(arr[3]); // 输出：undefined
console.log(arr[4]); // 输出：undefined
```

## 2.通过修改数组索引新增数组元素

```javaScript
// 修改索引号新增数组元素 追加数组元素
var arr = ['red','blue','black'];
arr[3] = 'pink'; // 追加数组元素
arr[4] = 'teacher'; // 追加数组元素
console.log(arr);

// 假设数组的下标被占用 那么再使用索引号，那么就是替换
arr[1] = 'brown';
console.log(arr);

// 假设直接给数组名赋值，就会直接替换数组中的所有元素
arr = '你好帅呀！';
console.log(arr);
```

解析：

1. 可以通过修改数组索引的方式追加数组元素
2. 不可以直接给数组名赋值，否则会覆盖以前的所有数据

## 作业1：数组存放1—10个整数：

```javaScript
// 数组新增元素
var arr = [];
for (var i = 0; i < 10; i++) {
    arr[i] = i + 1;
}
console.log(arr);
```

解析：使用for循环来增加数组



## 作业2：将数组[2,0,6,1,77,0,52,0,25,7]中大于等于10的元素筛选出来，放入新的数组里面去

```javaScript
// 方法1：筛选元素

// 筛选数组中的元素
var arr = [2,0,6,1,77,0,52,0,25,7];
var arr1 = [];
var j = 0;
// 把数组中大于等于 10 的元素选出来放入新的数组
for (var i = 0; i < arr.length; i++) {
  if (arr[i] >= 10) {
      // 新数组索引号应该从 0 开始，依次递增
      arr1[j] = arr[i];
      j++;
  }
}
console.log(arr1);
```

```javaScript
// 方法2：筛选元素

// 筛选数组中的元素
var arr = [2,0,6,1,77,0,52,0,25,7];
var arr1 = [];
// 由于arr1中没有任何的元素，所以arr1.length的长度是 0
// 把数组中大于等于 10 的元素选出来放入新的数组
for (var i = 0; i < arr.length; i++) {
  if (arr[i] >= 10) {
      // 由于arr1.length的长度为0，所以在存入元素的时候自增
      arr1[arr1.length] = arr[i];
  }
}
console.log(arr1);
```

解析：

1. 新数组的索引应该是从0开始的，并且是依次递增的
2. 在解决问题的时候，需要一步一步的往前走，不要乱了逻辑思维

## 作业3：删除指定的数组元素：

要求：将数组[2,0,6,1,77,0,52,0,25,7]中为0的元素去掉，输出一个不含0的新数组

```javascript
// 删除指定的数组元素
var arr = [2,0,6,1,77,0,52,0,25,7];
var arr1 = [];
for (var i = 0; i < arr.length; i++) {
    if (arr[i] !== 0) {
        arr1[arr1.length] = arr[i];
    }
}
console.log(arr1);
```

​                                                                                                  
