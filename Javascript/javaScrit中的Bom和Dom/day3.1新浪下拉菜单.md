# 新浪下拉菜单

1 案例需求
使用JavaScript+css+html制作下拉菜单，当鼠标放在菜单项时，菜单项的背景色会改变，而且会出现二级菜单，当鼠标放在二级菜单上时，二级菜单会变色，当鼠标离开菜单项后，二级菜单隐藏。

2 编写HTML结构代码
在HTML页面代码中，先用列表把菜单的内容做出来，代码如下：

```html
<ul class="nav">
    <li>
        <a href="#">文件</a>
        <ul>
            <li>
                <a href="#">新建文件</a>
            </li>
            <li>
                <a href="#">新建窗口</a>
            </li>
            <li>
                <a href="#">新建文件夹</a>
            </li>
        </ul>
    </li>
    <li>
        <a href="#">编辑</a>
        <ul>
            <li>
                <a href="#">撤销</a>
            </li>
            <li>
                <a href="#">重做</a>
            </li>
            <li>
                <a href="#">剪切</a>
            </li>
        </ul>
    </li>
</ul>
```



3 编写css样式
首先将所有的外边距和内边距都去掉，防止影响页面效果，使用通配符选择器实现该效果。然后将<a>标签的下划线去掉，并且修改字体的大小。最后将列表之前的圆点样式去掉，设置菜单的外边距。代码如下：

```css
* {
    margin: 0;
    padding: 0;
}
li {
    /* 去掉圆点 */
    list-style-type: none;
}
a {
    /* 去掉下划线 */
    text-decoration: none;
    /* 修改字体大小 */
    font-size: 14px;
}
/* 设置最外层ul的样式 */
.nav {
    /* 让这个列表显示往屏幕中间一点 */
    margin: 100px;
}
```


上面这一步对样式进行了初步的设置，根据自己的需求设计即可。接下来设计第一层li的样式。给它设定一个宽高，并且让该块级元素向左浮动，使第一层li排列在一行，紧接着让里面的文字居中。

```css
/* 子元素选择器“>”，选择第一层ul下的li */
.nav>li {
    width: 100px;
    height: 41px;
    float: left;
    text-align: center;
    /* 让下拉菜单紧跟在li下面 */
    position: relative;
}
```


接下来为所有的a标签设置样式。将所有的a标签设置为块级元素，让它们的长宽等于外面块级元素li的长和宽，设置行高，使a标签元素内的文字在垂直方向上居中，最后让其字体颜色变成黑色，并且为其添加边框属性。

```css
/* 后代选择器选择子孙后代，在这里选择所有的a标签 */
.nav li a {
    display: block;
    width: 100%;
    height: 100%;
    line-height: 41px;
    color: black;
    border: solid 1px #FECC5B;
}
```


接着为一级菜单设置伪类。当鼠标悬停在“文件”和“编辑”上时，让这两个a标签的背景色变成灰色，鼠标移开，恢复正常。

```css
.nav>li>a:hover {
    background-color: #eee;
}
```
接下来设置二级菜单的伪类。当鼠标移动到“新建文件”、“撤销”及其下面的列表项时，其背景变色，鼠标移开，恢复正常。可以使用 后代选择器，也可以使用子元素选择器，代码只展示后代选择器，子元素选择器为注释部分。

```css
.nav li ul li a:hover {
    background-color: #FFF5DA;
}
/* .nav>li>ul>li>a:hover {
    background-color: #FFF5DA;
} */
```
最后让二级菜单的ul隐藏起来，达到只显示一级菜单的效果。

```css
.nav ul {
    display: none;
    /* 让下拉列表定位在当前li下方 */
    position: absolute;
}
```
4 编写JavaScript部分
在之前的css样式中，对该菜单的样子做了基本的设置，接下来需要使用JavaScript代码做互动，就是当鼠标移动到两个一级菜单上时，下面的二级菜单会显示出来。

```html
    //1、获取两个一级菜单元素，即两个li：先获取第一层ul，然后获取ul下的子元素li
    var lis = document.querySelector(".nav").children;
    //2、循环给两个li绑定鼠标移进去和移出去的事件
    for (var i = 0; i < lis.length; i++) {
        lis[i].onmouseover = function () {
            //当鼠标移进去时，选择将第一层li（“文件”、“编辑”）下面的第二个子元素li（第一个是a标签）显示出来
            this.children[1].style.display = "block";
        }
        lis[i].onmouseout = function () {
            //当鼠标移出来时，选择将第一层li（“文件”、“编辑”）下面的第二个子元素li（第一个是a标签）隐藏
            this.children[1].style.display = "none";
        }
    }
```
