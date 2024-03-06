# Date时、分、秒的日期格式化

## 一、获取当前时间的小时、分钟、秒数

```JavaScript
// Date日期：获取当前时间的时、分、秒
var nowDate = new Date(); // 必须先要实例化Date日期对象

var hour =nowDate.getHours(); // 获取当前时间的小时数
console.log(hour);

var minute = nowDate.getMinutes(); // 获取当前时间的分钟数
console.log(minute);

var second = nowDate.getSeconds(); // 获取当前时间的秒数
console.log(second);
```

## 二、作业1：要求封装一个函数，然后返回当前的时、分、秒

```javaScript
// 要求封装一个函数，返回当前的时、分、秒
function getTime() {
    // 先实例化对象，然后再获取到时间：
    var nowDate = new Date();
    var hour =nowDate.getHours(); // 获取当前时间的小时数
    var minute = nowDate.getMinutes(); // 获取当前时间的分钟数
    var second = nowDate.getSeconds(); // 获取当前时间的秒数
    // 返回我们获取到的时间：
    return '当前时间是：' + hour + ':' + minute + ':' + second;
}
var nowTime = getTime();
console.log(nowTime); // 但是在返回的时间里，我们对于小于10的，需要在前面补上一个0，对于大于10的，则不补0，这该怎么改进呢？
```

改进：

```javaScript
// 要求封装一个函数，返回当前的时、分、秒
function getTime() {
    // 先实例化对象，然后再获取到时间：
    var nowDate = new Date();
    var hour =nowDate.getHours(); // 获取当前时间的小时数
    hour = hour < 10 ? '0' + hour : hour;

    var minute = nowDate.getMinutes(); // 获取当前时间的分钟数
    minute = minute < 10 ? '0' + minute : minute;

    var second = nowDate.getSeconds(); // 获取当前时间的秒数
    second = second < 10 ? '0' + second : second;
    // 返回我们获取到的时间：
    return '当前时间是：' + hour + ':' + minute + ':' + second;
}
var nowTime = getTime();
console.log(nowTime);
```

解析：其实就是利用三元表达式来做的，因为三元表达式要比if...else要简单得多

上述得原理就是：当小时、分钟、秒数小于10的时候，就在前面加0，如果大于就不加，其实这很好理解，这将和后面我们制作倒计时的任务相联系