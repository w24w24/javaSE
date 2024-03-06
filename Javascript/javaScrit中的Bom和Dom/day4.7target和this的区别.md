# target和this的区别

## 一、e.target返回的是触发事件的对象（元素）；this返回的是绑定事件的对象（元素）

```html
<!--    HTML代码-->
<div>测试</div>
<ul>
    <li>你好</li>
    <li>爱你</li>
    <li>不知道</li>
</ul>

<!--    JS代码-->
<script>
    // e.target和this
    let div = document.querySelector('div');
    div.addEventListener('click',function(e) {
        console.log(e.target);//返回的是触发事件的对象
        console.log(this);//返回的是绑定事件的对象
    });
    //是不是不够明白，看下面这个例子：
    let ul = document.querySelector('ul');
    ul.addEventListener('click',function(e) {
        console.log(e.target);//点击li，由于是li触发的，所以返回的是li对象
        console.log(this);//点击li，由于绑定的是ul，所以返回的是ul
    });
    //但是e.target仍然存在兼容性问题，可以这样解决：
    div.onclick = function(e) {
        e = e || window.event;
        let target = e.target || e.srcElement;
        console.log(target);
    }
</script>
```