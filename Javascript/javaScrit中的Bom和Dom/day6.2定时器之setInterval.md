# 定时器之setInterval()

解析：这个回调函数和6.0学习的setTimeout像是一堆孪生兄弟，无论是从语法还是形式上来看，都是非常的相似的

## 一、window提供的定时器的方式

```javascript
window.setInterval(回调函数，[间隔的时间毫秒数]);
```

解析：setInterval()方法重复调用一个函数，每个这个时间，就去调用一次回调函数

```javascript
//setInterval回调函数
window.setInterval(callBack,2000);
function callBack() {
    console.log('继续输出');
}
```

解析：什么是重复调用？就是这个函数一直重复调用自己，并不是执行一次就直接GC

## 二、setTimeout和setInterval的区别是什么？

解析：

1.setTimeout：延时时间到了就去调用这个回调函数，只调用一次，就结束了这个定时器

2.setinterval：每隔这个延时时间，就去调用这个回调函数，会调用很多次，重复调用这个函数