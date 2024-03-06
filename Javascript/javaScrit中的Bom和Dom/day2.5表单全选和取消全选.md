# 表单全选和取消全选

## 案例：表单全选和取消全选案例

业务需求：

1.点击上面全选复选框，下面所有的复选框都选中（全选）

2.再次点击全选复选框，下面的的复选框都不选中（取消全选）

3.如果下面复选框全部选中，上面按钮自动全部选中

4.如果下面复选框有一个没有选中，上面按钮就不选中

5.所有复选框一开始默认状态就是不选中

## 逻辑分析：

1.全选和取下全选：让下面的复选框checked属性（选中状态）跟随全选按钮即可

2.下面复选框需要全选中，上面全选才能选中的方法：给下面的所有复选框绑定点击事件，每次点击，都要循环检查下面所有的复选框有没有选中的，如果有一个没有选中的，上面全选就不选中。可以设置一个变量来控制是否全部选中

```html
<!--    这里是CSS代码-->
    <style>
        /*
        让表格的线段显示的方法
        */
        table,td,th{
            border: 1px solid silver;
            width: 250px;
            border-spacing: 15px;
            border-collapse: collapse;
        }
        thead tr{
            background-color: #23e7e0;
        }
        #j_tb td{
            font-size: 20px;
            color: blue;
            padding: 12px;
            margin: 12px;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<div class="wrap">
    <table>
        <thead>
            <tr>
                <th>
                    <input type="checkbox" id="j_cbAll">
                </th>
                <th>商品</th>
                <th>价钱</th>
            </tr>
        </thead>
        <tbody id="j_tb">
            <tr>
                <td>
                    <input type="checkbox">
                </td>
                <td>8000</td>
                <td>iphone</td>
            </tr>
            <tr>
                <td>
                    <input type="checkbox">
                </td>
                <td>8000</td>
                <td>mi</td>
            </tr>
            <tr>
                <td>
                    <input type="checkbox">
                </td>
                <td>8000</td>
                <td>oppo</td>
            </tr>
            <tr>
                <td>
                    <input type="checkbox">
                </td>
                <td>8000</td>
                <td>vivo</td>
            </tr>
        </tbody>
    </table>
</div>

<!--这里是Javascript代码-->
<script>
    // 1.全选和取消全选做法：让下面的所有复选框的checked属性（选中状态）跟随 全选按钮即可
    // 获取元素
    var j_cbAll = document.getElementById('j_cbAll'); // 全选按钮
    var j_tbs = document.getElementById('j_tb').getElementsByTagName('input'); // 下面所有的复选框
    // 注册事件
    j_cbAll.onclick = function() {
        // this.checked 可以得到当前复选框的选中状态
        // 如果是true，就是选中 如果是false就是未选中
        // console.log(this.checked);
        for (var i = 0; i < j_tbs.length; i++) {
            j_tbs[i].checked = this.checked;
        }
    }
    // 2.下面复选框需要全选中，上面全选才能选中的方法：
    // 给下面的所有复选框绑定点击事件，每次点击，都要
    // 循环检查下面所有的复选框有没有选中的，如果有一个
    // 没有选中的，上面全选就不选中。可以设置一个变量来控制是否全部选中
    for (var i = 0; i < j_tbs.length; i++) {
        j_tbs[i].onclick= function() {
            // 每次循环点击，都要去循环检查4个小按钮是否已经全选
            // 使用flag 控制全选按钮是否被选中，
            var flag = true;
            for (var i = 0; i < j_tbs.length; i++) {
                // 如果有一个元素未选中，就执行if语句
                // 如果都选中了，就不执行if语句
                if(!j_tbs[i].checked) {
                    flag = false;
                    break; // 只要有一个未选中，就直接退出for循环 这样可以提高执行效率
                }
            }
            // 当执行了if语句后，flag的布尔值false就被赋给j_cbAll
            // 当不执行if语句，flag的布尔值true被赋值给j_cbAll
            j_cbAll.checked = flag;
        }
    }
</script>
```