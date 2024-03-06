# DOM的重点核心

## 一、什么是DOM？

解析：DOM就是文档对象模型（Document Object Model，简称DOM），是w3c组织推荐的处理可扩展标记语言（HTML/XML）的标准`编程接口`。W3C组织已经定义了一系列的DOM接口，通过这些DOM接口可以改变网页的内容、样式和结构，有以下好处：

1.对于javaScript，为了能够让javaScriot可以操作HTML，javaScript有属于自己的一套DOM编程接口

2.对于HTML，DOM使HTML形成了一棵DOM树，包含文档【整个页面】、元素【页面中的所有标签】、节点【页面中所有的内容】

3.我们获取过来的DOM元素是一个对象（object），所以称之为文档对象模型

## 二、关于DOM操作

解析：DOM操作，我们主要是针对于元素的操做，主要是`创建、增、删、改、查、属性操作、事件操作`

#### （一）创建

1.document.write（）

2.innerHTML

3.createElement（）

## （二）增

1.appendChild

2.insertBefore

## （三）删

1.removeChild

## （四）改

解析：主要是修改DOM元素的属性，DOM元素的内容、属性、表单的值等等

1.修改元素属性：src、href、title等等

2.修改普通元素内容：innerHTML、innerText

3.修改表单元素：value、type、disabled等等

4.修改元素样式：style、className

## （五）查

解析：主要获取查询DOM的元素

1.DOM提供的获取API的方式：getElementById、getElementByTagName【古老用法不太推荐】

2.H5提供的新方法：querySelector、querySelectorAll【提倡使用】

3.利用节点操作获取元素：父节点（parentNode）、子节点（children）、兄弟节点（previousElementSibling、nextElementSibling）【提倡使用】

## （六）属性操作

解析：主要针对于自定义属性

1.setAttribute：设置DOM的属性值

2.getAttribute：得到DOM的属性值

3.removeAttribute：移除属性值

## （七）事件操作

解析：给元素注册事件，采取 `事件源.事件类型 = 事件处理程序`

鼠标事件：

1.onclick：鼠标点击左键触发

2.onmouseover：鼠标经过触发

3.onmouseout：鼠标离开触发

4.onfocus：获得鼠标焦点触发

5.onblur：失去鼠标焦点触发

6.onmousemove：鼠标移动触发

7.onmouseup：鼠标弹起触发

8.onmousedown：鼠标按下触发
