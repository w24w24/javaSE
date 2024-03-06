# 缓动画原理

效果原理：缓动动画就是让元素运动速度有所变化，最常见的是让速度慢慢停下来

思路：

1.让盒子每次移动的距离慢慢变小，速度就会慢慢落下来

2.核心算法：（目标值 - 现在的位置）/ 10，作为每次移动的距离步长

3.停止条件是：让当前盒子的位置等于目标位置就停止定时器

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
        top: 52px;
        left: 0;
        height: 100px;
        width: 100px;
        background-color: pink;
    }
</style>
<body>
<div>我是测试内容</div>
<button>点击测试</button>
<script>

    var div = window.document.querySelector('div');
    var btn = window.document.querySelector('button');
    //调用动画函数
    btn.addEventListener('click',function() {
        animate(div,400);
    });

    //简单动画函数的封装
    function animate(obj,target) {
        clearInterval(obj.timer);
       obj.timer = setInterval(function() {
           //步长值要写到定时器里
           var step = (target - obj.offsetLeft) / 10;
            if(obj.offsetLeft >= target) {
                //停止动画 实质是移除定时器
                clearInterval(obj.timer);
            }else {
                obj.style.left = obj.offsetLeft + step +'px';
            }
        },15)
    }
</script>
</body>
</html>
```

解析：

1.匀速动画就是：盒子当前的位置 + 固定的值

2.缓动动画就是：盒子当前的位置 + 变化的值（目标值 - 现在的位置） / 10

3.注意步长需要取整【使用数学公式：Math.ceil()】

