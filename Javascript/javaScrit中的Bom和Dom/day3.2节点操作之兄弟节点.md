# 节点操作之兄弟节点：node.nextSibling

解析：上述我们已经学习了节点操作之父节点、子节点；这一节我们学习兄弟节点。

## 一、兄弟节点有哪两种？

1.node.nextSibling返回当前元素的下一个兄弟节点，找不到就返回null，同样的，返回的也是包含所有的节点

```html
<!--下一个兄弟节点-->
node.nextSibling
```

```html
<!--    HTML结构（下拉框、下拉选项）-->
<span>我是测试的兄长</span>
<span class="test">我是测试</span>
<div>我是测试的弟弟</div>

<!--这里是JS代码-->
<script>
    // 1.获取元素
    var test = document.querySelector('.test');
    // node.nextSibling 得到的是下一个兄弟元素的所有节点，包含文本节点和元素节点
    console.log(test.nextSibling);
</script>
```

2.node.previousSibling返回当前元素的上一个兄弟节点，找不到就返回null，同样的，返回的也是包含所有的节点

```html
<!--上一个兄弟节点-->
node.previousSibling
```

```html
<!--    HTML结构（下拉框、下拉选项）-->
<span>我是测试的兄长</span>
<span class="test">我是测试</span>
<div>我是测试的弟弟</div>

<!--这里是JS代码-->
<script>
    // 1.获取元素
    var test = document.querySelector('.test');
    // node.previousSibling 得到的是上一个兄弟元素的所有节点，包含文本节点和元素节点
    console.log(test.previousSibling);
</script>
```

解析：以上这两种方式得到了所有的元素节点，但是得不到元素节点？所以我们应该怎么获取到元素节点呢？

## 二、我们怎样直接的到元素节点呢？

解析：JS为我们提供了两种新的方式，为了解决node.nextSibling得到的是全部节点，这种方式就是：

1.node.nextElementSibling，得到的是下一个兄弟节点的元素节点：

```html
<!-- 以下这种语法可以直接得到元素节点-->
node.nextElementSibling
```

```html
<!--    HTML结构（下拉框、下拉选项）-->
<span>我是测试的兄长</span>
<span class="test">我是测试</span>
<div>我是测试的弟弟</div>

<!--这里是JS代码-->
<script>
    // 1.获取元素
    var test = document.querySelector('.test');
    // node.nextElementSibling 得到的是下一个兄弟节点的元素节点
    console.log(test.nextElementSibling);
</script>
```

2.node.previousElementSibling，得到的是上一个兄弟元素的元素节点：

```html
<!-- 以下这种语法也是可以直接得到元素节点-->
node.previousElementSibling
```

```html
<!--    HTML结构（下拉框、下拉选项）-->
<span>我是测试的兄长</span>
<span class="test">我是测试</span>
<div>我是测试的弟弟</div>

<!--这里是JS代码-->
<script>
    // 1.获取元素
    var test = document.querySelector('.test');
    // node.previousElementSibling 得到的是上一个兄弟节点的元素节点
    console.log(test.previousElementSibling);
</script>
```

## 注意：这两个方式依旧存在兼容性问题，只有IE9以上才支持

## 三、如何让解决兼容性问题呢？

解析：

1.自己封装一个兼容性函数

```javascript
// 自己封装一个兼容性函数
var result = function getNextElementSibling(test) {
    var el = test;
    while(el === el.nextSibling) {
        if(el.nodeType === 1) {
            return el;
        }
    }
    return null;
}
```
