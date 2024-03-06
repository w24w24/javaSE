# 事件三要素

常见的鼠标事件：

![image-20221224133240315](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221224133240315.png)

## 一、事件概述

含义：javaScript使我们有能力创建动态界面，而事件是可以被javaScript侦测到的行为

简而言之：触发====响应机制

网页中的内一个元素都可以产生触发javaScript的事件，例如，我们可以在用户点击某一个按钮时产生一个事件，然后去执行某些操作

## 二、事件三要素：事件源、事件类型、事件处理程序

```html
<body>
<button id="btn">唐伯虎</button>
<script>
    // 获取事件源
    var btn = document.getElementById('btn');
    // 事件类型 事件处理程序
    btn.onclick = function() {
        alert('点秋香');
    }
</script>

</body>
```

解析：

1.事件源：事件被触发的对象即： 谁?  【按钮】

2.事件类型：事件被如何触发即：鼠标点击？鼠标经过？键盘按下？【点击】  

3.事件处理程序即：通过一个函数赋值的方式完成【和事件类型连用】

## 三、总结：执行事件的步骤

1.获取事件源

2.注册事件（绑定事件）

3.添加事件处理程序（采取函数赋值的形式）

## 四、作业1：有一个div，在点击div的时候在控制台输出“我被选中了”

```html
<body>
<div id="div">123</div>
<script>
    // 要求：点击div，在控制台输出，我被选中了
    // 1.获取事件源
    var arr = document.getElementById('div');
    // 2.绑定事件 3.在控制台打印我被选中了
    arr.onclick = function() {
        console.log('我被选中了');
    }
</script>

</body>
```

