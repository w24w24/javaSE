# this指向问题

解析：this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁，一般情况下，this的最终指向是那个调用它的对象

## 一、this的几个指向问题

1.全局作用域下、普通函数中this的指向全局对象window【注意：计时器里面this也是指向window的，因为调用计时器的对象是window】

```javascript
console.log(this);//这是在全局作用域中：指向的是window

function fn() {//这是在普通函数中：this指向的是window
    console.log(this);
}
window.fn();//这里的window可以省略

window.setTimeout(function() {//在计时器中：this指向的是window
    console.log(this);
},2000);
```

2.在方法调用中，谁调用this，this就指向谁

```javascript
var o = {//在方法中，谁调用就指向谁，这里指向o
    sayHi: function() {
        console.log(this);
    }
}
o.sayHi();

var btn = window.document.querySelector('button');
    //1.传统注册方式：
    btn.onclick = function() {
        console.log(this);//指向btn按钮
    }
    //2.使用addEVentListener注册
    btn.addEventListener('click',function() {
        console.log(this);//指向btn按钮
    })
```

3.构造函数中，this指向构造函数的实例

```javaScript
//构造函数：
function Fun() {
    console.log(this);
}
var fun = new Fun();
/*
1.构造函数需要使用new一下
2.使用构造函数后，会在内存中新开辟一块空间，这个this就是指向这个空间
3.只是将对象实例化之后赋值给到了fun
 */
```