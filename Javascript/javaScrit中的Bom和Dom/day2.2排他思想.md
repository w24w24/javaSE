# 排他思想：利用双重for循环达到“多项单选”的效果

解析：在实际的开发中间，我们一般需要在多个项目组之间选择一个，比如多个按钮点击一个等

```html
<!--这里是HTML代码-->
<button>按钮1</button>
<button>按钮2</button>
<button>按钮3</button>
<button>按钮4</button>
<button>按钮5</button>

<!--这里是Javascript代码-->
<script>
    // 1.获取事件
    var btn = document.getElementsByTagName('button');
    // 2.注册事件   处理程序
    // 使用for循环
    for (var i = 0; i < btn.length; i++) {
        btn[i].onclick = function() {
            // 需要再使用一个for循环清除所有按钮的背景颜色
            for (var i = 0; i < btn.length; i++) {
                btn[i].style.backgroundColor = '';
            }
            this.style.backgroundColor = 'pink';
        }
    }
</script>
```

解析：在内部使用双重for循环，第一个for循环是为了批量注册鼠标点击事件，第二个for循环是为了清除所有的按钮的背景颜色，之后再设置鼠标单击按钮要变化的颜色【即类似HTML中的单选按钮，将项目组归在一个类里面，只操作想要操作的项目】，这就是排他思想

## 总结：

如果有同一组元素，我们想要某一个元素实现某一种样式，需要用到循环的排他思想

1.所有元素的样式全部清除（干掉其它人）

2.给当前元素设置样式（留下自己）

3.注意顺序不允许颠倒，先干掉其它人，再留下自己