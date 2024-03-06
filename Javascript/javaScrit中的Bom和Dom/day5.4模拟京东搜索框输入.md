# 模拟京东搜索框输入

解析：在京东的界面中，只要我们按下了s键，就直接在搜索框获得焦点

第一种方式：使用keyCode【已被弃用】：

```html
<form action="javascript:void(0)">
    <input type="text">
</form>

<!--    JS代码-->
<script>
    let search = document.querySelector('input');
    document.addEventListener('keyup',function(e) {//要在整个文档页面中起作用，所以是document
        //测试s键的ASCII值
        //console.log(e.keyCode);
        if(e.keyCode === 83) {
            search.focus();//这是一个方法，所以需要括号
        }
    });
</script>
```

第二种方法：使用key【标准】

```html
<form action="javascript:void(0)">
    <input type="text">
</form>

<!--    JS代码-->
<script>
    let search = document.querySelector('input');
    document.addEventListener('keyup',function(e) {//要在整个文档页面中起作用，所以是document
        //测试s键的ASCII值
        //console.log(e.keyCode);
        if(e.key === 's') {
            search.focus();//这是一个方法
        }
    });
</script>
```