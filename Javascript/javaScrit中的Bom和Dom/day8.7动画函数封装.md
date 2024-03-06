# 动画函数封装

## 一、动画的实现原理

核心原理：通过定时器setInterval()不断移动盒子的位置

实现步骤：

1. 获得当前盒子的位置
2. 让盒子在当前位置上+1个移动距离
3. 利用定时器不断重复这个操作
4. 加一个结束条件结束定时器
5. 注意此元素需要添加定位，才可以使用element.style.left

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
</style>
<body>
<div></div>
<script>
    //动画原理：
    /*
    1. 获得当前盒子的位置
    2. 让盒子在当前位置上+1个移动距离
    3. 利用定时器不断重复这个操作
    4. 加一个结束条件结束定时器
    5. 注意此元素需要添加定位，才可以使用element.style.left*/
    var div = window.document.querySelector('div');
    //1.获得当前盒子的位置，并且在当前盒子的位置上+1
    setInterval(fn,30)
    function fn() {
        if(div.offsetLeft <= 400) {
            div.style.left = div.offsetLeft + 5 + 'px';
        }else {
            clearInterval(fn);
        }
    }
</script>
</body>
</html>
```