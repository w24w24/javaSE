# mouseoverr和mouseenter的区别

解析：

mouseover和mouseenter都是鼠标经过事件，在经过元素的时候都会触发相应的事件，但是二者之间是有本质区别的

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>仿淘宝固定侧边栏</title>
    <link rel="stylesheet" href="jingdong.css">
</head>
<style>
    .father{
        position: relative;
        height: 200px;
        width: 200px;
        background-color: pink;
        line-height: 200px;
    }
    .son{
        position: absolute;
        height: 100px;
        width: 100px;
        background-color: green;
        top: 50px;
        left: 50px;
        line-height: 100px;
    }
</style>
<body>
<div class="father">father
    <div class="son">son</div>
</div>
<script>
    var father = window.document.querySelector('.father');
    var son = window.document.querySelector('.son');
    father.addEventListener('mouseenter',function() {
        console.log(11);
    });
</script>
</body>
</html>
```

解析：

1. mouseover：我们只是给父亲添加了事件，当鼠标经过父盒子的时候，会触发，但是当鼠标经过父盒子内部的子盒子的时候，同样也是会触发

2. mouseenter：我们只是给父亲添加了事件，当鼠标经过父盒子的时候，会触发，但是当鼠标经过父盒子内部的子盒子的时候，就不会触发

   

这就是二者之间的区别【简而言之，就是mouseenter不会产生冒泡事件，到那时mouseover会产生冒泡事件】

## 注意：既然有鼠标经过，就有鼠标离开，鼠标离开使用mouseleave，同样的。mouseleave不会产生冒泡事件