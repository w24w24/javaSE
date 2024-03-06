# 函数可以调用用另外一个函数

## 1.定义：因为每个函数都是独立的代码块，用于完成特殊的任务，因为会经常用到函数调用的情况（如：一两车，车的轮胎可以看作是一个独立的代码块，发动机也可以看作是一个独立的代码块；但是想要让这辆车动起来，需要发动机和轮胎相互调用）

```javaScript
// 函数之间是可以相互调用的
function fn1() {
    console.log(11);
    fn2(); // 在这一个函数里面调用fn2
}
fn1(); // 只是调用就可以了

function fn2() {
    console.log(22);
}
```

## 2.函数之间是可以相互调用的

```javaScript
// 函数之间是可以相互调用的
function fn1() {
    console.log(111);
    fn2();
    console.log('fn1');
}
function fn2() {
    console.log(222);
    console.log('fn2');
}
fn1(); 
// 注意代码的执行顺序也是非常重要的
```



## 作业1：写一个程序，用户输入年份，输出当前年份2月份的天数

## 方法一：【程序单独运行输出：】

```javaScript
// 写一个程序 用户输入年份 如果是闰年，就输出29天；是平年就输出28天
function getYear() {
    var years = Number(prompt('请输入年份：'));
    if (years % 4 === 0 && years % 100 !== 0 || years % 400 === 0) {
        alert(years + '是闰年\n且' + years + '年的2月份有29天');
    }else {
        alert(years + '是平年\n且' + years + '年的2月份有28天');
    }
    return years;
}
getYear();
```

解析：如果用用户输入的是闰年，那么2月份就有29天；如果用户输入的年份是平年，那么2月份就有28天

## 方法二：【函数调用输出：】

```javaScript
// 写一个判断输出年份的性质的：
function isRunYear(year) {
    // 如果是闰年，则返回true 是平年则返回false
    var flag = false;
    if (year % 4 === 0 && year % 100 !== 0 || year % 400 === 0) {
        flag = true;
    }return flag;
}

// 写一个输出年份及其天数的：
function backDay() {
    var year = Number(prompt('请输入年份：'));
    if (isRunYear(year)) { // 调用函数需要加小括号
        alert('当前年份是闰年，且2月份有29天');
    }else {
        alert('当前年份是平年，且2月份有28天');
    }
}
backDay();
```