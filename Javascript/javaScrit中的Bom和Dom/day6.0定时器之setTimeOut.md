# 定时器之setTimeout

解析：在我们的JS页面中，经常有一些事件是和时间打交道的，比如：广告的倒计时、轮播图等等

## 一、window对象提供的定时器的方式

1.setTimeout()【timeout：延时】

2.setInterval()【interval：间隔】

## 二、怎么使用？

#### （1）window.setTimeout(调用函数，[延迟的毫秒数]):

```javascript
window.setTimeout(调用函数，[延迟的毫秒数]);
```

解析：setTimeOut()方法用于设置一个定时器，该定时器在定时器到期后执行调用该函数

1.第一种写法：

```javascript
//定时器
window.setTimeout(function() {
    console.log('时间到了');
},3000);
/* 
1.这个window在调用的时候可以省略；
2.这个延时单位是毫秒，但是可以省略，如果生省略，默认的是0
3.这个函数调用的时候可以直接写函数，也可以写函数名
*/
```

2.第二种写法：

##### 写函数名调用定时器：

```javaScript
//写函数调用定时器：
function callBack() {
    console.log('爆炸了');
}
window.setTimeout(callBack,2000);
```

3.第三种写法：【在实际开发中不提倡】

##### '函数名（）'：

```javascript
//'函数名（）'：
function callBack() {
    console.log('时间到了');
}
window.setTimeout('callBack()',2000);
```

## 注意：页面中有很多计时器，我们怎么区分呢？

解析：我们通过给计时器设置名字，来区别各个计时器，而且这些计时器可以同时执行，如:

```javascript
//给函数设置不同的名字来区分：
function callBack() {
    console.log('时间到了');
}
var timeout1 = window.setTimeout(callBack,3000);
var timeout2 = window.setTimeout(callBack,5000);
```

## 三、setTimeout（）定时器：也称之为`回调函数`

1.setTimeout（）这个调用函数我们也称之为回调函数callBack

2.普通函数是按照代码顺序直接调用，而这个回调函数，需要等待时间，时间到了才去调用这一个函数，因此称之为回调函数

3.回调：就是回头调用的意思，上一件事干完，再回头调用这个函数，以前讲解的element.onclick = function() {}或者是element.addEventListener('click',fn)里面的函数也是回调函数

## 四、案例：5秒后自动关闭的广告

```html
<!--    这里是css代码-->
    <style>
        img{
            width: 100px;
            height: 100px;
        }
    </style>
</head>
<body>
<img src="photo/下午好.jpg" alt=advertisement">
<script>
    var advertisement = window.document.querySelector('img');
    function callBack() {
        advertisement.style.display = 'none';
    }
    window.setTimeout(callBack,5000);

</script>
```