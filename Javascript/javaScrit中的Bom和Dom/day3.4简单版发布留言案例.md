# 简单版发布留言案例

## 一、案例

Javascript WebAPI DOM

节点操作之简单版发布留言案例
主要复习了节点操作的创建和添加以及删除节点的知识
实现功能：

1.留言板由下至上发布留言
2.删除留言

有一个输入框架，当在输入框里面输入内容的时候，点击发布的时候，发布到第一列里面，再新建发布的时候，就会生成在第二列里面

核心思路：

1.点击按钮之后，就动态创建一个li，添加到ul里面

2.创建li的同时，需要把文本域里面的值通过li.innerHTML赋值给li

3.如果想要新的留言显示在后面，就使用node.appendChild，如果想要显示就使用node.insertBefore



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
        textare{
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
    <button>发布</button>
    <ul>

    </ul>
</div>
<!--    JS代码-->
<script>
    // 1.获取元素
    var btn = document.querySelector('button');
    var text = document.querySelector('textarea');
    var ul = document.querySelector('ul');
    // 2.注册事件
    btn.onclick = function() {
        if(text.value === ''){
            alert('您没有输入内容');
        }else{
            // 1.创建元素
            var li = document.createElement('li');
            li.innerHTML = text.value + '<a href="javaScript:;">删除</a>'
            // 2.添加元素
            ul.insertBefore(li,ul.children[0]);
            // 3.删除元素
            var del = document.querySelectorAll('a');
            for (let i = 0; i < del.length; i++) {
                del[i].onclick = function() {
                    ul.removeChild(this.parentNode);
                }
            }
        }
    }
</script>
```

## 注意：在点击删除的时候，我们的a链接可能会产生页面跳转，为了阻止页面跳转，需要使用到以下语法：

```html
javascript:;
javascript:void(0);
```



