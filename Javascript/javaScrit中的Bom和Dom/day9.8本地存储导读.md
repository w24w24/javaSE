# 本地存储导读

目标：

1. 可以写出sessionStorage数据的存储以及获取方式
2. 可以写出localStorage数据的存储以及获取
3. 可以说出二者的区别

目录：

1. window.sessionStorage
2. window.loaclStorage

# 一、本地存储

解析：随着互联网的快速发展，基于网页的应用越来越普遍，同时也变得越来越复杂，为了满足各种各样的需求，会经常性的在本地存储大量的数据，HTML5提出了规范和相关的解决方案

## （一）本地存储的特性

1. 数据存储在用户的浏览器中
2. 设置、读取方便、甚至是页面刷新也不丢失数据
3. 容量较大，如sessionStorage可以存储5M，loaclStorage可以存储约20M【注意：这里的5M和20M已经很多了，5M相当于可以存储几百万个字符】
4. 只能存储字符串，可以将对象JSON.stringify()编码后进行存储

## (二)window.sessionStorage

1.生命周期为关闭窗口【即关闭浏览器窗口就失去】

2.在同一个窗口（页面）下数据可以共享

3.以键值对的形式存储使用

![image-20230302153340897](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302153340897.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>轮播图实现</title>
    <script src="jQuery.js"></script>
    <style>

    </style>
</head>
<body>
<form action="" method="post">
    <input type="text" value="">
    <button class="Set">存储数据</button>
    <button class="Get">获取数据</button>
    <button class="remove">删除数据</button>
    <button class="clear">删除数据清空所有数据</button>
</form>
<script>
    var ipt = window.document.querySelector('input');
    var Set = window.document.querySelector('.Set');
    var Get = window.document.querySelector('.Get');
    var remove = window.document.querySelector('.remove');
    var clear = window.document.querySelector('.clear');
    //1.存储数据
    Set.addEventListener('click',function () {
        var val = ipt.value;
        sessionStorage.setItem('uname',val);
        sessionStorage.setItem('pwd',val);
    });
    //2.获取数据
    //问题：在控制台打印输出的时候会一闪而过，不知道是什么原因引起的
    Get.addEventListener('click',function () {
        console.log(sessionStorage.getItem('uname'));
    });
    //3.删除数据
    remove.addEventListener('click',function () {
        sessionStorage.removeItem('uname');
    });
    //4.全部删除
    //注意：在实际的开发工作中，谨慎使用此方法
    clear.addEventListener('click',function () {
        sessionStorage.clear();
    })
</script>
</body>
</html>
```

## （三）window.localStoreage

1.生命周期永久有效，除非手动删除，否则关闭页面也是存在的

2.可以多窗口（页面）共享（同一浏览器可以可以共享）

3.以键值对的形式存储使用

![image-20230302162014715](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302162014715.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>轮播图实现</title>
    <script src="jQuery.js"></script>
    <style>

    </style>
</head>
<body>
<form action="" method="post">
    <input type="text" value="">
    <button class="Set">存储数据</button>
    <button class="Get">获取数据</button>
    <button class="remove">删除数据</button>
    <button class="clear">删除数据清空所有数据</button>
</form>
<script>
    var ipt = window.document.querySelector('input');
    var Set = window.document.querySelector('.Set');
    var Get = window.document.querySelector('.Get');
    var remove = window.document.querySelector('.remove');
    var clear = window.document.querySelector('.clear');
    //1.存储数据
    Set.addEventListener('click',function () {
        var val = ipt.value;
        localStorage.setItem('uname',val);
    });
    //2.获取数据
    Get.addEventListener('click',function () {
        console.log(localStorage.getItem('uname'));
    });
    //3.删除数据
    remove.addEventListener('click',function () {
        localStorage.removeItem('uname');
    });
    //4.全部删除
    clear.addEventListener('click',function () {
        localStorage.clear();
    })
</script>
</body>
</html>
```

解析：以上两种方法的用法都是一致的