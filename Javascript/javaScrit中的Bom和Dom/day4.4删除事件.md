# 删除事件（解绑事件）

## 一、删除事件的方式

#### （1）传统注册方式解绑事件：eventTarget.onclick = null

```html
<!--    HTML代码-->
<div>1</div>
<div>2</div>
<div>3</div>

<!--    JS代码-->
<script>
    var divs = document.querySelectorAll('div');
    //1.使用传统方式进行解绑事件
    divs[0].onclick = function() {
        alert('我是传统的点击弹窗');
        //弹出一次就使用传统的方式解绑，不让其一直弹窗
        divs[0].onclick = null;
    }
</script>
```

#### （2）方法监听注册方式解绑事件：eventTarget.removeEventListener(type,listener[,]useCapture)；

```html
<!--    HTML代码-->
<div>1</div>
<div>2</div>
<div>3</div>

<!--    JS代码-->
<script>
    var divs = document.querySelectorAll('div');
    //2.使用addEventListener进行解绑事件
    //由于解绑的事件需要一个函数名字，所以要将函数写在外部
    divs[1].addEventListener('click',fn)//里面的fn 调用不需要加小括号
    function fn() {
        alert('我是addEventListener的点击弹窗');
        divs[1].removeEventListener('click',fn);//首先要移除点击事件，点击事件是fn
    }
</script>
```

解析：为了可以方便解绑事件，不可以像下面这样书写：

```javaScript
//2.使用addEventListener进行解绑事件
divs[1].addEventListener('click',function() {
    alert('我是addEventListener的弹窗');
});
divs[1].removeEventListener('click',这里找不到要删除谁);
```

解决：

```javascript
//2.使用addEventListener进行解绑事件
//函数写在外部，为了方便调用
divs[1].addEventListener('click',fn)
function fn() {
    alert('我是addEventListener的弹窗');
    divs[1].removeEventListener('click',fn);
}
```

#### （3）attachEvent方式注册解绑事件：eventTarget.detachEvent(eventNameWithOn,callback)；

```html
<!--    HTML代码-->
<div>1</div>
<div>2</div>
<div>3</div>

<!--    JS代码-->
<script>
    var divs = document.querySelectorAll('div');
    //3.使用detach.Event(eventNameWithOn,callback)
    divs[2].attachEvent('click',fn1);
    function fn1() {
        alert('我是attachEvent事件的弹窗');
        divs[2].detachEvent('click',fn1);
    }
</script>
```

解析：使用attachEvent依旧存在兼容性问题，于是我们再封装一个兼容性函数

```javascript
//再封装一个兼容性函数
function removeEventListener(element,eventName,fn){
    //判断当前浏览器是否支持 removeEventListener 方法
    if(element.removeEventListener) {
        element.removeEventListener(eventName,fn)//第三个参数 默认是false
    }else if(element.detachEvent) {
        element.detachEvent('on' + eventName,fn);
    }else {
        element['on' + eventName] = null;
    }
}
```

