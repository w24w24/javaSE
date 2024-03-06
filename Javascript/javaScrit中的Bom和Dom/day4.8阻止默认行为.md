# 阻止默认行为

解析：由于事件冒泡会带来`坏处`，也会带来好处【这一节重点讲解坏处】

## 一、事件的常见属性和方法

1. e.target：返回触发事件的对象【遵循W3C标准】
2. e.srcElement：返回触发事件的对象【非标准 IE6~8使用】
3. e.type：返回事件的类型【比如：click、mouseover不带on】
4. e.cancelBubble：该属性阻止冒泡【非标准 IE6~8使用】
5. e.returnValue：该属性阻止默认事件（默认行为）【非标准 IE6~8使用 比如：不让链接跳转】
6. e.preventDefault()：该方法阻止默认事件（默认行为）【标准 比如：不让链接跳转】
7. e.stopPropagatioon()：阻止冒泡【标准】

```html
<!--    HTML代码-->
<div>百度</div>
<a href="https://www.baidu.com">百度</a>
<form action="https://www.baidu.com">
    <input type="submit" value="提交" name="sub">
</form>
<!--    JS代码-->
<script>
    //常见事件对象的属性和方式
    //1.返回事件类型
    let div = document.querySelector('div');
    div.addEventListener('click',fn);
    div.addEventListener('mouseover',fn);
    div.addEventListener('mouseout',fn);
    function fn(e) {
        console.log(e.type);
    }
    //2.新方式：阻止默认行为（事件）让链接不跳转、让按钮不提交
    let a = document.querySelector('a');
    a.addEventListener('click',function(e) {
        e.preventDefault();//DOM标准写法
    });
    //3.传统注册方式：阻止默认行为（事件）让链接不跳转、让按钮不提交
    a.onclick = function(e) {
        //普通浏览器：也可以使用：e.preventDefault()
        e.preventDefault();//这是一个方法
        //低版本浏览器：IE6~8
        e.returnValue;//这是一个属性【已被弃用】
        /*我们可以利用return false 也可以阻止默认行为 没有兼容性问题
        但是return之后的代码就不执行了 而且只适用于传统的注册方式
        对于addEventListener()是不起作用的
        */
        return false;
        alert('11');//不执行
    }
</script>
```

## 二、怎样阻止事件冒泡？【面试】

解析：事件冒泡：开始时由最具体的元素接收，然后逐级往上传播到DOM最顶层节点

阻止事件冒泡有两种方式：

1.使用stopPropagation：

```html
<!--    HTML代码-->
<div class="father">
    <div class="son">son盒子</div>
</div>

<!--    JS代码-->
<script>
    //阻止事件冒泡
    //1.使用stopPropagation()方法：
    var son = document.querySelector('.son');
    var father = document.querySelector('.father');
    /* 冒泡阶段：第三个参数省略或者是false，那么则属于冒泡阶段，son-->father-->body-->html-->document */
    son.addEventListener('click',function(e) {
        alert('son');
        e.stopPropagation();
    },false);
    father.addEventListener('click',function() {
        alert('father');
    },false);
```

解析：但是以上语法存在兼容性问题，IE6~8不支持，该怎么解决呢？这个时候就用到第二种方法了

2.使用e.cancelBubble = boolean:

```html
<!--    HTML代码-->
<div class="father">
    <div class="son">son盒子</div>
</div>

<!--    JS代码-->
<script>
    //阻止事件冒泡
    //1.使用cancel.Bubble方法：
    var son = document.querySelector('.son');
    var father = document.querySelector('.father');
    /* 冒泡阶段：第三个参数省略或者是false，那么则属于冒泡阶段，son-->father-->body-->html-->document */
    son.addEventListener('click',function(e) {
        alert('son');
        e.stopPropagation();//新版本支持 但是IE6~8不支持
        e.cancelBubble = true;//旧版本 IE6~8支持
    },false);
    father.addEventListener('click',function() {
        alert('father');
    },false);

</script>
```

## 三、为了解决兼容性问题

解析：封装一个兼容性函数：

```javascript
//封装一个兼容性函数：
if(event && event.stopPropagation) {
    event.stopPropagation();
}else{
    window.event.cancelBubble = true;
}
```
