# Math随机数方法：4种方式

## 一、Math.random()返回一个浮点数【注：不规定整数，那就返回浮点数】

### 1.不规定参数的范围，随机返回数字：

```javaScript
// Math.random()随机浮点数字 0 <= x < 1
// 这个方法里面不跟参数
// 代码验证
function getRandom() {
  return Math.random();
}
var random = getRandom();
```

### 2.规定一个区间，随机返回这个区间里面的数值：

```javaScript
// 规定一个区间，随机返回这个区间的任意一个数：
function getRandomArbitrary(min,max) {
    return Math.random() * (max - min) + min;
}
var random = getRandom(1,10);
console.log(random);
```

### 3.规定一个区间，随机返回这个区间的任意整数（不包含两边的数字）：

```javaScript
// 规定一个区间，随机返回这个区间的任意整数
function getRandomInt(min,max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min)) + min;
}
var random = getRandom(1,10);
console.log(random);
```

### 4.规定一个区间，随机返回这个区间的任意整数（需包含两边的数字）：

```javaScript
// 规定一个区间，随机返回这个区间的任意整数
function getRandomIntInclusive(min,max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
var random = getRandom(1,10);
console.log(random);
```



## 作业1：随机点名

```javaScript
// 随机点名
function getRandomIntInclusive(min,max) {
    min = Math.ceil(arguments[0]);
    max = Math.floor(arguments[arguments.length - 1]);
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
var arr = ['小明','小李','小红','小华'];
console.log(arr[getRandomIntInclusive(0,4)]);
```

解析：为了让我们的程序更加动态化和科学性，假如还要在后面增加名字，所以需要让区间更加人性化，即：

```javaScript
// 随机点名
function getRandomIntInclusive(min,max) {
    min = Math.ceil(arguments[0]);
    max = Math.floor(arguments[arguments.length - 1]);
    return Math.floor(Math.random() * (max - min + 1)) + min;
}
var arr = ['小明','小李','小红','小华'];
console.log(arr[getRandomIntInclusive(0,arr.length - 1)]);
```

解析：其实就是让数组的元素动态化变化