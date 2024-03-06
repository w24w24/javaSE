# 10秒钟后实现页面的跳转

```javascript
<button>点击</button>
<div></div>
<script>
     var btn = window.document.querySelector('button');
     var div = window.document.querySelector('div');
     btn.addEventListener('click',fn)
     function fn() {
         window.location.href = 'https://www.baidu.com';
     }
     var timer = 10;
     setInterval(function() {
         if(timer === 0) {
             window.location.href = "https://www.baidu.com";
         } else {
             div.innerHTML = "您将在"+ timer + "秒钟之后跳转到百度首页";
             timer --;
         }
     },1000)
```

解析：以上的代码在执行的时候会出现空白，想要解决，将函数执行放到一个函数体里去，先调用一次函数，就不会出现页面空白的情况了，如下：

```javaScript
<button>点击</button>
<div></div>
<script>
     var btn = window.document.querySelector('button');
     var div = window.document.querySelector('div');
     btn.addEventListener('click',fn)
     function fn() {
         window.location.href = 'https://www.baidu.com';
     }
     var timer = 10;
     fn1();//先调用一次函数，避免出现空白界面
     setInterval(fn1,1000);
         function fn1() {
             if(timer === 0) {
                 window.location.href = "https://www.baidu.com";
             } else {
                 div.innerHTML = "您将在"+ timer + "秒钟之后跳转到百度首页";
                 timer --;
             }
         }
</script>
```