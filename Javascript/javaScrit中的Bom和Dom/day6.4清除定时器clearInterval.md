# 清除定时器：clearInterval()

## 一、清除定时器：clearInterval()

```javascript
//清除定时器
window.clearInterval(intervalID);
```

解析：clearInterval()方法取消了先前通过调用setInterval()建立的定时器

## 注意：

1.window可以省略

2.里面的参数就是定时器的表示符

```javascript
<button class="begin">开启定时器</button>
<button class="stop">停止定时器</button>
<script>
    //1.获取按钮
    var begin = window.document.querySelector('.begin');
    var stop = window.document.querySelector('.stop');
    //2.定时器开启
    var timeBegin = null;//全局变量 null是一个空对象
    begin.addEventListener('click',function() {
        timeBegin = window.setInterval(function() {
            console.log('你好吗？');
        },1000);
    });
    stop.addEventListener('click',function() {
        window.clearInterval(timeBegin);
    });
</script>
```

