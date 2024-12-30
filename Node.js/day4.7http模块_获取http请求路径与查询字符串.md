# 一、提取http请求体中的“请求路径、查询字符串”【这是旧的提取方式】

## 一、代码演示：先看代码，再看参数解析

```js
const http = require('http');
const url = require('url');

const server = http.createServer((request,response) => {
  response.setHeader('content-type', 'text/htm;charset=utf-8');
  response.end('请求成功~');

// console.log(request.url);
// 获取到发起请求的url路径和查询字符串
let res = request.url;
// 导入url模块，使用里面的parse方法解析url路径和查询字符串
let parseURL = url.parse(res);
// console.log(parseURL);

// 获取到http路径
let pathName = parseURL.pathname;
console.log(pathName);

// 获取到查询字符串
let keyword = parseURL.query;
console.log(keyword);

});

server.listen(9000, () => {
  console.log('启动成功~');
});
```

## 二、参数解析：对照上面的代码来解答疑惑

```
第一步：我们想要获取到“浏览器发出的http请求中的【路径】、【查询字符串】”，就必须先拿到这个url地址
所以我们使用了：let res = request.url来获取url地址

第二步：我们使用let res = request.url获取到的是浏览器发出的的http请求和favicon的http请求，但是这种请求我们是无法使用的，需要将其转换为对象形式

第三步：let parseURL = url.parse(res)就是转换为对象的，这个时候就可以使用【对象的形式】去获取到里面的参数了

第四步：
1、let pathName = parseURL.pathname就可以获取到浏览器发出的http请求路径了
2、let keyword = parseURL.query就可以获取到浏览器的发出的查询字符串
```



# 二、提取http请求体中的“请求路径、查询字符串”【这是新的提取方式】

解析：在Node.js的官方API文档中，推荐使用这种新的方式去获取http的请求路径和查询字符串

###### 浏览器请求网址：http://127.0.0.1/search?keyword=h5

#### 1、代码演示：先看代码，再看参数解析

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

```js
const http = require('http');
const url = require('url');

const server = http.createServer((request, response) => {
  // 解决服务器的response是乱码问题
  response.setHeader('Content-Type', 'text/html;charset=utf-8');

  // 新方法获取http的路径和查询字符串
  // 实例化URL对象，然后传递参数request.url、'http://127.0.0.1'
  let getURL = new URL(request.url, 'http://127.0.0.1');
  // 在控制台可以得到一个对象，这个对象里面就包含了url地址的路径和查询字符串
  console.log(getURL);

  // 根据控制台的对象，打印或者是取到自己想要的参数
  console.log(getURL.pathname); // 获取路径
  console.log(getURL.searchParams.get('keyword'));

  response.end("所有数据已展示");
})

server.listen(9000, () => {
  console.log('服务器启动~');
})
```

#### 2、参数解析：对照上面的代码来解答疑惑

```
1、我们使用new URL(request.url, 'http请求地址')来代替传统的url.parse(url)

2、使用new URL(request.url, 'http请求地址')得到的url的对象，我们直接用对象的形式去获取对应的参数即可，如：路径、查询字符串

3、getURL.searchParams.get('keyword')的意思是：我们想要得到keyword，但是因为keyword在searchParms下，并且还是一个对象，所以我们需要使用get方法去获取，并且需要传递参数keyword进去【这种理解并不正确，只是为了后面方便复习，不产生疑惑】
```



