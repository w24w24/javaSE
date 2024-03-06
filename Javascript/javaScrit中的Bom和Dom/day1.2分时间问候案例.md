# 分时间段问候案例

要求：

1.根据不同时间，页面显示不同的图片，同时显示不同的问候语

2.如果上午使时间打开界面，显示上午好，显示上午的图片

3.如果下午打开页面，显示下午好，显示下午的图片

4.如果晚上打开页面，显示晚上好，显示晚上的图片



逻辑分析：

1.根据系统的不同时间来判断属于哪一个时间段【所以需要用到日期内置对象】

2.涉及到上午、下午、晚上【所以需要用到多分支语句】

3.需要一张图片，并且根据时间修改图片【也就是修改元素的属性---src】

4.因为要显示不同的问候语，所以我们需要一个div元素【使用innerText或者innerHTML修改元素内容即可】

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>我的第一个JS文件</title>
    <style>
        img {
            width:300px;
            height:300px;
        }
    </style>
</head>
<body>
<img src="photo/上午好.jpg" alt="">
<div>上午好</div>
<script>
    // 1.获取元素
    var img = document.querySelector('img');
    var div = document.querySelector('div');
    // 2.得到当前的小时数
    var date = new Date();
    var h = date.getHours();
    // 判断小时数改变数字和文字信息
    if(h < 12) {
        img.src = 'photo/上午好.jpg';
        div.innerHTML = '亲，上午好，好好写代码';
    }else if(h < 18) {
        img.src = 'photo/下午好.jpg';
        div.innerHTML = '亲，下午好，好好写代码';
    }else {
        img.src = 'photo/晚上好.jpg';
        div.innerHTML = '亲，晚上好，好好写代码';
    }

</script>

</body>
</html>
```