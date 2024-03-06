# 密码框验证信息

## 案例：密码框格式提示错误信息

如果用户离开密码框，里面输入的个数不是6~16，则错误信息，否则提示输入正确信息

逻辑：

1.首先判断的事件是表单失去焦点 onblur

2.如果输入正确，则提示正确的信息颜色为绿色小图标

3.如果输入的不是6~16，则提示颜色为红色小图标变化

4.因为里面的样式繁多，我们采用classsName修改样式

```html
<!--    这里是CSS代码-->
    <style>
        img{
            width: 15px;
            height: 15px;
        }
        span{
            color: silver;
            font-size: 10px;
        }
        .wrong{
            color: red;
        }
        .right{
            color: #0eecc3;
        }

    </style>
</head>
<body>

<!--这里是HTML代码-->
<div class="re">
    <input type="password" class="ipt">
    <img class="icon" src="photo/上午好.jpg" alt="Stepha.Curry" title="Stepha.Curry">
    <span class="wakeUp">请输入6~16位密码</span>
</div>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var input = document.querySelector('.ipt');
    var icon = document.querySelector('.icon');
    var wakeUp = document.querySelector('.wakeUp');
    // 2.注册事件   处理程序
    input.onblur = function() {
        // 根据表单里面值的长度 ipt.length
        if(this.value.length < 6 || this.value.length > 16) {
            wakeUp.className = 'wakeUp wrong';
            wakeUp.innerHTML = '输入错误，要求输入6~16位的密码';
            icon.src = 'photo/下午好.jpg';
        }
        else {
            wakeUp.className = 'wakeUp right';
            wakeUp.innerHTML = '输入正确';
            icon.src = 'photo/晚上好.jpg';
        }
    }
</script>
```