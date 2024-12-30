# 一、http请求体

请求体非常灵活，可以为空，也可以不为空

## 一、不为空

1、键值对的形式：登录proccess on网站，浏览器会向登录网站的服务器发送我们的登录信息，这个时候我们的“账号、密码”就被当作请求体发送到服务器中【账号、密码是被加密的】

```js
1ogin_emai1-779498590%4099.com&1ogin_password=zDAZn2w76CucPzD&type=account_1ogin
```



2、JSON格式：登录掘金账号，和上面一样，只是请求体的信息不再是键值对，而是JSON格式

```js
["ev_type" : "batch" ,"1ist": [{"ev_type" : "pageview" ,"payload": {"pid":"index" ,"source
```

