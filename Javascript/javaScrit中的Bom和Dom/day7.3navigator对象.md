# navigator对象

解析：在日常使用中，我们可能会使用不同的中断打开不同的网站。那么这些网站是如何判断我们使用的是移动端还是pc端的呢？

## 一、这就涉及到了navigator对象

解析：什么是navigator对象？

navigator包含有关浏览器的信息，具有很多属性，我们最常用的是userAgent，该属性可以返回由客户发送的服务器的user-agent头部的值

下面的前端代码可以判断用户使用了哪一个终端打开页面，实现跳转

![image-20230220224315997](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230220224315997.png)