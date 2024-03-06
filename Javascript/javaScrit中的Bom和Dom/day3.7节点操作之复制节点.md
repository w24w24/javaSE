# 节点操作之复制节点

## 一、复制节点（clone节点）

解析：在实际的开发中，我们想要复制一份节点，通过ctrl+c显示是不满足实际的，所以JS为我们提供了以下语法：

```html
node.cloneNode();
```

解析：node.cloneNode()方法返回调用该方法的节点的一个副本，也称之为克隆节点/拷贝节点

## 注意：在node.cloneNode（），当括号里面的参数为空或者是false，都是浅拷贝，所谓的浅拷贝就是只复制标签，但是不复制内容（术语：浅拷贝，只复制当前的节点本身，不复制节点内部的子节点）。想要解决这一问题，只需要在括号内部加上布尔值true即可

```html
<!--    HTML代码-->
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>

<!--    JS代码-->
<script>
    // 1.获取事件
    var ul = document.querySelector('ul');
    // 1.node.cloneNode()
    var cloneLi = ul.children[0].cloneNode(true);// 单纯的clone是不会显示的，需要使用添加节点的方式显示
    ul.appendChild(cloneLi);//但是这样的clone并没有内容，在括号内部加上true，就会复制到所有
</script>
```

总结：node.cloneNode（）

1.如果括号里面为空或者是false，则是浅拷贝，即只克隆复制节点本身，不克隆里面的子节点

2.如果括号参数为true，则是深拷贝，会复制节点本身以及里面的所有字节点
