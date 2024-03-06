# return终止函数，一次只允许返回一个值

## 例子：

```javaScript
// return终止函数
function getArr(num1,num2) {
    return num1+ num2; // return后面的代码不会被执行
    alert('我是不会被执行的'); // 由于上面的return 已经终止了程序，于是这句语句也不会再被执行
}
console.log(getArr(1,2));
```

注：return只可以返回一个值，即使有多个值被逗号隔开，也只是默认为最后一个值为返回值，但是怎么解决这个问题呢？【我们使用数组输出】

```javaScript
// return只可以返回一个值
function getSum(num1,num2) {
    return num1,num2; // 只有最后一个值会被返回
}
console.log(getSum(1,2)); // 只是返回最后一个值
```

使用数组输出：

```javaScript
// 避免return只输出一个值
function getSum(num1,num2) {
    // 使用数组的方式进行输出:
    return [num1 + num2 , num1 -num2 , num1 / num2 , num1 * num2];
}
getSum(3,1);
console.log(getSum(3,1));
```

注：在使用数组的方式进行输出的时候。就已解决了return只可以输出一个值的情况



# 函数返回值的两个注意事项

## 1.我们的函数假如有return，则返回函数后面的值，假如没有return，则返回undefined

```javaScript
// 有return的情况
function getSum(num1,num2) {
    return num1; // 有返回值 则返回return后面的值
}
console.log(getSum(1,2)); //

// 没有return的情况
function getSums(num1,num2) {
    // 没有返回值 则返回undefined
}
console.log(getSums(3,4));
```



## break、continue、return之间的区别：

1. break：结束当前循环体(如：while、for)
2. continue：跳出本次循环，继续执行下次循环(如：for、while)
3. return：不仅可以退出循环，还可以返回return中的值，同时结束当前函数体内的代码