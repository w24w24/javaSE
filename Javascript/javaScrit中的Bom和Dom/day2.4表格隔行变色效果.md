# 表格隔行变色效果

## 这里需要用到鼠标经过：onmouseover、鼠标离开：onmouseout

```html
<!--    这里是CSS代码-->
    <style>
        .table{
            border: 1px solid silver;
            border-spacing: 15px;
            border-collapse: collapse;
        }
        thead tr{
            height: 30px;
            background-color: #05e5e5;
        }
        tbody tr{
            height: 30px;
        }
        tbody td{
            border-bottom: 1px solid #d7d7d7;
            font-size: 12px;
            color: blue;
            padding: 12px;
            margin: 12px;
        }
        .tableTrChangeColor{
            cursor: pointer;
            background-color: pink;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<table class="table" style="">
    <caption>证券交易报表</caption>
    <thead>
        <tr>
            <th>代码</th>
            <th>名称</th>
            <th>最新公布净值</th>
            <th>累计净值</th>
            <th>前单位净值</th>
            <th>净增长率</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>03526</td>
            <td>农银金穗3个月定期开发债券</td>
            <td>1.075</td>
            <td>1.079</td>
            <td>+0.047%</td>
        </tr>
        <tr>
            <td>03526</td>
            <td>农银金穗3个月定期开发债券</td>
            <td>1.075</td>
            <td>1.079</td>
            <td>+0.047%</td>
        </tr>
        <tr>
            <td>03526</td>
            <td>农银金穗3个月定期开发债券</td>
            <td>1.075</td>
            <td>1.079</td>
            <td>+0.047%</td>
        </tr>
        <tr>
            <td>03526</td>
            <td>农银金穗3个月定期开发债券</td>
            <td>1.075</td>
            <td>1.079</td>
            <td>+0.047%</td>
        </tr>
        <tr>
            <td>03526</td>
            <td>农银金穗3个月定期开发债券</td>
            <td>1.075</td>
            <td>1.079</td>
            <td>+0.047%</td>
        </tr>
        <tr>
            <td>03526</td>
            <td>农银金穗3个月定期开发债券</td>
            <td>1.075</td>
            <td>1.079</td>
            <td>+0.047%</td>
        </tr>
    </tbody>
</table>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var table = document.querySelector('tbody').querySelectorAll('tr');
    // 2.注册事件   处理程序
    for (var i = 0; i < table.length; i++) {
        // 3.鼠标经过事件
        table[i].onmouseover = function() {
            // 测试是否存在 console.log('11');
            // 想要让鼠标经过的改变经过的背景的颜色，尽量在CSS中写，这样便于修改
            this.className = 'tableTrChangeColor';
        }
        // 4.鼠标离开事件
        table[i].onmouseout = function() {
            this.className = '';
        }
    }
</script>
```

解析：当涉及多个项目组需要改变的时候，就会使用到for循环来获取事件，然后使用到单个事件进行设计

## 注意：

1.在获取事件的时候，使用到了 `var table = document.querySelector('tbody').querySelectorAll('tr');`这句话的意思是：获取tbody下面的所有tr