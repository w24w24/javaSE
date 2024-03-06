# break和continue

## 1.continue关键字：

continue用于立即跳出本次循环，继续下一次的循环（本循环体中continue之后的代码就会少执行一次）

## 例子：我们在吃5个包子，但是在我们吃到第3个的时候，里面有虫子，所以扔掉第3个包子，继续吃第4个、第5个包子

```javaScript
for (var i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;//只要遇到continue，就直接跳出本次循环，直接执行i++
    }
    console.log('我正在吃第' + i + '个包子');

```

## 作业：计算1——100之间除了被7整除以外的其它整数的和

```javaScript
//求1——100之间 除了可以被7整除以外的整数和
var sum = 0;
for (var i = 1; i <= 100; i++) {
    if (i % 7 === 0) {
        continue;
    }
    sum += i;
}
console.log(sum);
```

## 2.break关键字

break关键字用于立即跳出整个循环（整个循环直接结束）

```javaScript
for (var i = 1; i <= 5; i++) {
    if (i === 3) {
        break;
    }
    console.log('这是第' + i + '个包子')
}
```

## 作业：平时自己多加训练即可

![image-20221201194605585](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221201194605585.png)