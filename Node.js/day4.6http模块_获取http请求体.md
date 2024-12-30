# 一、获取http请求体

## 一、获取http“请求体”代码演示

###### 一、html代码：需要浏览器发送一个请求，让服务器进行处理

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <!-- "http://localhost:9000//login" 和 "http://127.0.0.1:9000" 是一样的 -->
  <form action="http://127.0.0.1:9000" method="post">
    <input type="text" name="username" id="username">
    <input type="password" name="password" id="password">
    <input type="submit" value="提交">
  </form>
  
</body>
</html>
```

###### 二、node.js代码：在服务器处理浏览器发出来的请求【自主理解】

```js
const http = require('http');

// 这个服务对象是用来处理浏览器的请求的
const server = http.createServer((request, response) => {
  // 设置一个空字符，用来存储浏览器的请求体
  let body = '';
  // 对浏览器发送过来的数据进行处理
  // data是固定的写法，表示数据
  request.on('data', chunk => {
    // 对浏览器发送过来的数据进行格式化处理，即拼接到body空字符中，再toString()
    body += chunk.toString();
  })

  // 展示数据
  // 当使用 request.on('data', chunk => {...}对于数据处理完毕之后，就对浏览器进行响应
  request.on('end', () => {
    // 我们选择的操作是在集成终端中打印“浏览器发送过来数据的”
    console.log(body);
    // 然后在浏览器端响应“http hello”
    response.end('http hello');
  });

  // 解决中文乱码
  response.setHeader('content-type', 'text/html;charset=utf-8');
});


// 对于浏览器的端口进行监听
// 当有浏览器请求这个端口的时候，就进行响应操作
server.listen(9000, () => {
  console.log('启动成功');
})
```

###### 三、node.js代码：在服务器处理浏览器发出来的请求【官方理解】

```js
const http  =require('http');

// 创建服务器
const server = http.createServer((request,response) => {
  // 设置响应头：为了解决乱码问题
  response.setHeader('content-type', 'text/html;charset=utf-8');

  // 处理浏览器发送过来的请求：整合浏览器的“请求体数据”
   // 1、先新建一个空字符串
  let body = "";
  request.on('data', chunk => {
    // 2、拼接数据
    body += chunk.toString(); // chunk默认是Buffer数据类型，需要转成字符串
  });

  // 3、当数据接收完毕后，触发end事件
  request.on('end', () => {
    // 4、将数据存储到文件中：但是这里我们在集成终端中显示即可
    console.log(body);
    console.log('显示成功');

    // 服务器响应浏览器的请求：在浏览器弹出信息
    response.end("http 请求成功~")
  })

});

// 监听端口
// 如果node.js代码没有错，那么就提示弹出提示
server.listen(9000, () => {
  console.log('服务器启动成功~');
})
```

