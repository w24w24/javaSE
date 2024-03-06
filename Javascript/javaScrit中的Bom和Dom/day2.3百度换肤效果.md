# 百度换肤效果

```html
<!--    这里是CSS代码-->
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        body{
            background: url(photo/背景图片.png) no-repeat top;
        }
        li{
            list-style: none;
        }
        .baidu{
            overflow: hidden;
            margin: 100px auto;
            background-color: #fff;
            width: 310px;
            padding-top: 10px;
        }
        .baidu li{
            float: left;
            margin: 0 1px;
            cursor: pointer;
        }
        .baidu img{
            width: 100px;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<ul class="baidu">
    <li><img src="photo/上午好.jpg" alt=""></li>
    <li><img src="photo/下午好.jpg" alt=""></li>
    <li><img src="photo/晚上好.jpg" alt=""></li>
</ul>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var imgs = document.querySelector('.baidu').querySelectorAll('img');
    // 2.for循环注册事件
    for (var i = 0; i < imgs.length; i++) {
        imgs[i].onclick = function() {
            // this.src就是我们点击图片的路径
            // console.log(this.src)
            // 把这个路径 thi.src 给body就可以了
            document.body.style.backgroundImage = 'url(' + this.src + ')';
        }
    }
</script>
```

