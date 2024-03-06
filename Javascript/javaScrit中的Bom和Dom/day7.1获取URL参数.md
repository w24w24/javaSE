# 获取URL参数：登录界面显示欢迎字样

## 一、案例：获取URL参数数据

主要练习数据在不同页面中的传递

## 二、案例分析：

1.第一个登录界面，里面有提交表单，action提交到index.html页面

2.第二个页面，可以使用第一页面中的参数，这样实现了一个数据不同页面之间的传递效果

3.第二个页面之间之所以可以使用第一个页面的数据，是因为利用了URL里面的location.search参数

4.在第二个界面中，需要把这个参数提取

具体操作：

1.第一步去掉？利用substr

2.第二步利用=号分割键和值split('=')

## 三、案例实现

1.先写一个登录界面

```html
<form action="index.html">
    用户名：<input type="text" name="uname">
    <input type="submit" value="登录">
</form>
```

2.再写一个首页

```html
<div></div>
<script>
  console.log(location.search);
  //初始状态：?uname=ready
  //1.先去掉问号？，substr（'起始的位置'，截取几个字符）
  var params = location.search.substring(1);
  console.log(params);
  //利用split把字符串分割为数组的形式：[ "uname", "ready" ]
  //2.利用=号把字符串分割为数组 split('=')
  var arr = params.split('=');
  var div = window.document.querySelector('div');
  div.innerHTML = arr[1] + '欢迎您';//利用下标截取需要的字符串
</script>
```



