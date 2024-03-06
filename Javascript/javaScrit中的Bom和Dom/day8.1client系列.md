# client系列

解析：client翻译过来就是客户端，我们使用client的相关属性来获取元素的可视区的相关信息。通过client可以动态的得到该元素的边框大小、元素大小等

![image-20230224130935769](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230224130935769.png)

## 一、client和offset的区别是什么？

解析：

1.offsetWith得到的是区域的宽度，包括了border边框

2.clientWith得到的也是区域的宽度，是不包含border边框的，但是是包含padding的

