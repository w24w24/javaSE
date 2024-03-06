# 节点操作之动态生成表格

案例：动态生成表格

需求：根据学生数据动态生成表格，同时还可以删除学生数据。

![在这里插入图片描述](https://img-blog.csdnimg.cn/7e85708663164c2992c495c80d4edb36.png?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBAX1RvdWdoX0dpcmw=,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)

**案例分析：**

（1）因为里面的学生数据都是动态的，我们需要 js 动态生成，这里我们模拟数据，自己定义好数据。数据我们采用数组对象形式存储。

（2）所有的数据都是放到 tbody 里面的行里面。

（3）因为行很多，我们需要循环创建多个行（对应多个人）。

## 一、使用数组对象形式存储学生数据

```javascript
let dataS = [
    {
    name: '魏延',
    subject: 'javascript',
    score: 100
    //最后的删除是不需要的，因为这个删除是表格所独有的
},
    {
        name: 'Rookie',
        subject: 'javascript',
        score: 88
    },
    {
        name: 'The Shy',
        subject: 'javascript',
        score: 95
    },
    {
        name: 'jackLove',
        subject: 'javascript',
        score: 93
    },
];
```

## 二、动态生成表格---创建行

解析：我们知道table表格是先有行，再在行里面存放若干个单元格

1.遍历对象：k得到的是属性名；obj[k]得到的是属性值

```html
for (let k in obj)
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
<!--    网页编码【注意：必须放置在第一行】-->
    <meta charset="utf-8"/>
<!--    页面标题-->
    <title>案例：动态生成表格</title>
    <meta http-equiv="refresh" content="60">

<!--    这里是css代码-->
    <style>
        a{
            text-decoration: none;
        }
        table{
            width: 500px;
            margin: 100px auto;
            border-collapse: collapse;
            text-align: center;
        }
        th,td{
            border: 1px solid black;
        }
        thead tr{
            height: 40px;
            background-color: #cccc;
        }
    </style>
<body>
<!--    HTML代码-->
<table cellspacing="0">
    <thead>
        <tr>
            <th>姓名</th>
            <th>科目</th>
            <th>成绩</th>
            <th>操作</th>
        </tr>
    </thead>
    <tbody>
<!--        因为实际开发中，数据是动态取过来的，所以不写死-->
    </tbody>
</table>

<!--    JS代码-->
<script>
    //1.先去准备好学生的数据
    //问题产生：一个对象只可以存储一个学生的信息，怎么存储多个？
    //解决办法：使用数组，数据中可以有多个数据，一个数据就是一个对象
    var dataS = [
        {
        name: '魏延',
        subject: 'javascript',
        score: 100
        //最后的删除是不需要的，因为这个删除是表格所独有的
    },
        {
            name: 'Rookie',
            subject: 'javascript',
            score: 88
        },
        {
            name: 'The Shy',
            subject: 'javascript',
            score: 95
        },
        {
            name: 'jackLove',
            subject: 'javascript',
            score: 93
        },
        {
            name: 'Ming',
            subject: 'javascript',
            score: 10
        }
    ];
    //2.往tbody里面创建行：有几个人创建几行【通过数组的长度】
    var tbody = document.querySelector('tbody');
    for (var i = 0; i < dataS.length; i++) {//外面的for循环管行
        //创建行:tr
        var tr = document.createElement('tr');
        tbody.appendChild(tr);
        //因为单元格是放在行里面的，所以在行tr里面创建td
        //单元格的数量取决于每个对象里面的属性个数 for循环遍历对象 dataS[i]
        for (var k in dataS[i]) {//里面的for循环管单元格
            //创建单元格
            var td = document.createElement('td');
            //把对象里面的属性值给td
            //console.log(dataS[i][k])
            //遍历对象：for (let k in obj)   k得到的是属性名；obj[k]得到的是属性值
            td.innerHTML = dataS[i][k];//把值给到td单元格里面去
            tr.appendChild(td);
        }
        //3.创建有删除两个字的单元格
        var td = document.createElement('td');
        td.innerHTML = '<a href="javascript:;">删除</a>'
        tr.appendChild(td);
    }
    //4.删除操作 开始【因为我们删除的是行和里面的单元格，所以要等其创建完毕】
    let del = document.querySelectorAll('a');
    for (var i = 0; i < del.length; i++) {
        del[i].onclick = function() {
            tbody.removeChild(this.parentNode.parentNode);
        }
    }

</script>
</body>
</html>
```

## 注意：在创建事件的时候需要使用到：

1.createElement（）：创建事件

2.querySelector（）：获取事件
