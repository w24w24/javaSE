# 节点操作之创建和添加节点

## 一、创建节点

解析：意思是，当一篇文章开始发布的时候，评论区是空白的，我们可以发布评论。当第一条评论发布的时候，这个时候评论就会填充到评论区。这个评论发布和评论填充的具体过程就是创建节点，JS为我们提供了以下语法：

```javascript
document.creatElement('tagName')
```

document.creatElement()方法是创建tagName指定的HTML元素，因为这些元素不存在，是根据我们的需求动态生成的，所以我们也称之为动态创建节点

```html
<!--    HTML代码-->
<ul></ul>

<!--    JS代码-->
<script>
    // 1.创建元素节点
    var li = document.createElement('li');
</script>
```

解析：为什么不会在ul内部显示呢？

###  注意：原因：只是创建节点是不够的，你没有添加到相应的区域，所以是不会显示的



## 二、添加节点

解析：添加节点是为了解决创建的节点没有被显示在相应的位置

node.appendChild(child)方法将一个节点添加到指定的父节点的子节点列表末尾，类似于css里面的after伪类，意思是：node是父元素，append是追加，chlid意思是孩子，就是为父元素的子元素的末尾再追加一个子元素

```html
<!--    HTML代码-->
<ul></ul>

<!--    JS代码-->
<script>
    // 1.创建元素节点
    var li = document.createElement('li');
    // 2.添加节点   node.appendChild(child)
    // 先获取到 node:也就是父节点 child:也就是子节点 类似于追加元素，相当于数组中的push
    var ul = document.querySelector('ul');
    // 然后使用语法添加节点
    ul.appendChild(li);
</script>
```

## 三、假如我不想在节点的子元素的末尾添加，想要在节点的子元素前面添加，需要怎么做呢？

node.insertBefore(child)方法将一个节点添加到指定的父节点的子节点列表之前，类似于css里面的before伪类，意思是：node是父元素，inset是插入，before意思是之前，意思是在父节点的子节点之前再插入一个子节点 

解析：JS也是为我们提供了这种语法，语法是： 

```html
node.insertBefore(child,指定元素);
```

```html
<!--    HTML代码-->
<ul>
    <li>我是节点</li>
</ul>

<!--    JS代码-->
<script>
    // 1.创建元素节点
    var li = document.createElement('li');
    // 2.添加节点   node.appendChild(child)
    var ul = document.querySelector('ul'); // 先获取到父节点
    ul.appendChild(li); // 在父节点的子节点末尾追加一个子节点
    // 2.创建一个元素节点
    var lili = document.createElement('li');
    // 添加节点
    ul.insertBefore(lili,ul.children[0]);
</script>
```

