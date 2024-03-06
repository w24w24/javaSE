# offsetLeft和offsetTop获取元素偏移【offset：偏移；偏移中心】

## 一、offset概述

解析：offset翻译过来就是偏移量，我使用offset可以动态的得到该元素的位置（偏移）、大小等。使用这一个属性就可以直接在JS中得出元素的相关信息，不需要再去css中使用定位获取了

1. 获得元素距离带有定位父元素的位置
2. 获得元素自身的大小（高度和宽度）
3. 注意：使用offset返回的数值都是不带单位的

offset系列常用属性：

![image-20230222131112887](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230222131112887.png)

## 一、代码示意理解：使用offset获取元素的位置

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>首页</title>
</head>
<style>
    .father{
        background-color: pink;
        height: 200px;
        width: 200px;
        margin: 150px;
        position: relative;
    }
    .son{
        width: 100px;
        height: 100px;
        background-color: purple;
        margin-left: 45px;
    }
</style>
<body>
    <div class="father">
        <div class="son"></div>
    </div>
<script>
    //offset系列
    var father =window.document.querySelector('.father');
    var son = window.document.querySelector('.son');
    //可以使用offset得到元素的偏移位置，返回不带数值的信息
    console.log(father.offsetTop);
    console.log(father.offsetLeft);
    //它以带有定位的父元素为准，如果没有父亲，或者是父亲没有定位，则以body为准
    console.log(son.offsetLeft);
</script>
</body>
</html>
```

## 二、代码示意理解：使用offset获取元素的大小

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>首页</title>
</head>
<style>
    .father{
        background-color: pink;
        height: 200px;
        width: 200px;
        margin: 150px;
        position: relative;
    }
    .son{
        width: 100px;
        height: 100px;
        background-color: purple;
        margin-left: 45px;
    }
    .w{
        background-color: green;
        width: 200px;
        height: 200px;
        margin-left: 250px;
        margin-top: 150px;
    }
</style>
<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <div class="w"></div>
<script>
    //offset系列
    var father = window.document.querySelector('.father');
    var son = window.document.querySelector('.son');
    var w = window.document.querySelector('.w');
    //1.可以使用offset得到元素的偏移位置，返回不带数值的信息
    console.log(father.offsetTop);
    console.log(father.offsetLeft);
    //2.它以带有定位的父元素为准，如果没有父亲，或者是父亲没有定位，则以body为准
    console.log(son.offsetLeft);
    //3.获取元素的大小 有padding、border、width，会获取到这些数据
    //注意：offset是不包括margin的
    console.log(w.offsetWidth);
    console.log(w.offsetHeight);

    //使用offset返回带有定位的父亲
    console.log(son.offsetParent);//返回的是带有定位的父亲，否则返回的是body
    console.log(son.parentNode);//返回的是最近的一级的父亲，亲爸爸，不管元素有没有定位


</script>
</body>
</html>
```