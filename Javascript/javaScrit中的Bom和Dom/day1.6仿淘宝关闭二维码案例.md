# 仿淘宝关闭二维码案例【即关闭窗口】

## 一、作业：当鼠标点击二维码按钮的时候，关闭整个二维码

解析：

1.利用样式的显示和隐藏完成，隐藏元素：display:none ，显示元素：display:block

2.点击按钮，就直接让这个二维码盒子隐藏起来即可

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>关闭二维码</title>
<!--内嵌样式-->
    <style>
        img {
            width: 200px;
            height: 200px;
            margin: 20px;
            padding:50px;
        }
    </style>
</head>
<body>
<div class="box">
    <img src="photo/下午好.jpg" alt="">
    <i class="close-btn">X</i>
</div>
<script>
    //1.获取事件
    var btn = document.querySelector('.close-btn');
    var box = document.querySelector('.box');
    //2.注册事件 处理程序
    btn.onclick = function() {
        box.style.display = 'none';
    }
</script>
</body>
</html>
```

解析：

想要在关闭内容的同时，也要让关闭按钮消失，就需要让内容和关闭按钮处于同一个div盒子里面