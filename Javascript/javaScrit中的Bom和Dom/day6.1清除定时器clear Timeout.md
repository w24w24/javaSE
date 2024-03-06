# 清除定时器：clear.setTimeout

## 一、停止Timeout()定时器：

```javascript
window.clearTimeout(timeout ID)
```

解析：clearTimeout()方法取消了先前通过调用setTimeout()建立的定时器

```html
<!--    这里是css代码-->
    <style>
        img{
            width: 100px;
            height: 100px;
        }
    </style>
</head>
<body>
<button>点击我停止定时器</button>
<script>
    var btn = window.document.querySelector('button');
    //爆炸计时器：
    function startSetTime() {
        console.log('已经停止');
    }
    var fn = window.setTimeout(startSetTime,2000);//给定时器设置一个名字fn
    
    //停止爆炸按钮
    btn.addEventListener('click',stopBang);
    function stopBang() {
        window.clearTimeout(fn);//在此处调用定时器fn，终止回调函数
    }
</script>
```