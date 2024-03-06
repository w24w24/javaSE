# 节点操作之删除节点

## 一、删除节点

解析：我们可以在页面中增加节点，也可以删除节点，JS为我们提供了以下方式删除节点：

```javascript
node.removeChild(child);
```

node.removeChild(child)方法是从DOM中删除一个子节点，然后返回当前的节点

```html
<!--    HTML代码-->
<button>删除</button>
<ul>
    <li>熊大</li>
    <li>熊二</li>
    <li>光头强</li>
</ul>

<!--    JS代码-->
<script>
    // 1.获取元素
    var ul = document.querySelector('ul');
    var btn = document.querySelector('button');
    // 3.点击按钮，依次删除
    btn.onclick = function() {
        if(ul.children.length === 0) {
            this.disabled = true;
        }else {
            ul.removeChild(ul.children[0]);
        }
    }
</script>
```

解析：当所有的元素都已经被删除了，那么就禁用按钮，让它不再删除
