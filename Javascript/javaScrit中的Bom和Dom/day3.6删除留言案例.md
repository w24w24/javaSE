# 删除留言案例

解析：在3.4中，，我们学习了如何发布留言，现在我们制作一个删除留言的案例

第一种方式：

```html
<!--    这里是css代码-->
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .msg{
            width: 300px;
            height: 200px;
            margin: 100px auto;
            position: relative;
        }
        .sub{
            position: absolute;
            top: 20%;
            right: 10px;
        }
        .del{
            position: absolute;
            top: 20%;
            right: -30px;
        }
        textarea{
            resize: none;
            outline: none;
            width: 250px;
            height: 100px;
        }
        li{
            background-color: pink;
            color: #e61515e7;
            font-size: 16px;
            margin-bottom: 5px;
            padding-left: 10px;
        }
        li a{
            text-decoration: none;
            float: right;
        }
    </style>
<body>
<!--    HTML代码-->
<div class="msg">
    <textarea name="" id="123" cols="30" rows="10" placeholder="请输入"></textarea>
    <button class="sub">发布</button>
    <button class="del">删除</button>
    <ul>

    </ul>
</div>

<!--    JS代码-->
<script>
    // 1.获取元素
    var textarea = document.querySelector('textarea');
    var btnSub = document.querySelector('.sub');
    var btnDel = document.querySelector('.del');
    var ul = document.querySelector('ul');
    // 2.发布按钮注册事件
    btnSub.onclick = function() {
        if(textarea.value === '') {
            alert('您没有输入任何内容');
        }else {
            // 新建元素
            let li = document.createElement('li');
            li.innerHTML = textarea.value;
            // 添加元素
            ul.appendChild(li);
        }
    }
    // 3.删除按钮注册事件
    btnDel.onclick = function() {
        ul.removeChild(ul.children[0]);
    }

</script>
```

第二种方式：

```html
<!--    这里是css代码-->
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .msg{
            width: 300px;
            height: 200px;
            margin: 100px auto;
            position: relative;
        }
        button{
            position: absolute;
            top: 20%;
            right: 10px;
        }
        textarea{
            resize: none;
            outline: none;
            width: 250px;
            height: 100px;
        }
        li{
            background-color: pink;
            color: #e61515e7;
            font-size: 16px;
            margin-bottom: 5px;
            padding-left: 10px;
        }
        li a{
            text-decoration: none;
            float: right;
        }
    </style>
<body>
<!--    HTML代码-->
<div class="msg">
    <textarea name="" id="123" cols="30" rows="10" placeholder="请输入"></textarea>
    <button class="sub">发布</button>
    <ul>

    </ul>
</div>

<!--    JS代码-->
<script>
    // 1.获取元素
    var textarea = document.querySelector('textarea');
    var btnSub = document.querySelector('button');
    var ul = document.querySelector('ul');
    // 2.发布按钮注册事件
    btnSub.onclick = function() {
        if(textarea.value === '') {
            alert('您没有输入任何内容');
        }else {
            // 新建元素
            let li = document.createElement('li');
            li.innerHTML = textarea.value + '<a href="javascript:;">删除</a>';
            // 添加元素
            ul.appendChild(li);
            // 删除元素
            let del = document.querySelectorAll('a');// 这里是获取所有的a，因为我们会发布很多条言论，每一条言论中间都是有删除属性的
            for (let i = 0; i < del.length; i++) {// 这里使用for循环，遍历所有的a删除属性
                del[i].onclick = function() {// 这里是点击谁的a删除属性，就删除相应的ul中的li
                    ul.removeChild(this.parentNode);// 这里因为点击a删除属性，删除的是ul中的li，所以使用了ul作为父节点。删除的ul下面的li，是当前父节点下面的li，也就是删除a所在的li
                }
            }
        }
    }
</script>
```

解析：第二种方式是通过在留言栏里增加a链接，通过css设计，将删除浮动在右边，在JS中使用事件注册，增加点击事件
