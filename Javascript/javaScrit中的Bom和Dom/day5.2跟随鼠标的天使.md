# 跟随鼠标的天使

解析：我们有时候需要制作页面中与鼠标相关的需求

## 一、案例：制作一个跟随鼠标移动的图片

核心：鼠标事件mousemove，只要鼠标移动，就会获得鼠标在页面文档中的坐标，将这个坐标赋值给图片即可

```html
<!--    这里是css代码-->
    <style>
        img{
            /*为了让图片不占位置，所以使用绝对定位*/
            position:absolute;
            width: 20px;
            height:20px;
        }
    </style>
<body>
<!--    HTML代码-->
<img src="photo/下午好.jpg" alt="">
<!--    JS代码-->
<script>
    let pic = document.querySelector('img');
    document.addEventListener('mousemove',function(e) {
        //mousemove只要鼠标移动1px，就会触发事件
        //console.log(1);
        //核心原理：只要鼠标移动，就会获得鼠标在页面文档中的距离
        let x = e.pageX;//获取页面中的x坐标
        let y = e.pageY;////获取页面中的y坐标
        console.log('x坐标是' + x,'y坐标是' + y);
        //图片接收坐标
        pic.style.left = x - 10 + 'px';//由于我们的坐标是有距离的，所以需要加上px才可以移动
        pic.style.top = y - 10 + 'px';
    });
</script>
```

解析：注意在赋值的时候给上单位px，否则图片不会跟随鼠标移动