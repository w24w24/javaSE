# 节点操作之父节点：node.parentNode

## 一、节点层级

解析：利用DOM树可以把节点划分作不同的层级关系，最常见的是`父子兄`层级关系

![image-20230131153445476](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230131153445476.png)

1.父级节点：node.parentNode

```html
<!--这里是HTML代码-->
<div class="box">
    <span class="erweima">x</span>
</div>

<!--这里是Javascript代码-->
<script>
    // 1.父节点 parentNode
    var erweima = document.querySelector('.erweima');
    // 一般的写法还需要下面这一串代码：
    var box = document.querySelector('.box');
    console.log(box);
    // 但是使用父节点，就不需要使用上面这一串代码了，直接这样写：
    console.log(erweima.parentNode);
</script>
```

## 注意：使用父节点得到的元素节点，是离自己最近的父级节点（亲爸爸） 如果找不到，就返回为 null，如下，因为离自己最近的是box这一个，所以，找到到是box，而不是test这一个

```html
<!--这里是HTML代码-->
<div class="test">
    <div class="box">
        <span class="erweima">x</span>
    </div>
</div>

<!--这里是Javascript代码-->
<script>
    // 1.父节点 parentNode
    var erweima = document.querySelector('.erweima');
    // 一般的写法还需要下面这一串代码：
    var box = document.querySelector('.box');
    console.log(box);
    // 但是使用父节点，就不需要使用上面这一串代码了，直接这样写：
    console.log(erweima.parentNode);
</script>
```

