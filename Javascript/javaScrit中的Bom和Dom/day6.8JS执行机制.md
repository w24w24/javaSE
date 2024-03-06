# JS执行机制

![image-20230220131923610](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230220131923610.png)

```javaScript
console.log(1);
    document.onclick = function() {
        console.log("click");
    };
    setTimeout(function() {
        console.log(3);
    },3000);
    console.log(2);
```

解析：在执行的时候，我们借助一个程序，异步进程处理

![JS 执行机制 - it书童](https://image-1253761983.picgz.myqcloud.com/2020-02-22-022252.jpg)

解析：由于主线程不断地重复获得任务、执行任务、再获任务、再执行，所以这种机制被称之为`事件循环【event loop】`