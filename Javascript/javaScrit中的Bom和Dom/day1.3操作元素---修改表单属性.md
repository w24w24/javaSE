# 操作元素---修改表单属性

利用DOM可以操作如下表单元素的属性：

type、value、checked、selected、disabled等等

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>我的第一个JS文件</title>
    <style>

    </style>
</head>
<body>
<button>按钮</button>
<input type="text" value="输入内容">
<script>
    // 1.获取元素
    var btn = document.querySelector('button');
    var input = document.querySelector('input');
    // 2.注册事件 处理程序
    btn.onclick = function () {
        // input.innerHTML = '点击了'; 这是普通盒子 比如div标签里面的内容才有的
        // 想要修改表单里面的值 文字内容是通过value来修改的
        input.value = '点击了';

        // 如果想要某一个表单被禁用，不能被点击 disable
        // btn.disabled = true; // 想要让这个按钮生效，直接让布尔值为true就可以了
        // this指向的是当前函数的调用者
        this.disabled = true;
    }
</script>

</body>
</html>
```

解析：

1.和普通的html标签不一样，修改表单元素时候，innerText和innerHTML就不起作用了；在修改表单元素里面的文字内容的时候，需要用到的是`input.value = '值'`

2.禁用表单的按钮的时候，需要用到disabled【其中的this是指向当前函数的调用者，在开发中使用非常的频繁】