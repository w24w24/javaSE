# 动画函数的使用

1.先建立一个JS文件

```javaScript
function animate(obj, target, callback) {
    // console.log(callback);  callback = function() {}  调用的时候 callback()

    // 先清除以前的定时器，只保留当前的一个定时器执行
    clearInterval(obj.timer);
    obj.timer = setInterval(function() {
        // 步长值写到定时器的里面
        // 把我们步长值改为整数 不要出现小数的问题
        // var step = Math.ceil((target - obj.offsetLeft) / 10);
        var step = (target - obj.offsetLeft) / 10;
        step = step > 0 ? Math.ceil(step) : Math.floor(step);
        if (obj.offsetLeft === target) {
            // 停止动画 本质是停止定时器
            clearInterval(obj.timer);
            // 回调函数写到定时器结束里面
            // if (callback) {
            //     // 调用函数
            //     callback();
            // }
            callback && callback();
        }
        // 把每次加1 这个步长值改为一个慢慢变小的值  步长公式：(目标值 - 现在的位置) / 10
        obj.style.left = obj.offsetLeft + step + 'px';

    }, 15);
}
```

2.再建一个css文件：

```css
.sliderBar {
    position: fixed;
    right: 0;
    bottom: 100px;
    width: 40px;
    height: 40px;
    text-align: center;
    line-height: 40px;
    cursor: pointer;
    color: #fff;
}
.con {
    position: absolute;
    left: 0;
    top: 0;
    width: 200px;
    height: 40px;
    background-color: purple;
    z-index: -1;
}
```

3.在html中书写代码:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>动画原理</title>
    <link rel="stylesheet" href="jingdong.css">
    <script src="./photo/animate.js"></script>
</head>
<body>
<div class="sliderBar">
    <span>←</span>
    <div class="con">问题反馈</div>
</div>
<script>
    // 1. 获取元素
    var sliderBar = document.querySelector('.sliderBar'); //获取父级元素
    var con = document.querySelector('.con'); //获取问题反馈元素
    // 当我们鼠标经过 sliderBar 就会让 con这个盒子滑动到左侧
    // 当我们鼠标离开 sliderBar 就会让 con这个盒子滑动到右侧
    sliderBar.addEventListener('mouseenter', function() { //设置鼠标经过事件
        // animate(obj, target, callback);
        //调用动画函数，并执行回调函数
        animate(con, -160, function() {
            // 当我们动画执行完毕，就把 ← 改为 →
            sliderBar.children[0].innerHTML = '→';
        });

    })
    //设置鼠标离开事件
    sliderBar.addEventListener('mouseleave', function() {
        // animate(obj, target, callback);
        animate(con, 0, function() {
            sliderBar.children[0].innerHTML = '←';
        });
    })
</script>
</body>
</html>
```