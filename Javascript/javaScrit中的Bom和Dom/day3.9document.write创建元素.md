# document.write创建元素

解析：我们的有些标签，在HTML中是不存在的，所以我们在JS中使用动态方式创建元素，动态创建元素有3种方式：

1.document.write（）

2.element.innerHTML（）

3.document.createElement（）

## 一、区别

1.document.write（）：是直接将内容写入页面的内容流。但是在文档流执行完毕之后，这个方法会导致页面重绘

```html
<!--    HTML代码-->
<span>你是一朵花</span>
<button>创建div</button>

<!--    JS代码-->
<script>
    //1.获取元素
    let button = document.querySelector('button');
    button.onclick = function() {
        document.write('<div>创建成功</div>');
    }
</script>
```

解析：这种方式会导致我们原先创建的页面元素全部被重新绘制，这种创建方式并不好

## 二、innerHTML和createElement效率对比

element.innerHTML 和 document.createElement() 都可以创建元素。
1、element.innerHTML 创建多个元素有两种方式：
①拼接字符串的方式：

```html
var inner = document.querySelector('.inner');
for (var i = 0; i < 100; i++) {
	inner.innerHTML += '<a href="#">百度</a>';
}
```

但其创建并添加上去总共用了3000毫秒左右

②数组形式拼接

```html
var inner = document.querySelector('.inner');
var arr = [];
for (var i = 0; i < 100; i++) {
	arr.push('<a href="#">百度</a>');
}
inner.innerHTML = arr.join('');  //数组转换为字符串
```

用了8毫秒左右

2、document.creatElement()

```html
var create = document.querySelector('.create');
for (var i = 0; i < 100; i++) {
    var a = document.createElement('a');
    create.appendChild(a);
}
```

用了20毫秒左右

## 总结：

1.innerHTML 创建多个元素时（不要拼接字符串，采取数组形式拼接）效率比 createElement() 更高一点

2.虽然innerHTML 的结构相对来说复杂点，但是执行效率高

3.createElement()创建多个元素效率稍微低一点，但是createElement() 的结构更简单清晰。

3.innerHTML是将内容写入某个DOM节点，不会导致页面重新绘制

