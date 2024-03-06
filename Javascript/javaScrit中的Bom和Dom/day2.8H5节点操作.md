

# 为什么要学习节点操作以及节点简介

## 一、为什么要学习节点？

解析：节点的目的主要还是获取元素

获取元素有2种方式：以下这两种方式都可以获取元素节点，我们后面都会使用，但是节点操作更为简单

### 1.利用DOM提供的方法或者是API获取元素：

document.getElementById();

document.getElementByTagName();

document.querySelector()等等

缺点是：逻辑性不强，非常的繁琐。意思是只要操作，都要对其中进行获取

### 2.利用节点的层级关系进行获取：

优点：利用父子兄节点关系获取元素，逻辑性强，但是兼容性稍差

## 二、上面是节点？

解析：网页中的所有元素都是节点（标签、属性、文本、注释等等），在DOM中，节点使用node来表示。HTML  DOM树中的所有节点均可以通过javaScript访问，所有HTML元素（节点）均可被修改，也可以创建或者删除

![image-20230131153445476](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230131153445476.png)

## 三、节点概述？

解析：一般的，节点至少拥有nodeType（节点类型）、nodeName（节点名称）、nodeValue（节点值）这三个基本属性

![image-20230131154118692](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230131154118692.png)

1.元素节点nodeType为1

2.属性节点nodeType为2

3.文本节点nodeType为3【文本节点包括文字、空格、换行等】

#### 在实际开发中，节点操作主要操作的是元素节点