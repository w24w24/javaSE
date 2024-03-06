# 元素滚动scroll系列

解析：scroll翻译过来就是滚动的意思，我们使用scroll系列可以动态得到元素的大小、滚动距

![image-20230226125020378](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230226125020378.png)

## 一、scroll的用法

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="jingdong.css">
</head>
<style>
    div{
        width: 200px;
        height: 200px;
        background-color: pink;
        border: 10px solid red;
        padding: 10px;
    }
</style>
<body>
<div>我是内容</div>
<script>
    var div = window.document.querySelector('div');
    //使用scroll获取到元素的高度 scroll是不包含边框的 但是包含padding
    console.log(div.scrollHeight);
</script>
</body>
</html>
```

## 二、scroll和client的区别

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="jingdong.css">
</head>
<style>
    div{
        width: 200px;
        height: 200px;
        background-color: pink;
        border: 10px solid red;
        padding: 10px;
    }
</style>
<body>
<div>我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容</div>
<script>
    var div = window.document.querySelector('div');
    //scroll得到的是内容的实际宽度，但是client得到的是区域的实际宽度，和内容没有关系
    console.log(div.scrollHeight);
    console.log(div.clientHeight);
</script>
</body>
</html>
```

## 三、那么怎么使用scroll呢？

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="jingdong.css">
</head>
<style>
    div{
        width: 200px;
        height: 200px;
        background-color: pink;
        border: 10px solid red;
        padding: 10px;
        overflow: auto;
    }
</style>
<body>
<div>我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容
    我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容我是内容</div>
<script>
    var div = window.document.querySelector('div');
    //scroll常用属性： scrollTop和scrollLeft
    //scrollTop得到的是上卷的内容的宽度，scrollLeft得到的是距做左边的距离
    div.addEventListener('scroll',function() {
        console.log(div.scrollTop);
    });
</script>
</body>
</html>
```

解析：scroll最常使用的就是scrollTop和scrollLeft