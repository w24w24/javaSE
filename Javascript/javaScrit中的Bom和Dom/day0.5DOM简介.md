# DOM简介

## 一、什么是DOM？

含义：DOM（Document Object Model）是文档对象模型，处理可扩展标记语言（HTMl或者XML）的标准编程接口，通过DOM接口可以改变网页的内容、结构和样式

## 二、DOM树

![image-20221223172502678](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221223172502678.png)

文档：一个页面就是一个文档，在DOM中使用document表示

元素：页面中的所有标签都是元素，DOM中使用element表示

节点：网页中所有的内容都是节点（标签、属性、文本、注释等等），DOM中使用node表示



#### 注意：DOM把图示内容都看作是对象，既然是对象，那就有自己的属性和方法