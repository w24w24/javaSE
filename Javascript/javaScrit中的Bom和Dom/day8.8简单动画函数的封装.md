# 简单动画函数的封装

注意：函数需要传递2个参数，动画对象和移动到的距离

1.动画函数封装语法：

```javaScript
//简单动画函数的封装
    function animate(obj,target) {
        var timer = setInterval(function() {
            if(obj.offsetLeft >= target) {
                //停止动画 实质是移除定时器
                clearInterval(timer);
            }else {
                obj.style.left = obj.offsetLeft + 5 +'px';
            }
        },20)
    }
```

2.例子应用：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>动画原理</title>
</head>
<style>
    div{
        /*注意：使用Js设计动画的时候，必须要有定位*/
        position: absolute;
        left: 0;
        height: 100px;
        width: 100px;
        background-color: pink;
    }
    span{
        position: absolute;
        left: 0;
        display: block;
        color: blue;
        top: 150px;
    }
</style>
<body>
<div></div>
<span>我是测试内容</span>
<script>

    var div = window.document.querySelector('div');
    var test = window.document.querySelector('span');
    //调用动画函数
    animate(div,400);
    animate(test,400);

    //简单动画函数的封装
    function animate(obj,target) {
        var timer = setInterval(function() {
            if(obj.offsetLeft >= target) {
                //停止动画 实质是移除定时器
                clearInterval(timer);
            }else {
                obj.style.left = obj.offsetLeft + 5 +'px';
            }
        },20)
    }
</script>
</body>
</html>
```