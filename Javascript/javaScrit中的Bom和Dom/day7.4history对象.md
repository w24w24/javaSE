# history对象

解析：JS给我们提供了一个history对象，与浏览器历史记录进行交互，该对象包含用户（在浏览器窗口中）访问过的URL。有如下属性：

![image-20230222123913286](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230222123913286.png)

## 一、案例：

对于history对象，其实就是浏览器的浏览器历史和界面之间的切换。比如：我们打开了两个界面，想要使用返回上一个界面，所以需要使用到forward前进，想要回退到下一级，可以使用到back后退。其中的go是使用数字来进行设计前进和后退的

## 二、例子：

1.首页界面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>首页</title>
</head>
<body>
    <a href="login.html">点击我去往加载页面</a>
    <button>前进</button>
<script>
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',function() {
        //history.forward();
        history.go(1);
    });
</script>
</body>
</html>
```

2.加载页面：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>首页</title>
</head>
<body>
    <a href="login.html">点击我去往加载页面</a>
    <button>前进</button>
<script>
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',function() {
        //history.forward();
        history.go(1);
    });
</script>
</body>
</html>
```