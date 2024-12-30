# 一、获取请求行和请求头

## 一、提取htpp请求报文

提问：为什么需要http请求报文？

解答：这是因为浏览器会发送一些请求给到我们的服务器，这个时候我们需要知道浏览器发送请求的内容是什么、想要我们返回什么（举例：顾客（浏览器）去餐厅点菜，餐厅厨师（服务器）需要知道顾客点了什么菜，需要加些什么才可以做菜）

| 含义          | 语法                                                         | 重点掌握 |
| ------------- | ------------------------------------------------------------ | -------- |
| 请求方法      | request.method                                               | *        |
| 请求版本      | request.httpVersion                                          |          |
| 请求路径      | request.url                                                  | *        |
| URL路径       | require('url').parse(request.url).pathname                   | *        |
| URL查询字符串 | require('url').parse(request.url, true).query                | *        |
| 请求头        | request.headers                                              | *        |
| 请求体        | request.on('data', function( chunk ) {}) <br/>request.on('end', function(  ) {}) |          |

#### <span style="color:red">备注：“获取请求体是最重要的”，因为在开发中经常需要对请求体部分进行操作</span>

## 二、http方法代码演示

```js
// 引入http模块
const http = require('http');

// 创建服务对象
const server = http.createServer((request, response) => {
  // 获取请求方法
  console.log(request.method);

  // 获取请求路径
  console.log(request.url);

  // 获取请求版本
  console.log(request.httpVersion);
  // 获取请求头
  console.log(request.headers);

  // 设置服务器的响应体
  response.end("Hello welcome to the LOL~")
});

// 设置端口监听
server.listen(9000, () => {
  console.log('服务已经启动~');
});
```



