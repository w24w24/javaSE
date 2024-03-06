# 常见的键盘事件

解析：事件除了可以使用鼠标触发，还可以使用键盘触发

1.onkeyup：某个键盘按键被松开时触发

```html
<script>
    //键盘事件：onkeyup
    //1.传统注册方式：
    document.onkeyup = function() {
        console.log('这是传统的弹起方式');
    }
    //2.新注册方式：
    document.addEventListener('keyup',function() {
        console.log('这是新的弹起方式');
    });
</script>
```

2.onkeydown：某个键盘案件被按下时触发

```html
<script>
    //键盘事件：onkeydown
    //1.传统注册方式：
    document.onkeydown = function() {
        console.log('这是传统的按下触发方式');
    }
    //2.新注册方式：
    document.addEventListener('keydown',function() {
        console.log('这是新的按下触发方式');
    });
</script>
```

3.onkeypress：某个键盘被按下时触发【但是它不识别功能键，不如ctrl、shift、alt等等】已被弃用

```html
<script>
    //键盘事件：onkeypress
    //1.传统注册方式：
    document.onkeypress = function() {
        console.log('这是传统的press按下触发方式');
    }
    //2.新注册方式：
    document.addEventListener('keypress',function() {
        console.log('这是新的按下触发方式');
    });
</script>
```

## 一、注意：

1.执行顺序：onkeydown-->onkeypress-->onkeyup

2.使用addEventListener，不需要加on

3.onkeypress不识别功能键

## 二、如何判断用户按下了哪一个键？

键盘事件对象：

1.keyCode：得到的是ASCII值

2.key：得到的是某一个键

3.onkeyup和onkeydown不识别大小写

4.onkeypress识别大小写

```html
<script>
    // 判断用户按下了哪一个键
    // 键盘事件对象中的keyCode可以得到ASCII值
    // 键盘事件code得到的是哪一个键
    document.addEventListener('keyup',function(e) {
        console.log('keyup的值：\n' + e.keyCode);
        //1.我们的keyup和keydown不区分大小写 a和A得到的都是65
        //2.我们的keypress区分大小写 a和A得到的不是同一个ASCII值
    });
    document.addEventListener('keypress',function(e) {
        console.log('keypress的值：\n' + e.keyCode);
        //2.我们的keypress区分大小写 a和A得到的不是同一个ASCII值
    });
</script>
```

#### 注意：在实际开发中，我们经常使用的onkeyup和onkeydown，因为可以识别所有的键

