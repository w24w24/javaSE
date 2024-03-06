# 模拟京东单号查询

```html
<!--    这里是css代码-->
    <style>
    * {
    margin: 0;
    padding: 0;
    }

    .search {
    position: relative;
    width: 178px;
    margin: 100px;
    }

    .con {
    display: none;
    position: absolute;
    top: -40px;
    width: 171px;
    border: 1px solid rgba(0, 0, 0, .2);
    box-shadow: 0 2px 4px rgba(0, 0, 0, .2);
    padding: 5px 0;
    font-size: 18px;
    line-height: 20px;
    color: #333;
    }

    .con::before {
    content: '';
    width: 0;
    height: 0;
    position: absolute;
    top: 28px;
    left: 18px;
    border: 8px solid #000;
    border-style: solid dashed dashed;
    border-color: #fff transparent transparent;
    }
    </style>
</head>

<body>
<div class="search">
    <div class="con">123</div>
    <input type="text" placeholder="请输入您的快递单号" class="jd">
</div>
<script>
    let con = document.querySelector('.con');
    let search = document.querySelector('.jd');
    search.addEventListener('keyup',function(){
        if(this.value === '') {//如果内容为空，就隐藏放大框
            con.style.display = 'none';
        }else{//如果有内容，就把内容给到放大框
            con.style.display = 'block';
            con.innerText = this.value;
        }
    //当我们失去焦点的时候，就隐藏整个盒子
    search.addEventListener('blur',function() {
        con.style.display = 'none';
    });
    //当我们获得焦点的时候，就显示盒子
    search.addEventListener('focus',function() {
        if(search.value !== '') {
            con.style.display = 'block';
        }
    });
    });
</script>
```

解析：

#### （一）为什么要使用keyup，不使用keydown和keypress？

解析：因为keydown是键按下时候就已经触发了，所以会导致内容无法被写入文本框，只有在第二个键按下的时候，才会显示第一个键；keypress是只有在第三个键按下的时候才会显示，所以这两个都不可以使用，最好的是keyup

#### （二）获得焦点的时候，为什么要使用if语句？

解析：因为文本框在获得焦点的时候，都会显示隐藏的方法框，只有当文本框里面有内容的时候，才可以显示放大的文本框，所以要使用if判断语句值不为空才可以