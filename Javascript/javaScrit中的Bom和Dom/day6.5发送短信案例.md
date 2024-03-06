# 发送短信案例

## 一、案例：

案例分析：

1、按钮点击之后，会禁用 disable 为true

2、同时按钮里面的内容会发生变化，注意 button 里面的内容通过 innerHTML修改

3、定义一个变量，在定时器里面不断递减

4、如果变量为0，说明到了事件，我们需要停止定时器，并且复原按钮的初始状态

```html
<!--    这里是css代码-->
    <style>
        button{
            margin-left: 10px;
        }
    </style>
</head>
<body>
手机号码：<input type="text"><button>点击发送</button>
<script>
    var btn = window.document.querySelector('button');
    var time = 60;//定义剩下的秒数
    btn.addEventListener('click',function() {
        btn.display = true;
        var setTimeInterval = setInterval(function() {
            if(time === 0) {
                //清除定时器和复原按钮
                window.clearInterval(setTimeInterval);
                btn.display = false;
                btn.innerHTML = '点击发送';
                time = 60;
            } else {
                btn.innerHTML = '还剩下' + time + '秒';
                time --;
            }
        },1000);
    })
</script>
```