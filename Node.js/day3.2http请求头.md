# 一、http请求头

解析：响应头是记录与`浏览器`相关的一些信息

## 1、请求头结构

```js
// 请求头是由多对“键值对”组成的

Host: www.baidu.com // 主机名
Connection:keep-alive // 交互行为
Upgrade-Insecure-Requests:1 // 升级http为https，提升交互的安全性
User-Agent:Mozilla/5.0(windows NT 10.0;Win64;x64)Chrome/108.0.0.0 // 浏览器平台以及版本号
Accept: text/html,application/xhtml+xml,application/xml;q=0.9Sec-Fetch-Site:none // 浏览器能够处理的数据类型
Sec-Fetch-Mode:navigate
Sec-Fetch-User:?1
Sec-Fetch-Dest:document
sec-ch-ua: "Not?A Brand";v="8","chromium";v="108","Google Chrome" ;v="108"
sec-ch-ua-mobile:?0
sec-ch-ua-platform:"Windows"
Accept-Encoding:gzip,deflate,br // 浏览器支持的压缩方式
Accept-Language:zh-CN,zh;q=0.9,en;q=0.8,la;q=0.7 // 浏览器支持的一些语言
Cookie:BIDUPSID=106A974BAB5BA0458E81F18CBEA96E52:PSTM=1669267573:BD UPN=12314753
```

