# DOM事件流理论

定义：事件流描述的是`从页面中接收事件的顺序`【事件发生时会在元素节点之间按照特定的顺序传播，这个传播过程就是DOM事件流】

![JavaScript-事件高级 - Liyi's personal blog](https://z3.ax1x.com/2021/07/05/RhmW6J.png)

DOM事件流分为3个阶段：

1. 捕获阶段【从document处开始寻找到div处】
2. 当前目标阶段【定位到div处】
3. 冒泡阶段【div处往外查找】

#### 事件冒泡：IE最早提出的，事件开始时由最具体的元素接收，然后逐级向上传播到DOM最顶层节点的过程

#### 事件捕获：网景最早提出的，由DOM最顶层节点开始，然后逐级向下传播到最具体的元素接收的过程

![对JS事件流的深入理解 - 知乎](https://pic3.zhimg.com/v2-4fa0e50fe4db2b07d525c11cac81c172_b.jpg)

例如：我们往水里面扔一块石头，首先它会有一个下落的过程，这个过程就可以理解为从最顶层向事件发生的最具体元素（目标点）的捕获过程；之后会产生泡泡，会在最低点（最具体元素）之后漂浮到水面上，这个过程相当于事件冒泡

## 一、注意点

#### 1.JS代码只可能执行捕获或者冒泡中的一个阶段

#### 2.onclick或者是attachEvent只能得到冒泡阶段

#### 3.addEventListener(type,listener[,useCapture])第三个参数如果是true，表示在事件捕获阶段调用事件处理程序；如果是false（不写默认就是false），表示在事件冒泡阶段调用事件处理程序

```html
<!--    HTML代码-->
<div class="father">
    <div class="son">son盒子</div>
</div>

<!--    JS代码-->
<script>
    //DOM事件流
    //1.JS只可以执行捕获或者是冒泡中的一个阶段
    //2.onclick和attachEvent（IE） 只能得到冒泡阶段
    /* 捕获阶段：第三个参数是true，那么则属于捕获阶段，document-->html--->body--->father--->son */
    var son = document.querySelector('.son');
    var father = document.querySelector('.father');
    son.addEventListener('click',function() {
        alert('son');
    },true);
    father.addEventListener('click',function() {
        alert('father');
    },true);
    /* 冒泡阶段：第三个参数省略或者是false，那么则属于冒泡阶段，son-->father-->body-->html-->document */
    son.addEventListener('click',function() {
        alert('son');
    },false);
    father.addEventListener('click',function() {
        alert('father');
    },false);

</script>
```

## 三、实际开发中的使用

实际开发中我们很少使用事件捕获，我们更关注事件冒泡。有些事件是没有冒泡的，比如onblur、onfocus、onmouseenter、onmouseleave。事件冒泡有时候会带来麻烦，有时候又可以很巧妙地解决某些事情，在4.8《阻止默认行为》中讲解

