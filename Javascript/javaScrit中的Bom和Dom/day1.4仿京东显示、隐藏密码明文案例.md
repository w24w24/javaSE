# 仿京东显示、隐藏密码明文案例

作业要求：

1.设计一个登录界面，当用户输入密码的时候，点击眼睛，可以切换为可见的，再点击一下眼睛，就可以切换为隐藏的

核心思路：

1.点击眼睛按钮，把密码框类型改为文本框就可以看见里面的密码了

2.一个按钮具有两个状态，点击一次，切换为文本框，继续点击切换为密码框

3.算法：利用一个flag变量，来判断flag的值，如果是1就切换为文本框，flag设置为0，如果是0就切换为密码框，flag设置为1

## 一、下面是代码示意图：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>京东明文密码隐藏案例</title>
    <style>
        img {
            width: 50px;
            height: 50px;
        }
    </style>
</head>
<body>
<div class="box">
    <label for="">
        <img src="photo/上午好.jpg" alt="curry" id="eye">
    </label>
    <input type="password" name="" id="pwd">
</div>

<script>
    // 1.获取元素
    var eye = document.getElementById('eye');
    var pwd = document.getElementById('pwd');
    // 2.注册事件 处理程序
    var flag = 0; // 声明一个变量，作为算法
    eye.onclick = function() {
        // 点击与一次之后，我们的flag要变化，这是为了再次点击作铺垫
        if(flag === 0) {
            pwd.type = 'text';
            eye.src = 'photo/下午好.jpg'
            flag = 1;
        }else {
            pwd.type = 'password';
            flag = 0;
            eye.src = "photo/上午好.jpg";
        }
    }
</script>
</body>
</html>
```