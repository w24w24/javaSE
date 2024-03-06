# 页面加载事件

## 一、窗口加载事件

问题：为什么要用到窗口加载事件？我们以前学习的内容，为了遵循执行顺序，所以把JS放在了html中的body的后面，但是现在我不想放在后面，我像随便放在页面中的一个位置，需要怎么做呢？这个时候就用到了窗口加载事件了。所谓的窗口加载就是等页面中的所以内容全部执行完毕，再见触发相应的事件，这恰好解决了JS文件位置的问题

```javascript
window.onload = function() {}//或者是下面这种
window.addEventListener('load',function() {});
```

解析：window.onload是窗口（页面）加载事件，当文档内容完全加载完成会触发该事件（包括图像、脚本文件、css文件等），就调用的处理函数

```javascript
//需求：点击按钮弹出一个对话框
//不想要JS文件放在body后面，需要这样解决：
//第一种：window.onload = function() {}
window.onload = function() {
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',function() {
        window.alert('你好，我是使用传统注册函数的弹窗');
    });
}
//第二种：window.addEventListener('load',function() {})
window.addEventListener('load',function() {
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',function() {
        window.alert('你好，我是使用addEventListener的弹窗');
    });
});
```

## 二、注意

1.有了window.onload就可以把JS代码写在页面元素的上方，因为onload是等页面内容全部加载完毕，再去执行处理函数

2.window.onload传统注册事件方式只可以写一次，如果有多个，会以最后一个window.onload为准

3.如果使用addEventListener则没有限制

```javascript
window.onload = function() {
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',function() {
        window.alert('你好，我是使用传统注册函数的弹窗');
    });
};
//会执行下面这一处理函数：
window.onload = function() {
    var btn = window.document.querySelector('button');
    btn.addEventListener('click',function() {
        window.alert('你好，我是使用传统注册函数的第二个弹窗');
    });
}
```

## 三、还有一个与`窗口加载事件`十分像的处理函数

```javascript
document.addEventListener('DOMContentLoad',function() {});
```

解析：DOMContentLoad事件触发，仅当DOM加载完成，不包括css样式表、图片、flash等等【只有IE9+才支持】

#### 和前两个页面加载事件相比，使用这个处理函数的好处是什么？

解析：前两个页面加载事件是`完全加载完文档页面内容`才开始执行，如果文档页面中的图片特别多的话【专门的图片网站】，从用户访问到load触发可能需要很长的时间，交互效果就不可以即时的实现，必然影响用户的体验，那么此时的DOMContentLoad事件就比较合适