# tab栏切换布局分析【重点】



```html
<!--    这里是CSS代码-->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        a {
            color: black;
        }

        li {
            list-style: none;
        }

        .ETab {
            position: relative;
            width: 990px;
        }

        .box {
            width: 100%;
            height: 50px;
            font-size: 14px;
            /* background-color: #ccc; */
            border-bottom: 1px solid red;
            overflow: hidden;
            margin-bottom: 50px;
        }

        .box .current {
            background-color: red;
            color: #fff;
        }

        .box ul li {
            float: left;
            height: 50px;
            text-align: center;
            padding: 0 25px;
            line-height: 50px;
        }

        .boxs {
            position: absolute;
            font-size: 12px;
        }

        .box1 ul li {
            width: 50%;
            padding-left: 42px;
        }

        .box ul a:hover {
            color: red;
        }

        .box1 {
            padding-top: 20px;
            margin-top: 50px;
            margin-bottom: 50px;
        }

        .box2 ul li {
            float: left;
            width: 200px;
            padding-left: 42px;
            line-height: 20px;
        }

        .boxs1 {
            position: absolute;
        }

        .item {
            display: none;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<div class="ETab">
    <div class="box">
        <ul>
            <li class="current" data-index="0">商品介绍</li>
            <li>规格与包装</li>
            <li>售后保障</li>
            <li>商品评价</li>
        </ul>
    </div>
    <div class="tab_con">
        <div class="item boxs" style="display: block;">
            <div class="box1">
                <ul class="li1">
                    <li>品牌: Apple</li>
                </ul>
            </div>
            <div class="box2">
                <ul>
                    <li>商品名称：AppleiPhone 12</li>
                    <li>商品编号：100016034400</li>
                    <li>商品毛重：350.00g</li>
                    <li>CPU型号：其他</li>
                    <li>运行内存：其他</li>
                    <li>机身存储：128GB</li>
                    <li>摄像头数量：后置双摄</li>
                    <li>后摄主摄像素：1200万像素</li>
                    <li>前摄主摄像素：1200万像素</li>
                    <li>屏幕比例：其他</li>
                    <li>分辨率：其他</li>
                    <li>屏幕前摄组合：其他</li>
                    <li>操作系统：iOS(Apple)</li>
                </ul>
            </div>
        </div>
        <div class="item">
            规格与包装
        </div>
        <div class="item">
            售后保障
        </div>
        <div class="item">
            商品评价
        </div>
    </div>
</div>

<!--这里是Javascript代码-->
<script>
    // box下的tab栏切换
    // 1.获取事件
    var box = document.querySelector('.box');
    var lis = box.querySelectorAll('li');
    var items = document.querySelectorAll('.item');
    // 2.注册事件   处理程序
    for (var i = 0; i < lis.length; i++) {
        lis[i].setAttribute('data-index',i); // 利用自定义属性设置索引号，以便于点击获取
        lis[i].onclick = function() {
            // 干掉所有人 其余的了类清理 class这个属性
            for (var i = 0; i < lis.length; i++) {
                lis[i].className = '';
            }
            // 留下自己
            this.className = 'current';

            // 显示下面的模块
            var index = this.getAttribute('data-index'); // 通过获取索引号得到点击的模块
            // console.log(index);
            // 干掉所有人 让其余的div隐藏 留下我自己
            for (let i = 0; i < items.length; i++) {
                items[i].style.display = 'none';
            }
            // 留下自己，让自己显示出来
            items[index].style.display = 'block'; // index指向的是被点击的索引号，点击谁，谁显示
        }
    }
</script>
```

## 练习版本：

```html
<!--    这里是CSS代码-->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        a {
            color: black;
        }

        li {
            list-style: none;
        }

        .ETab {
            position: relative;
            width: 990px;
        }

        .box {
            width: 100%;
            height: 50px;
            font-size: 14px;
            /* background-color: #ccc; */
            border-bottom: 1px solid red;
            overflow: hidden;
            margin-bottom: 50px;
        }

        .box .current {
            background-color: red;
            color: #fff;
        }

        .box ul li {
            float: left;
            height: 50px;
            text-align: center;
            padding: 0 25px;
            line-height: 50px;
        }

        .boxs {
            position: absolute;
            font-size: 12px;
        }

        .box1 ul li {
            width: 50%;
            padding-left: 42px;
        }

        .box ul a:hover {
            color: red;
        }

        .box1 {
            padding-top: 20px;
            margin-top: 50px;
            margin-bottom: 50px;
        }

        .box2 ul li {
            float: left;
            width: 200px;
            padding-left: 42px;
            line-height: 20px;
        }

        .boxs1 {
            position: absolute;
        }

        .item {
            display: none;
        }
    </style>	
</head>
<body>

<!--这里是HTML代码-->
<div class="ETab">
    <div class="box">
        <ul>
            <li class="current" data-index="0">商品介绍</li>
            <li>规格与包装</li>
            <li>售后保障</li>
            <li>商品评价</li>
        </ul>
    </div>
    <div class="tab_con">
        <div class="item boxs" style="display: block;">
            <div class="box1">
                <ul class="li1">
                    <li>品牌: Apple</li>
                </ul>
            </div>
            <div class="box2">
                <ul>
                    <li>商品名称：AppleiPhone 12</li>
                    <li>商品编号：100016034400</li>
                    <li>商品毛重：350.00g</li>
                    <li>CPU型号：其他</li>
                    <li>运行内存：其他</li>
                    <li>机身存储：128GB</li>
                    <li>摄像头数量：后置双摄</li>
                    <li>后摄主摄像素：1200万像素</li>
                    <li>前摄主摄像素：1200万像素</li>
                    <li>屏幕比例：其他</li>
                    <li>分辨率：其他</li>
                    <li>屏幕前摄组合：其他</li>
                    <li>操作系统：iOS(Apple)</li>
                </ul>
            </div>
        </div>
        <div class="item">
            规格与包装
        </div>
        <div class="item">
            售后保障
        </div>
        <div class="item">
            商品评价
        </div>
    </div>
</div>

<!--这里是Javascript代码-->
<script>
    // 1.设置tab栏切换效果
    // 获取元素
    var tabBox= document.querySelector('.box'); // 先获取包裹 tab 栏的 div 盒子
    var lis = tabBox.querySelectorAll('li'); // 再获取div盒子里面的 li
    var items = document.querySelectorAll('.item'); // 获取 item
    // 注册事件 处理程序
    // 由于是多元素注册事件，所以使用for循环来注册
    for (var i = 0; i < lis.length; i++) {
        // 给lis设置索引号，用于控制下item的显示和隐藏
        lis[i].setAttribute('data-index',i);
        lis[i].onclick = function() {
            // 清除其它元素的所有样式
            for (var i = 0; i < lis.length; i++) {
                lis[i].className = ''; // 注意这里是清除所有元素的属性
            }
            // 让被点击的元素属性变化 
            this.className = 'current';

            // 2.设置tab栏切换时候界面的隐藏、显示效果
            var index = this.getAttribute('data-index');
            for (let i = 0; i < items.length; i++) {
                // 隐藏其它所有的item元素
                items[i].style.display = 'none'; // 注意此处的是清除其它所有的元素的属性
            }
            // 显示自己的部分
            items[index].style.display = 'block';
        }
    }
</script>
```

