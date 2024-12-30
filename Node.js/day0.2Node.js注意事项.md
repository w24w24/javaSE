# 一、Node.js注意事项？

#### <span style="color:red">注意：在Node.js中是不允许使用BOM、DOM的API的。原因是因为Node.js有自己的API，和浏览器的API是不同的，如下：</span>



1、这是在`浏览器端`编写的javascript

![image-20240813221940683](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240813221940683.png)



2、这是在`Node.js`中编写的Javascript

![image-20240813222018025](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240813222018025.png)



# 二、总结

1、其中的console和定时器是相同的

```js
console.log("I love you!!");
setTimeout(()=> {
  console.log("lov you too!!")
},1000)
```

2、其它的API接口都是不同的

<span style="color:red">3、Node.js中不能使用BOM和DOM的API，但是可以使用cnsole和定时器API</span>

<span style="color:red">4、Node.js的顶级对象为global，也可以使用globalThis访问顶级对象</span>



