# 猜数字游戏

![image-20221216205107935](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221216205107935.png)

```javaScript
// 随机数字游戏
function getRandomIntInclusive(min,max) {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min + 1)) + min;
}

var random = getRandomIntInclusive(1,5);
while (true) { // 注意：这是一个死循环
    var string = Number(prompt('你来猜，请输入一个1~10之间的数字：')); // 注意此处，经常使用失误
    if (random > string) {
        alert('您输入的数字小了');
    }else if (random < string) {
        alert('您输入的数字大了');
    }else if (string === null) {
        alert('您没有输入任何内容哦');
    }else if(random === string) {
        alert('这你都猜对了');
        break;
    }else {
        alert('输入的不是数字，请重新输入');
    }
}
```

## 作业2：要求用户猜1~50之间的数字，只有10次机会

