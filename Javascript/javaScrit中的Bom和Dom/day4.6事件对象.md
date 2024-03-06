# 事件对象

```html
<!--    这里是css代码-->
    <style>
        div{
            width: 100px;
            height: 100px;
            background-color: #d77282;
            line-height: 100px;
            text-align: center;
            color: white;
        }
    </style>
<body>
<!--    HTML代码-->
<div>123</div>

<!--    JS代码-->
<script>
    //事件对象
    let div = document.querySelector('div');
    div.onclick = function(event) {
        console.log(event);
    }
    //event就是一个事件对象，写到我们监听的函数的小括号里面 当作形参来看
    //事件对象只有有了事件才会存在【如：onclick就是事件】，事件对象是系统创建的，不需要传递参数
    //事件对象是我们事件的一系列相关数据的集合，它跟事件相关。比如鼠标点击就包含了鼠标的相关信息，鼠标坐标；如果是键盘事件里面就包含键盘的相关事件的信息，比如判断用户按下了哪一个键盘
</script>
```

## 一、实际开发技巧

```javascript
div.addEventListener('click',function(event) {
    alert(event);
});
//注：这里的事件对象不一定是event，可以自定义，在实际开发中，我们可以写成evt或者是e都可以
div.addEventListener('click',function(e) {
    console.log(e);
});
```

## 二、但是存在兼容性问题，怎么解决？

在IE6、7、8中，是不识别以下写法的：

```javascript
div.onclick = function(event) {
    console.log(event);
}
```

需要这样书写：

```javaScript
div.onclick = function(event) {
    console.log(window.event);
}
```

如何同时兼容呢？应该这样书写：

```javaScript
div.onclick = function(event) {
    event = event || window.event;
    console.log(event);
}
```

但是现在已经不怎么考虑兼容性问题了

