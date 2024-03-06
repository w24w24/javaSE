# 获取元素

DOM在我们的实际开发中主要是用来操作元素的

## 一、我们如何获取页面中的元素呢？

1.根据ID获取

2.根据标签名获取

3.通过HTML5新增的方法获取

4.特殊元素获取

## 二、根据ID获取：getElementById('参数名')

使用getElementById()方法可以获取带有ID的对象元素

```html
<body>
    <div id="time">2019-9-9</div>
<script>
    // 因为文档页面是从上往下加载的，所以得先有标签，所以script吓到标签得下面
    var str = document.getElementById('time');
    console.log(str);
    console.log(typeof str); // 返回的是一个元素对象
    console.dir(str); // 打印我们返回的元素对象，更好查看里面的属性和方法
</script>

</body>
```

解析：

1.因为文档页面是从上往下加载的，所以得先有标签，所以script吓到标签得下面

2.get 获得；element 元素；by 通过；【驼峰命名法】

3.参数id是大小写敏感的字符串【既然是字符串，在使用getElementById('参数名')时，参数名就一定要使用引号引起来，否则出现错误】

4.在使用getElementById('参数名')获取后返回的是元素对象

## 三、根据标签名获取：getElementsByTagName('参数名')

使用getElementsByTagName()方法可以返回带有指定标签名的对象的集合

```html
<body>
    <ul>
        <li>知否知否，应是等你好久1</li>
        <li>知否知否，应是等你好久2</li>
        <li>知否知否，应是等你好久3</li>
        <li>知否知否，应是等你好久4</li>
        <li>知否知否，应是等你好久5</li>
    </ul>
<script>
    // 1.返回的是 获取过来对象的集合，以为数组的形式存储的
    var lis = document.getElementsByTagName('li');
    // 想要依次打印里面的元素对象，可以采用遍历的形式
    for (var i = 0; i < lis.length; i++) {
        console.log(lis[i]);
    }
    // 3.如果页面中只有一个li 返回的还是伪数组的形式
    // 4.如果页面中没有这个元素，返回的是空的伪数组元素
</script>
```

解析：

1.使用getElementsByTagName()获取元素，返回的元素对象是以数组的形式返回的

2.如果在获取中，页面中间只有一个li元素，那么返回得到元素对象依旧是以伪数组形式展现的

3.如果页面中没有获取的元素，那么返回的不是null，也不是undefined，依旧一个空的伪数组的形式

### 假设同时有ol和ul，怎么获取ol里面li？

解析：我们可以使用element.getElementsByTagName('参数名')（此方法需要和document.getElementsByTagName()结合使用【因为此种方法返回的是伪数组的形式】）获取【element指的是父级元素，如ol、ul】

```html
<body>
    <ul>
        <li>知否知否，应是等你好久1</li>
        <li>知否知否，应是等你好久2</li>
        <li>知否知否，应是等你好久3</li>
        <li>知否知否，应是等你好久4</li>
        <li>知否知否，应是等你好久5</li>
    </ul>
    
    <ol id = "ol">
        <li>你是谁呀！1</li>
        <li>你是谁呀！2</li>
        <li>你是谁呀！3</li>
        <li>你是谁呀！4</li>
        <li>你是谁呀！5</li>
    </ol>
    
    <ol>
        <li>你爱我吗</li>
        <li>你爱我吗</li>
    </ol>
<script>
    // 第一种：直接使用数组形式获取
    // 下面这两行代码必须同时出现，并且配合使用，第一条代码返回的是整个界面中的ol，第二条限定是哪一条ol里面的li
    var ol = document.getElementsByTagName('ol'); // 因为这里的ol返回的是伪数组的形式，所以需要进一步确定想要返回哪一个ol
    console.log(ol[1].getElementsByTagName('li')); // 这里的ol[1]就是返回索引号为1的ol里面的所有li
    
    
   // 第二种：通过ID获取
    var ol = document.getElementById('ol');
    console.log(ol.getElementsByTagName('li'));
</script>

</body>
```

解析：

因为在html文档中，我们的ol或者是ul又多个，但是我们只是想要其中的某一个，所以就要进行筛选，但是应该怎么筛选呢？

使用element.getElementsByTagName('参数名')，element指的是父级元素，并且在获取的时候，，父元素必须是单个对象（必须指明是哪一个对象元素），获取的时候不包括父元素自己