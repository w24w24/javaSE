# 缓动动画添加回调函数

回调函数原理：函数可以作为一个参数，将这个函数作为一个参数传递到另一个函数里面，当那个函数执行完毕之后，再执行传递进去的参数，这个过程就叫做回调

回调函数书写的位置：定时器结束的位置

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
    //1.以下是被封装的缓动动画函数：
    function animate(obj,target,callBack) {
        clearInterval(obj.timer);
        obj.timer = setInterval(function() {
            var step = (target - obj.offsetLeft) / 10;
            step = step > 0 ? Math.ceil(step) : Math.floor(step);
            if(obj.offsetLeft === target) {
                clearInterval(obj.timer);
                if(callBack) {
                    callBack();
                }
            }else {
                obj.style.left = obj.offsetLeft + step + 'px';
            }
        })
    }
    //2.以下是传如实际参数的格式：
    btn500.addEventListener('click',function() {
        animate(div,500,function() {
            div.style.backgroundColor = 'pink';
        });
    });
    btn800. addEventListener('click',function() {
        animate(div,800,function() {
            div.style.backgroundColor = 'red';
        });
    })


</script>
</body>
</html>
```

解析：在缓动动画封装函数中，callBcak就是形参【只是这个形式参数是一个函数】，这个传递过程就是回调参数的的传递