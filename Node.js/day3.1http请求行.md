# 一、http请求行

## 1、请求行及其结构解析

```js
// 请求行
GET https://www.baidu.com/ HTTP/1.1


GET：请求方法
https：协议名
://：固定写法
www.baidu.com【或者是196.128.10】：主机名/域名
/：路径
https://www.baidu.com：请求的URL
HTTP/1.1：请求的版本号
```

## 2、请求方法

| 方法                                | 作用         |
| ----------------------------------- | ------------ |
| <span style="color:red">GET</span>  | 获取数据     |
| <span style="color:red">POST</span> | 新增数据     |
| PUT/PATCH                           | 更新数据     |
| DELETE                              | 删除数据     |
| HEAD/OPTIONS/CONNECT/TRACE          | 使用相对较少 |

