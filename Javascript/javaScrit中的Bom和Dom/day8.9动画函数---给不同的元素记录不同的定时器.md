# 动画函数---给不同的元素记录不同的定时器

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
    span{
        position: absolute;
        left: 0;
        display: block;
        color: blue;
        top: 200px;
    }
</style>
<body>
<div></div>
<span>我是测试内容</span>
<button>点击测试</button>
<script>

    var div = window.document.querySelector('div');
    var test = window.document.querySelector('span');
    var btn = window.document.querySelector('button');
    //调用动画函数
    animate(div,400);
    btn.addEventListener('click',function() {
        animate(test,400);
    });

    //简单动画函数的封装
    function animate(obj,target) {
        //当我们不断的点击按钮，这个元素的速度会越来越快，因为开启了太多的定时器
        //解决方案 让我们的元素只有一个定时器在执行
        //先清除以前的定时器，只保留当前的一个
        clearInterval(obj.timer);
       obj.timer = setInterval(function() {
            if(obj.offsetLeft >= target) {
                //停止动画 实质是移除定时器
                clearInterval(obj.timer);
            }else {
                obj.style.left = obj.offsetLeft + 5 +'px';
            }
        },20)
    }
</script>
</body>
</html>
```

## 注意：

为了提高运行效率和减少内存的占用，我们将原先的var timer改为obj.timer，原理是：利用JS是一门动态语言，可以很方便的给当前对象添加属性

```javaScript
//1.可以直接得到对象，并且通过属性进行赋值操作
var obj = {};
obj.name = 'andy';

//2.这里传递进来的和1是一致的，仍然可以通过属性进行赋值操作
function animate(obj,target) {
        clearInterval(obj.timer);
       obj.timer = setInterval(function() {
            if(obj.offsetLeft >= target) {
                //停止动画 实质是移除定时器
                clearInterval(obj.timer);
            }else {
                obj.style.left = obj.offsetLeft + 5 +'px';
            }
        },20)
```

解析：使用上述这种方式，给不同的元素指定了不同的定时器，既避免了在内存中开辟新的空间，又很好的解释了语法格式
