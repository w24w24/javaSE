# 注册事件的两种方式（绑定事件）

## 一、注册事件概述

解析：给元素添加事件；称之为`注册事件`或者是`绑定事件`。

## 二、注册事件的两种方式：传统方式和方法监听注册事件

解析：

#### （一）传统注册方式

利用on开头的事件：如onclick

```html
<!--	直接在html文件中间写-->
<button onclick="alert(Hi~)">点击</button>

<!--	在JS里面书写-->
btn.onclick = function() {}
```

特点：注册事件的`唯一性`。

解析：什么是唯一性？就是一个元素、一个事件只可以设置一个处理函数，最后注册的处理函数会覆盖前面注册的处理函数，如下：第一个会被最后一个注册函数覆盖了

```html
<!--    HTML代码-->
<button>传统注册方式</button>
<button>方法监听注册方式</button>

<!--    JS代码-->
<script>
    var btns = document.querySelectorAll('button');
    //1.传统注册方式
    btns[0].onclick = function() {
        alert('Hi~');
    }
    btns[0].onclick = function() {
        alert('Hello,我是传统注册方式');
    }
</script>
```

#### （二）方法监听注册事件：addEventListener	事件监听方式

W3c标准，推荐方式

addEventListener（）：这是一个方法，特别是在移动端开发中使用得很多【这虽然是一个好方法，但是在IE9之前是不支持此方法的，可以使用attachEvent（）方法代替】

特点：同一个元素、同一个事件可以添加多个监听器【监听器就是监听处理函数】，按注册事件依次执行，不会像以on开头的传统注册方式存在唯一性问题

###### 1.语法：

```html
eventTarget.addEventListener(type,listener[,useCapture])
```

解析：eventTarget.addEventListener（）方法将指定的监听器注册到eventTarget(目标对象上)，当该对象触发指定的事件时，就会执行事件处理函数

该方法接收三个参数：

1. type：事件类型字符串，必须引号，比如click、mouseover，注意不要像传统方式一样带on
2. listener[,useCapture]：事件处理函数，事件发生时，会调用该监听函数
3. useCapture：可选参数，是一个布尔值，默认是false，学完DOM事件流之后，我们再进一步学习

```html
<!--    HTML代码-->
<button>传统注册方式</button>
<button>方法监听注册方式</button>

<!--    JS代码-->
<script>
    var btns = document.querySelectorAll('button');
    //2.事件监听注册方式
    btns[1].addEventListener('click',function() {
        alert('Hello,我是事件监听注册方式');
    })
    btns[1].addEventListener('click',function() {
        alert('我是事件监听注册方式，我并不会被前一个覆盖');
    })
</script>
```