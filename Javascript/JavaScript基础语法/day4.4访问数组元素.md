# 访问数组中的元素

## 一、获取数组元素

### 1.数组的索引

索引(下标)：用来访问数组元素的序号(数组下标记从0开始)

```javascript
var arr = ['小敏','小强','小红','小李'];
console.log(arr);// 这是获取数组中对的所有元素
console.log(arr[2]);// 这是获取数组中下标为2的元素
```

### 2.在数组元素这里，访问就是获取、得到的意思

### 3.当索引超出数组元素的时候

```javaScript
// 定义一个数组
var arr = [1,2,3,'pink老师',true];
// 通过访问数组中的下标遍历元素
console.log(arr[0]);
console.log(arr[1]);
console.log(arr[2]);
console.log(arr[3]);
console.log(arr[4]);
console.log(arr[5]);
```

解析：由于所以超出了数组的元素，在显示的时候就是undefined

## 数组作业练习：

要求：定义一个数组。里面存放星期一到星期日（共7天），最后在控制台输出星期日