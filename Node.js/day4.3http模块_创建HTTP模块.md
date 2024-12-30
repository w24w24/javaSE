# 一、创建http服务器

## 一、示例

```js
// 引入http模块
const http = require('http');

// 创建服务对象
const server = http.createServer((request, response) => {
  // 设置服务器的响应体
  response.end("Hello welcome to the LOL~")
});

// 设置端口监听
server.listen(9000, () => {
  console.log('服务已经启动~');
})
```

## 二、参数解析

1、http：http和fs一样，都是node自带的模块，只需要引入即可使用

2、server：server一个对象，且是服务的意思，createServer是http模块中的一个方法，在createServer中，接受一个回调函数，这个回调函数中有两个参数，分别是request、response。request是将浏览器的数据进行打包处理，response是将服务器的数据进行打包处理

3、response.end：是服务器的响应函数，用来响应浏览器并且中止这个程序的运行

4、server.listen：是服务器的监听函数，用来监听浏览器向服务器的某个端口发送请求

5、9000：端口号

6、server.listen：这个方法接收两个参数，一个是端口号，一个是回调函数，回调函数中可以做一些数据的处理和信息提示