# 禁止选中文字和禁止右键菜单

## 一、在4.0中，我们学习了鼠标事件，接下来学习新的鼠标事件

1.禁止鼠标右键菜单：contextmenu【context：上下文】主要控制合适何时显示上下文菜单，主要用于程序员取消默认的上下文菜单 

```javascript
<!--    HTML代码-->
<span>我是一段不愿意被分享的文字</span>
<!--    JS代码-->
<script>
    //禁止数鼠标右键菜单
    document.addEventListener('contextmenu',function(e) {
        e.preventDefault();
    });
</script>
```

解析：但是使用ctrl+c还是可以复制，该怎么解决呢？

2.禁止鼠标选中（selectstart：开始选中）

```javascript
<!--    HTML代码-->
<span>我是无法使用鼠标选择的文字</span>
<!--    JS代码-->
<script>
    //禁止数鼠标右键菜单
    document.addEventListener('selectstart',function(e) {
        e.preventDefault();
    });
</script>
```