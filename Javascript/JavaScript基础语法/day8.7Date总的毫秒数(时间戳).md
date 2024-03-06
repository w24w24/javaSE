# Date总的毫秒数（时间戳）

### 序言：什么叫做时间戳？

解析：因为我们的时间是永远不会重复的，就像是邮戳一样，当你写一封信发出去，在被盖上邮戳之后你就不可以再改变信的内容了

## 一、如何获得Date总的毫秒数？

解析：获得Date总的毫秒数？这个不是指当前时间的毫秒数，而是距离1970年1月1号到现在过了多少毫秒

## 二、那么这种获得Date总的毫秒数有几种写法呢？

### 1.通过`valueOf()`来表示：

```javaScript
// 通过valuesOf()获取Date总的毫秒数
var time = new Date();
console.log(time.valueOf());
```

## 2.通过`getTime()`表示：

```javaScript
// 通过getTime()获取Date总的毫秒数
var time = new Date();
console.log(time.getTime());
```

### 简单的写法（因为value()、getTime()太长了，想要简写一下）：

1.第一种写法：

```javaScript
// 简单一点的写法：
var time1 = +new Date(); // 只需要在 new 关键字之前放置一个 + 号就可以了
console.log(time1);
```

2.第二种写法（H5新增属性）：

```javaScript
// H5新增属性，直接输出即可：
console.log(Date.now()); // 注意这里的Date的首字母一定要大写，而且后面不带小括号
```

