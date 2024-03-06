# H5新增获取元素方式

这种方式只支持i9以上的浏览器，假设在不考虑兼容性或者是在移动端下，可以使用这种方法

1.document.getElemengtsByClassName('类名')：根据类名返回元素对象集合

```html
<body>
<div class="box">盒子1</div>
<div class="box">盒子2</div>
<div id="nav">
    <ul>
        <li>首页</li>
        <li>产品</li>
    </ul>
</div>
<script>
    var Box = document.getElementsByClassName('box'); // 使用类名选择器，不需要加.
    console.log(Box);

</script>

</body>
```

2.document.querySelector('选择器')：根据选择器返回第一个元素对象

```html
<body>
<div class="box">盒子1</div>
<div class="box">盒子2</div>
<div id="nav">
    <ul>
        <li>首页</li>
        <li>产品</li>
    </ul>
</div>
<script>
    var firstBox = document.querySelector('.box'); // 返回执行选择器的第一个对象，必须要加.
    console.log(firstBox);
    var firstNav = document.querySelector('#nav');
    console.log(firstNav);

</script>

</body>
```

3.document.querySelectorAll('选择器')：根据指定选择器返回

```html
<head>
    <meta charset="UTF-8">
    <title>我的第一个JS文件</title>
</head>
<body>
<div class="box">盒子1</div>
<div class="box">盒子2</div>
<div id="nav">
    <ul>
        <li>首页</li>
        <li>产品</li>
    </ul>
</div>
<script>
    var allBox = document.querySelectorAll('.box');
    console.log(allBox);
    var allNav = document.querySelectorAll('#nav'); // 对于id，加#就可以了
    console.log(allNav);

</script>

</body>
```