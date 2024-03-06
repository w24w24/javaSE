# 操作元素----修改元素属性

常用的元素的属性操作：

1.innerText、innerHTML：改变元素的内容

2.src、href

3.id、alt、title

## 一、制作一个简单的图片切换效果：

```html
<body>
<button id="ldh">刘德华</button>
<button id="zxy">张学友</button>
<img src="photo/刘德华.jpg" alt="" title="刘德华">
<script>
    // 获取元素
    var ldh = document.getElementById('ldh');
    var zxy = document.getElementById('zxy');
    var img = document.querySelector('img');
    // 注册事件 处理程序
    zxy.onclick = function () {
        img.src = 'photo1/张学友.jpg';
        img.title = '张学友';
    }
    ldh.onclick = function () {
        img.src = 'photo/刘德华.jpg';
        img.title = '刘德华';
    }
</script>

</body>
```

解析：

1.其中的图片切换效果就是将另一张图片的地址放到点击时候的切换即可

2.为了让程序含有严谨性，在切换的时候，鼠标放入的时候，图片的标题也要跟着变化

3.需要不断地完善代码地可读性，不可让读取者或者开发人员感到迷惑