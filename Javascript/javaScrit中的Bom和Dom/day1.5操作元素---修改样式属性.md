# 操作元素---修改样式属性

## 一、样式属性操作

我们可以通过JS修改元素的大小、位置、颜色等样式

```javascript
element.style; // 行内样式操作
element.className; // 类名样式操作
```

## 二、注意：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>样式属性操作---使用JS</title>
<!--内嵌样式-->
    <style>
      div {
          width: 200px;
          height: 200px;
          background-color: pink;
      }
    </style>
</head>
<body>
    <div></div>
    <script>
        // 1.获取元素
        var div = document.querySelector('div');
        // 2.注册事件 处理程序
        var flag = 0;
        div.onclick = function() {
            if(flag === 0) {
                // div.style.background-color = 'blue';
                this.style.backgroundColor = 'blue';
                this.style.width = '250px';
                this.style.height = '250px';
                flag = 1;
            }else {
                // div.style.background-color = 'pink';【这是在CSS中的写法】
                this.style.backgroundColor = 'pink'; // 在JS中间，采用驼峰命名法，中间不使用'-'隔开
                this.style.width = '200px';
                this.style.height = '200px';
                flag = 0;
            }
        }
    </script>
</body>
</html>
```

1.JS里面的样式采取驼峰命名法则，如：fontSize、backgroundColor

2.JS里面修改style样式操作，产生的是行内样式，js权重比较高【也就是说：内嵌样式的权重没有JS的style样式操作权重高】