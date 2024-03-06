# 倒计时效果

## 一、案例：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210221171942186.png)

## 二、核心思路：

1.这个倒计时是不断变化的，因此需要定时器来自动变化（setInterval）

2.四个黑色盒子里面放的分别是天、小时、分钟、秒

3.四个黑色盒子分别利用innerHTML放入计算的天、小时、分钟、秒

4.当页面第一次进入执行的时候，也是属于间隔毫秒数的，因此刚刷新时候页面会有空白【解决：先调用一次这个函数，这样就不会留下空白界面了】

5.最好采用封装函数的形式，这样可以先调用一次函数，防止刚刷新页面有空白问题

```html
<!--    这里是css代码-->
    <style>
        .day,.hour,.minute,.second{
            width: 200px;
            height: 100px;
            color: #fff;
            background-color: black;
            display: inline-block;
            text-align: center;
            line-height: 100px;
            font-weight: 600;
            font-size: 24px;
        }
    </style>
</head>
<body>
<div>
    <span class="day">0</span>
    <span class="hour">1</span>
    <span class="minute">2</span>
    <span class="second">3</span>
</div>
<script>
    //1.获取天、小时、分钟、秒
    var day = window.document.querySelector('.day');
    var hour = window.document.querySelector('.hour');
    var minute = window.document.querySelector('.minute');
    var second = window.document.querySelector('.second');
    //获取用户输入的日期
    var inputTime = +new Date("2023-2-13 16:52:00");//添加+号是将时间转换为毫秒形式
    countDown();//先调用一次这个函数，防止第一次刷新页面有空白
    window.setInterval(countDown,1000);//定时器
    //倒计时思路和函数
    /*
    1.获取规定的时间毫秒数
    2.获取当前时间毫秒数
    3.规定时间毫秒数字 - 当前时间毫秒数
    4.利用公式转化为天、小时、分钟、秒
    */
    function countDown() {
        var nowTime = +new Date();
        var times = (inputTime - nowTime) / 1000;
        if(times >= 0) {
            //利用以下公式转换为天、小时、分钟、秒
            var d = parseInt(times / 60 / 60 / 24);
            d = d < 10 ? "0" + d : d;
            var h = parseInt((times / 60 / 60) % 24);
            h = h < 10 ? "0" + h : h;
            var m = parseInt((times / 60) % 60);
            m = m < 10 ? "0" + m : m;
            var s = parseInt(times % 60);
            s = s < 10 ? "0" + s : s;
            //将时间赋值div
            window.day.innerHTML = d + '天';
            window.hour.innerHTML = h + '时';
            window.minute.innerHTML = m + '分';
            window.second.innerHTML = s + '秒';
        }
    }

</script>
```