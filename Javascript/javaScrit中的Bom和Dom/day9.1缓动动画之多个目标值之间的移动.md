# 缓动动画之多个目标值之间的移动

解析：在实际的开发中，我们会设置和设计多个缓动动画，这个时候，最初的单个程序设计就不满足需求了，这个时候需要这样改进

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
<button class="btn500">点击到500</button>
<button class="btn800">点击到800</button>
<script>

    var div = window.document.querySelector('div');
    var btn500 = window.document.querySelector('.btn500');
    var btn800 = window.document.querySelector('.btn800');
    //调用动画函数
    btn500.addEventListener('click',function() {
        animate(div,500);
    });
    btn800. addEventListener('click',function() {
        animate(div,800);
    })

    //简单动画函数的封装
    function animate(obj,target) {
        clearInterval(obj.timer);
       obj.timer = setInterval(function() {
           //步长值要写到定时器里
           //var step = Math.ceil((target - obj.offsetLeft) / 10);
           var step = (target - obj.offsetLeft) / 10;
           step = step > 0 ? Math.ceil(step) : Math.floor(step);
            if(obj.offsetLeft === target) {
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

解析：以下代码代表的意思是：当一个元素移动的方向和距离是正的【即大于0】，那么我们就需要大的值；如果一个元素移动的方向和距离是负的【即小于0】，那么我们需要取小的值

```javascript
var step = (target - obj.offsetLeft) / 10;
           step = step > 0 ? Math.ceil(step) : Math.floor(step);
```

## 总结：

1. 如果是正值，则步长往大了取整
2. 如果是负值，则步长往小了取整