# 操作元素----修改元素内容

解析：javaScript中的DOM操作可以改变网页内容、结构、样式，我们可以利用DOM操作元素来改变元素里面的内容、属性等，注意以下都是属性：

## 一、改变元素内容

```html
element.innerText
```

解析：从起始位置到终止位置的内容，但它去除html标签，同时空格和换行也会去掉

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>我的第一个JS文件</title>
    <style>
        div{
            color:black;
            background-color:pink;
        }
    </style>
</head>
<body>
<button>显示当前系统时间</button>
<div>某个时间</div>
<script>
    // 获取事件源
    var btn = document.querySelector('button');
    var div = document.querySelector('div');
    // 事件类型【点击按钮的时候，在div上显系统事件】
    btn.onclick = function() {
        div.innerText = getDate();
    }

    function getDate() {
        var nowDate = new Date();
        var year = nowDate.getFullYear();
        var month = nowDate.getMonth();
        var day = nowDate.getDate();
        var arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六'];
        var week = nowDate.getDay();
        return ('今天的日期是：' + year + '年' + month + '月' + day + '日' + arr[week]);
    }
</script>

</body>
</html>
```

```html
element,innerHTML
```

解析：从起始位置到终止位置的全部内容，包括html标签，同时保留空格和换行



## 二、innerText和innerHTML的区别：在读取html标签上

```html
<body>
<div></div>
<script>
   // innerText和innerHTML的区别
   var div = document.querySelector('div');
   div.innerText = ('<strong>今天是：</strong>>2022年12月27日');
   // 我们想要让‘今天是：’字符串加粗显示于是直接在里面加strong是不起作用的
</script>

</body>
```

解析：innerText是不识别html标签的

```html
<body>
<div></div>
<script>
   // innerText和innerHTML的区别
   var div = document.querySelector('div');
   div.innerHTML = ('<strong>今天是：</strong>2022年12月27日');
   // 我们想要让‘今天是：’字符串加粗显示,于是直接在里面加strong也是起作用的
</script>

</body>
```

解析：innerHTML是支持显示html标签的



注意：我们的innerText是由于IE发起的，是不标准的；但是innerHTML是由W3C发起的，是标准的，也是在实际开发中使用得最多的

## 三、innerText和innerHTML的区别：都可以读取内容

```html
<p>
    我是内容
    <span>123</span>
</p>
<script>
    // innerText和innerHTML的区别：在读取内容上
    var p = document.querySelector('p');
    // innerText:不识别HTML标签，而且去除空格和换行
    console.log(p.innerText);
    // innerHTML识别HTML标签，保留空格和换行
    console.log(p.innerHTML);
</script>

</body>
```