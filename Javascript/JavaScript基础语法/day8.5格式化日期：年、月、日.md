# Date年、月、日的日期格式化

这样的代码：

```javaScript
var now = new Date('2019-10-1 8:8:8');
console.log(now);
```

然后输出：Date Tue Oct 01 2019 08:08:08 GMT+0800 (中国标准时间)

#### 上述这这种日期的表现形式并不符合我们的浏览习惯，我们想要这样的日期形式：2022-12-17 14:35:23，我们应该怎么做呢？

![image-20221217140121262](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221217140121262.png)

```javaScript
// 使用date进行输出学习：
var nowYear = new Date();
console.log(nowYear.getFullYear()); // 获取年份 2022
console.log(nowYear.getMonth() + 1); // 获取月份 12【这是因为月份是从0月开始的，所以需要 + 1】
console.log(nowYear.getDate()); // 获取当天日期 17
console.log(nowYear.getDay()); // 获取当前星期 6【注：周一返回1 ，周六返回6，但是周日返回0】
```

### 现在想要返回清晰可辨的日期：

```javaScript
// 使用date输出完整，清晰的时间：
var nowYear = new Date();
console.log('当前日期为：' + nowYear.getFullYear() + '年' + (nowYear.getMonth() + 1) + '月' + nowYear.getDate() + '日，' + '星期' + nowYear.getDay());
```

解析：为了增强程序的可维护性，可以把我们的日期都使用变量来进行表示，然后再引用就可以了，如：

```javaScript
// 为了后续的可维护性，可以这样来书写语句：
var nowYear = new Date();
var year = nowYear.getFullYear();
var month = nowYear.getMonth() + 1;
var day = nowYear.getDate();
var week = nowYear.getDay();
console.log('今天的日期是：' + year + '年' + month + '月' + day + '日' + '星期' + week); // 但是一个问题就是，星期我们一般喜欢使用一、二、三来代替1、2、3，所以这个部分我们应该怎么改进呢？
```

改进：

```javaScript
var nowYear = new Date();
var year = nowYear.getFullYear();
var month = nowYear.getMonth() + 1;
var day = nowYear.getDate();
var arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六'];
var date = nowYear.getDay();
console.log('今天的日期是：' + year + '年' + month + '月' + day + '日' + arr[date]);
```

解析：由于星期是从星期天（0）开始的【因为外国默认星期天是一个星期的开始】，所以创建一个数组：`['星期日','星期一','星期二','星期三','星期四','星期五','星期六']`，之后再将获取到的星期的小写数字，作为数组的索引值`arr[date]`，即可输出想要的大写模式的星期了