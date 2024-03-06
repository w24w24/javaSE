# 操作元素---获取自定义属性值

## 一、我们之前所学的是什么？

解析：我们之前所学的都是：

1.获取元素的属性，如：src、style、href、id、class等；

2.获取元素的属性值，如：element.属性【获取属性值】、element.getAttribute('属性')

```html
<!--这里是Javascript代码-->
<script>
    // 1.第一种获取方法
    var div = document.querySelector('div');
    console.log(div.id);
    // 2.第二种获取方法
    console.log(div.getAttribute('id'));
</script>

```

## 二、element.属性和element.getAttribute('属性')的区别是什么？

解析：

1.element.属性：获取的是内置属性值（元素本身自带的属性：如div自带的id、class属性）

2.element.getAttribute('属性')：获取的是自定义的属性（标准），程序员自己定义的属性。

解析：在实际的开发中，我们通过class和id获取属性已经不能够支持我们使用，于是这个时候，我们就会自定义属性，在众多的数据组别中区别和判断谁是谁，该调用谁

## 三、可不可以修改这些属性值呢？

解析：是可以的

1.修改使用`element.属性`获取到的值：

```html
<!--这里是HTML代码-->
<div id="demo" index="1"></div>

<!--这里是Javascript代码-->
<script>

    var div = document.querySelector('div');
    // element.属性 = ''修改属性值
    div.id = 'wang'; // 初始值设置为 demo，现在赋值为 wang
```

2.修改使用element.getAttribute('属性')获取到的值：element.setAttribute('属性','值')

```html
<!--这里是HTML代码-->
<div id="demo" index="1"></div>

<!--这里是Javascript代码-->
<script>

    var div = document.querySelector('div');
    // 修改使用 element.getAttribute('属性') 获取到的值
    div.setAttribute('index','5');
    console.log(div.getAttribute('index'));

</script>
```

3.移除属性：element.removeAttribute('属性');

```html
<!--这里是HTML代码-->
<div id="demo" index="1"></div>

<!--这里是Javascript代码-->
<script>

    var div = document.querySelector('div');
    //  移除属性 element.removeAttribute('属性');
    div.removeAttribute('index');
    console.log(div.getAttribute('index')); // 已经移除了，所以最后得到的是null

</script>
```

4.H5新增获取属性方法：注意这种新增的获取方式存在兼容性问题，注意使用

```html
<!--这里是HTML代码-->
<div id="demo" data-index="1"></div>

<!--这里是Javascript代码-->
<script>

    var div = document.querySelector('div');
    //  H5新增获取属性方式
    console.log(div.dataset.index);
    console.log(div.dataset['index']);
    
</script>
```

解析：dataset是一个集合，里面包含了所有的data开头的自定义属性值

```html
<!--这里是HTML代码-->
<div data-time="20" data-list-name="50"></div>

<!--这里是Javascript代码-->
<script>
    let gainAttribute = document.querySelector('div');
    // 使用getAttribute获取到属性
    console.log(gainAttribute.getAttribute('data-time'));
    console.log(gainAttribute.getAttribute('data-list-name'));
    // 使用dataset获取属性 如果自定义属性里面有多个 — 连接的单词，使用dataset调用的时候，采用驼峰命名法
    
    console.log(gainAttribute.dataset.listName);
    console.log(gainAttribute.dataset['listName']);
</script>
```

## 四、为什么需要自定义属性？

解析：

因为数据都是存放在服务器的，我们使用数据的时候一般都是从跟后台调过来使用的。为了提高执行效率，我们使用自定义属性将简单数据存放在页面上，以便于直接调用，比如setAttribute和getAttribute
