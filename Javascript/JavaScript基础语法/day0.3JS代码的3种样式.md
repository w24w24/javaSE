# JS代码的3种样式

## 1.行内样式：

```javaScript
<!-- 1.行内式的JS代码，直接写到HTML的内部 -->
<input type="button" value="唐伯虎" onclick="alert('秋香姐姐')">
```

## 2.内嵌式代码：

```javaScript
<!-- 2.JS的内嵌式代码   -->
    <script>
        alert('沙漠骆驼');
    </script>
```

## 3.外部式：

这是在js文件里面的代码：

```javaScript
alert('如果我是DJ，你还会爱我吗？')
```

在html中引入JS的代码：

```javaScript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>我的第一个JS文件</title>
    <!-- 3.外部式JS代码 -->
    <script src="my.js"></script>
	//注：在script之间，不允许再写任何代码
</head>
<body>

</body>
</html>
```

## 注：单双引号的使用，在html中，我们推荐使用双引号，但是在JS中，推荐使用单引号



