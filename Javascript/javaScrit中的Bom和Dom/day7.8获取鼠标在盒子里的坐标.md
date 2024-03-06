# 获取鼠标在盒子里的坐标

## 一、案例：

在某些时，我们可能需要获取到鼠标在某个区域的坐标，所以需要获取到鼠标在盒子里的坐标

逻辑分析：

1.我们在盒子里面点击，想要得到鼠标距离盒子左右的距离

2.首先得到鼠标在页面中的坐标（e.oageX和e.pageY）

3.其次利用盒子在页面中的距离（box.offsetLeft和box.offsetTop）

4.用鼠标距离页面的左边减去盒子在页面中的距离，就得到了鼠标在盒子内的坐标

5.如果想要移动一下鼠标，就获得最新的坐标，需要使用到鼠标事件，mousemove

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>首页</title>
</head>
<style>
    .test{
        background-color: pink;
        width: 200px;
        height: 200px;
        margin-left: 150px;
        margin-top: 150px;
    }
</style>
<body>
    <div class="test"></div>
<script>
    var box = window.document.querySelector('.test');
    //1.先使用pageX和pageY获取到元素的界面中的距离
    //2.一个是使用到鼠标的点击事件（click）、一个是使鼠标的移动事件（mousemove）
    box.addEventListener('mousemove',fn);
    //box.addEventListener('click',fn);
    function fn(e) {
        var x = e.pageX - box.offsetLeft;
        var y = e.pageY - box.offsetTop;
        this.innerHTML = 'x坐标是' + x + ' y坐标是' + y;
    }

</script>
</body>
</html>
```