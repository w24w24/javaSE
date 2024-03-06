# 节点操作之子节点：parentNode.childNodes【标准】

解析：parentNode.childNodes 返回包含指定节点的子节点的集合，该集合为即时更新的集合。parentNode.childNodes 得到的是所有的子节点，包括元素节点 、文本节点等等。如果只想要里面的元素节点，则需要专门处理，所以我们不提倡使用parentNode.childNodes

```html
<!--这里是HTML代码-->
<ul>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ul>

<ol>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ol>

<!--这里是Javascript代码-->
<script>
    // DOM提供的方法（API）获取
    var ul = document.querySelector('ul');
    var lis = ul.querySelectorAll('li');
    // 1.子节点: parentNode.childNodes 得到的是所有的子节点 包含 元素节点、文本节点等等
    console.log(ul.childNodes); // 得到的总共有9个，但是在上面的ul中只有4个，为什么？
    // 原因：parentNode.childNodes 得到的是所有的子节点，包括元素节点、文本节点等等
    // 如果只想要里面的元素节点，则需要专门处理，所以我们不提倡使用childNodes
    console.log(ul.childNodes[0].nodeType); // 文本节点为3
    console.log(ul.childNodes[1].nodeType); // 元素节点为1
</script>
```

## 一、如何解决上述代码中使用 parentNode.childNodes 方法获取的节点中同时包含文本节点和元素节点？

解析：一般来说，我们获取节点，只是获取元素节点进行操作，并不想要包含文本节点，我们可以通过这种方式进行解决：

由于元素节点nodeType的值是1，所以可以利用这一个特性进行筛选

```html
<!--这里是HTML代码-->
<ul>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ul>

<ol>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ol>

<!--这里是Javascript代码-->
<script>
    // DOM提供的方法（API）获取
    var ul = document.querySelector('ul');
    var lis = ul.querySelectorAll('li');
    // 1.子节点: parentNode.childNodes 得到的是所有的子节点 包含 元素节点、文本节点等等
    console.log(ul.childNodes); // 得到的总共有9个，但是在上面的ul中只有4个，为什么？
    // 原因：parentNode.childNodes 得到的是所有的子节点，包括元素节点、文本节点等等
    // 如果只想要里面的元素节点，则需要专门处理，所以我们不提倡使用childNodes
    console.log(ul.childNodes[0].nodeType); // 文本节点为3
    console.log(ul.childNodes[1].nodeType); // 元素节点为1

    // 经过处理获取元素节点：
    // 利用元素节点的 nodeType 是1的属性来筛选元素节点
    var gainElementNodes = document.querySelector('ul');
    for (let i = 0; i < gainElementNodes.childNodes.length; i++) {
        if(gainElementNodes.childNodes[i].nodeType === 1) {
            console.log(ul.childNodes[i]);
        }
    }
</script>

```

# 节点操作之子节点：parentNode.children【非标准】

解析：parentNode.children 返回包含指定节点的子节点的集合，该集合为即时更新的集合。parentNode.children 得到的只是元素节点，不包括文本节点等等。想要得到元素节点，不需要专门处理，所以我们提倡使用parentNode.children

```html
<!--这里是HTML代码-->
<ul>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ul>

<ol>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ol>

<!--这里是Javascript代码-->
<script>
    // DOM提供的方法（API）获取
    var ul = document.querySelector('ul');
    var lis = ul.querySelectorAll('li');
    // 1.子节点: parentNode.children 获取所有的子节点 也是实际开发常用的
    console.log(ul.children);
</script>
```

# 节点操作之第一个子节点和最后一个子节点

解析：上述我们已经学习了怎样获取节点中的元素节点，现在我们学习一下如何获取元素节点中的第一个子节点和最后一个子节点

1.parentNode.firstChild：firstChild返回第一个子节点，找不到返回null，同样是包含所有的节点

2.parentNode.lastChild：lastChild返回最后一个子节点，找不到返回null，同样是包含所有的节点

```html
<!--这里是HTML代码-->
<ul>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ul>

<ol>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ol>

<!--这里是Javascript代码-->
<script>
    // DOM提供的方法（API）获取
    var ul = document.querySelector('ul');
    // 1.子节点: parentNode.firstChild 获取第一个子节点，包含所有的节点
    console.log(ul.firstChild);
    console.log(ul.lastChild);

</script>
```

## 一、如何解决parentNode.firstChild和parentNode.lastChild获取的是文本节点而不是元素节点？

解析：JS为我们提供了新的获取方式：

1.parentNode.firstElementChild：获取子节点的第一个元素节点

2.parentNode.lastElementChild：获取子节点的最后一个元素节点

```html
<!--这里是HTML代码-->
<ul>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ul>

<ol>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ol>

<!--这里是Javascript代码-->
<script>
    // DOM提供的方法（API）获取
    var ul = document.querySelector('ul');
    // 1.子节点: parentNode.firstChild 获取第一个子节点，包含所有的节点
    console.log(ul.firstElementChild);
    console.log(ul.lastElementChild);

</script>
```

## 注意：这两个获取方式可能存在兼容性问题，只有IE9以上才支持

## 二、如何解决兼容性问题，而且又可以返回想要的节点呢？



解析：我们可以使用上述所学的parentNode.children，这个方法返回的是节点中的所有的元素节点，并且是以伪数组的形式展现的，所以我们可以利用这一个特性进行获取，`这也是实际开发最常用的方法`

```html
<!--这里是HTML代码-->
<ul>
    <li>我是第一个</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是最后一个</li>
</ul>

<ol>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
    <li>我是li</li>
</ol>

<!--这里是Javascript代码-->
<script>
    // DOM提供的方法（API）获取
    var ul = document.querySelector('ul');
    // 1.子节点: parentNode.firstChild 获取第一个子节点，包含所有的节点
    console.log(ul.firstElementChild);
    console.log(ul.lastElementChild);
    
    // 由于上述存在兼容性问题，于是我们可以使用 parentNode.children 获取元素节点
    var firstNode = ul.children;
    console.log(firstNode[0]);
    console.log(firstNode[firstNode.length - 1]); // 此处使用元素的长度减1，就是最后一个元素节点
</script>
```