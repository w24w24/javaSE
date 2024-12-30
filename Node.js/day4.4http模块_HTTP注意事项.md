# 一、http注意事项

1、命令行`ctrl + c`停止http服务

2、当http服务启动后，更新代码`必须重启服务才能生效`

3、响应内容中文乱码的解决办法，给响应头添加处理方法：`response.setHeader('content-type', 'text/html;charset=utf-8')`

```js
// 引入http模块
const http = require('http');

// 创建服务对象
const server = http.createServer((request, response) => {
  // 解决中文乱码
  response.setHeader('content-type', 'text/html;charset=utf-8');
  response.end("Hello welcome to the LOL~")
});

// 设置端口监听
server.listen(9000, () => {
  console.log('服务已经启动~');
});
```

4、端口号被占用

```
Error：listen EADDRINUSE：Address alreay in use ：：：9000
```

1）关闭当前正在运行的监听端口的服务（使用较多）

2）修改端口号

5、HTTP协议默认的端口号是80（也就是说，当端口号是80的时候，在访问IP地址的时候，端口号可以不显示）

```
IP地址：192.168.1.0.0:80 和192.168.1.0.0 是一样的
```

6、HTTPS协议的端口号是443

7、HTTP服务开发常用的端口号有3000、8080、8090、9000等

```
如果端口号被系统的某些程序占用，但是仍然想使用这个端口，那么就去将系统的端口给停掉

步骤：
1、在系统中搜索“资源监视器”，在侦听端口中找到系统正在使用的端口，记住正在运行的PID号
2、然后到“任务管理器”的详细信息中，根据记下的PID，寻找到对应的程序，将其给停止，即可让我们自己的程序使用这个端口号了
```

