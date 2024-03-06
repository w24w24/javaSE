# 接day1.5---使用className修改样式属性

## 一、为什么会需要使用className修改样式属性呢？

解析：在样式较少	或者	是功能比较简单的情况下使用样式即element.style修改样式属性，但是一旦遇到样式繁杂、功能繁杂，再使用这一种方式就不太适合了

```html
<!--    这里是CSS代码-->
    <style>
        div{
            border: 1px solid silver;
            width: 200px;
            height: 200px;
            line-height: 200px;
            text-align: center;
            background-color: lightcyan;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<div>text</div>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var test = document.querySelector('div');
    // 2.注册事件   处理程序
    test.onclick = function() {
        // 假设在JS中使用element.style改变样式的话，需要如此多的代码
        this.style.background = 'purple';
        this.style.color = '#fff';
        this.style.fontSize = '25px';
        this.style.margin = '100px';
    }
</script>
```

## 二、如何解决这一问题呢？

解析：为了避免使用繁杂的代码在JS中改变样式，我们可以直接把改变样式的代码书写在CSS中，在JS中引用类名className即可

```html
<!--    这里是CSS代码-->
    <style>
        div{
            border: 1px solid silver;
            width: 200px;
            height: 200px;
            line-height: 200px;
            text-align: center;
            background-color: lightcyan;
        }
        .change{
            background-color: purple;
            font-size: 25px;
            margin: 100px;
            color: #fff;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<div>text</div>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var test = document.querySelector('div');
    // 2.注册事件   处理程序
    test.onclick = function() {
        // 假设在JS中使用element.style改变样式的话，需要如此多的代码
        // this.style.background = 'purple';
        // this.style.color = '#fff';
        // this.style.fontSize = '25px';
        // this.style.margin = '100px';

        // 在Js中使用className引用即可改变
        this.className = 'change';
    }
</script>
```

## 三、使用className需要注意的地方？

解析：

1.如果样式较多，可以采用类名方式更改元素样式

2.class是个保留字，因此使用className来操作元素属性

3.clasName会直接更改元素的类名，会覆盖掉原先的类名

## 四、如何解决className会直接更改类名这一问题呢？

解析：在CSS中我们学习了一个叫做多选择器的方法，在这里就可以使用了

```html
<!--    这里是CSS代码-->
    <style>
        div{
            border: 1px solid silver;
            width: 200px;
            height: 200px;
            line-height: 200px;
            text-align: center;
            background-color: lightcyan;
        }
        .change{
            background-color: purple;
            font-size: 25px;
            margin: 100px;
            color: #fff;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<div class="first">text</div>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var test = document.querySelector('div');
    // 2.注册事件   处理程序
    test.onclick = function() {
        // 假设在JS中使用element.style改变样式的话，需要如此多的代码
        // this.style.background = 'purple';
        // this.style.color = '#fff';
        // this.style.fontSize = '25px';
        // this.style.margin = '100px';

        // 在Js中使用className引用即可改变
        // this.className = 'change';

        // 既想要保留与原来的类名，又想要改变样式，就可以使用多选择器操作
        this.className = 'first change';
    }
</script>
```