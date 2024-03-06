# 记住用户名案例

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
<input type="text" id="username"> <input type="checkbox" name="" id="remember">记住用户名
<script>
    var username = window.document.querySelector('#username');
    var remember = window.document.querySelector('#remember');
    if(localStorage.getItem('username')) {
        username.value = localStorage.getItem('username');
        remember.checked = true;
    }
    //引入一个新概念 change 当选项变化时
    remember.addEventListener('change',function () {
        if(this.checked) {
            localStorage.setItem('username',username.value);
        } else {
            localStorage.removeItem('username');
        }
    })
</script>
</body>
</html>
```

## 注意：这里引入了一个新概念 change