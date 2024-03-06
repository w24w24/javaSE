# location常见方法

![image-20230220222003162](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230220222003162.png)

```javaScript
<button>点击</button>
<script>
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',fn);
    function fn() {
        //1.使用assign，浏览器会记录历史，所以可以实现后退的功能
        location.assign('https://www.baidu.com');
        //2.使用replace是直接跳转到页面，浏览器不会记录历史，所以没有后退功能
        location.replace('https://www.baidu.com');
    }
</script>
```

