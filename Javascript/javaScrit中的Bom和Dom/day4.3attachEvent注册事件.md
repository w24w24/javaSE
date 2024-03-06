# attachEvent注册事件【注意：此方法不标准，请勿用于生产环境中】

## 一、为什么要使用attachEvent注册事件？

解析：因为在4.2中我们学习了eventTarget.addEventListener(type,listener[,useCapture])，这个事件注册方式虽然好，但是却有着兼容性问题。在以前，我们是使用attachEvent来进行事件监听

## 二、语法和使用

```html
eventTarget.attachEvent(eventNameWithOn,callback);
```

解析：eventTarget.attachEvent()方法是将指定的监听器注册到eventTarget上(目标对象)上，当该对象触发指定的事件的时候，指定的回调函数就会执行

该方法接收两个参数：

eventNameWithOn：事件类型字符串，比如onclick、onmouseover。注意这里要带上on

callback：事件处理函数，当目标触发事件时，回调函数被调用

```html
<!--    HTML代码-->
<button>传统注册方式</button>
<button>方法监听注册方式</button>
<button>IE9 attachEvent</button>

<!--    JS代码-->
<script>
    var btns = document.querySelectorAll('button');
    //3.IE9 attachEvent 现在已经无法使用
    btns[2].attachEvent('onclick',function() {
        alert('我是老人了');
    });
</script>
```

## 三、有没有一种兼容性方法，让所有的浏览器都支持？

解析：按照以前的方式都是些一个`兼容性封装函数`

#### （一）注册事件兼容性解决方案【兼容性处理原则：首先照顾大多数浏览器，再处理特殊浏览器】

```javascript
//封装一个兼容性函数
function addEventListener(element,eventName,fn) {
    //判断当前浏览器是否支持 addEvenListener 方法
    if(element.addEventListener) {
        element.addEventListener(eventName,fn);//第三个参数默认是false
    }else if(element.attachEvent){
        element.attachEvent('on' + eventName,fn);
    }else {
        //相当于element.onclick = fn
        element['on' + eventName] = fn;
    }
}
```

解析：fn的形式

```javascript
divs[1].addEventListener('click',fn)
    function fn() {
        alert('我是addEventListener的弹窗');
        divs[1].removeEventListener('click',fn);
    }
```