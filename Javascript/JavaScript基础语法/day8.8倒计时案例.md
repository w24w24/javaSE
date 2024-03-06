# 倒计时案例

## 一、制作一个倒计时效果：

![image-20221217191156253](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221217191156253.png)

## 分析：

倒计时的核心算法：`就是用输入的是时间减去现在的时间就是剩余的时间，即倒计时；但是不要能拿着时分秒相减，比如：05分减去25分就会是负数`,所以怎样避免这种情况呢？

答：

1. 使用时间戳来做，用户输入时间的总毫秒数减去现在的时间的总的毫秒数，得到的就是剩余时间的毫秒数

2. 把剩余的毫秒数字转化为天、时、分、秒（时间戳转换为时分秒），但是我们应该怎么转换呢？

   解析：使用转换公式：

   ```javaScript
   // 使用转化公式
   day = parseInt(总的毫秒数 / 60 / 60 /24); // 转换天数
   hour = parseInt(总的毫秒数 / 60 / 60 % 24); // 转换小时
   minute = parseInt(总的毫秒数 / 60 % 60); // 转换分钟
   second = parseInt(总的毫秒数 % 60); // 转换秒
   ```

## 二、开始书写

```javaScript
// 写一个倒计时
function countDown(time) {
    var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
    var inputTime = +new Date(time); // 返回的是用户输入时间总的毫秒数
    var times = (inputTime - nowTime) / 1000; /*times是剩余时间总的
    秒数【由于1秒等于1000毫秒，所以除以1000就是当前的秒数】*/
    var day = parseInt(times / 60 / 60 / 24);
    day = day < 10 ? '0' + day : day;
    var hour = parseInt(times / 60 / 60 % 24);
    hour = hour < 10 ? '0' + hour : hour;
    var minute = parseInt(times / 60 % 60);
    minute = minute < 10 ? '0' + minute : minute;
    var second = parseInt(times % 60);
    second = second < 10 ? '0' + second : second;
    return day + '天' + hour + '小时' + minute + '分钟' + second + '秒';
}

var time = countDown('2023-12-17 22:00:00');
console.log(time);

var date = new Date();
console.log(date);
```

解析：

1. 先返回当前时间总的毫秒数，再返回用户输入时间总的毫秒数
2. 由于用户输入的时间毫秒数必定是大于当前时间毫秒数的，因为只有大于当前时间毫秒数，才可能形成倒计时的情况
3. 为了得到我们想要的倒计时，只要使用用户输入的时间毫秒数减去当前的时间毫秒数，就的到了剩余的时间毫秒数；但是这还是毫秒数，想要得到秒，需要进行转换【因为1秒 = 1000 毫秒】，所以使用剩余的时间毫秒数除以1000，就将剩余时间转换为了秒
4. 再者就是使用公式转换为天、小时、分钟、秒【注意：想要在前面添加多0，就需要使用到三元表达式进行转换】
5. 再返回最终的结果即可