# 显示隐藏文本内容

## 一、显示隐藏文本内容

解析：当鼠标点击文本时，里面默认的文本隐藏，当鼠标离开文本框时，里面的文字显示

## 注意：

## 1.首先需要两个新事件，获得焦点onfocus，失去焦点onblur

## 2.如果获得焦点，判断里面的内容是否为默认文字，如果是，就自动清空表单内容

## 3.如果失去焦点，判断表单内容是否为空，如果为空，则表单内容改为默认文字

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!--    网页编码【注意：必须要放置在第一行】-->
    <meta charset="utf-8"/>
<!--    页面标题-->
    <title>显示隐藏文本框内容</title>
<!--    网页关键字-->
    <meta name="keywords" content="前端学习网，后端开发，JS学习网">
<!--    网页描述-->
    <meta name="description" content="JS学习网是一个富有技术活力的Wbe技术学习网站">
<!--    本页作者-->
    <meta name="author" content="谭磊">
<!--    版权声明-->
    <meta name="copyright" content="本网站所有教程均为自己原创，版权所有，禁止转载，否则必将追究法律责任">
<!--    定义网页自动刷新跳转-->
    <meta http-equiv="refresh" content="60">

    <style>
        input{
            color: #999;
        }
    </style>
</head>
<body>

<!--这里是HTML代码-->
<input type="text" value="手机" name="手机">

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var text = document.querySelector('input');
    // 2.注册事件   获得焦点事件 onfocus
    text.onfocus = function() {
        // console.log('得到了焦点');
        if(this.value === '手机'){
            this.value = '';
        }
        // 获得焦点之后，将文本框里的文字变黑
        this.style.color = '#333';
    }
    text.onblur = function() {
        // console.log('失去了焦点');
        if(this.value === '') {
            this.value = '手机';
        }
        // 失去焦点的时候，将默认文本颜色还原为最初的浅色
        this.style.color = '#999';
    }
</script>

</body>
</html>
```

