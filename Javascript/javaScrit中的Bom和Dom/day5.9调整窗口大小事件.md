# 调整窗口大小事件

## 一、调整窗口大小事件

```javascript
window.onresize = function() {};
window.addEventListener('resize',function() {});
```

解析：window.onresize是调整窗口大小加载事件，当时触发时候就调用的处理函数

```javascript
window.addEventListener('resize',function(){
    console.log('变化了');
});
```

### 二、注意

1.只要窗口大小发生像素变化，就会触发这个事件

2.我们经常利用这一个事件完成响应式布局。window.innerWidth当前屏幕的宽度

```javascript
window.addEventListener('load',function() {
    var div = window.document.querySelector('div');
    window.addEventListener('resize',function() {
        if(window.innerWidth <= 900) {
            div.style.display = 'none';
        }else{
            div.style.display = 'block';
        }
    });
});
```