# 获取body和HTML元素

html标签和body标签，在我们的前端文档中都只有一个，所以我们的JS也为获取它提供了专门的方法，以下就是获取两种标签的方法：

## 一、获取body表签

```javaScript
// 获取body标签
var arr = document.body;
console.log(arr);
```

解析：直接使用document.body即可获得页面中的body元素

## 二、获取html元素

```javaScript
// 获取html元素
var arr = document.documentElement;
console.log(arr);
```

解析：再获取html标签的时候，和获取body标签时有些不一样，获取html标签是使用document.documentElement来获取html标签的