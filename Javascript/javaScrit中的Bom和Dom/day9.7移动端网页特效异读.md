# 移动端网页特效异读

目标：

1. 可以写出移动端触屏特效
2. 可以写出常见的移动端特效
3. 可以使用移动端开发插件开发移动端特效
4. 可以使用移动端开发框架开发移动端特效

目录：

1. 触屏事件
2. 移动端常见特效
3. 移动端常用开发插件
4. 移动端常用开发框架

# 一、移动端touch触摸事件

触屏事件概述：移动端浏览器兼容性比较好，我们不需要考虑JS的兼容性问题，可以放心使用原生JS书写效果，但是移动端也有自己独特的地方，比如触屏事件touch（也称触摸事件），Android和IOS都有

touch代表一个触摸点，触摸点可能是一根手指，也可能是一根触摸笔，出品事件可以响应用户手指（或触控笔）对屏幕或触控板操作

常见的触屏事件有：

![image-20230302122713628](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302122713628.png)

```html
<script>
   var div = window.document.querySelector('div');
   div.addEventListener('touchstart',function() {
       console.log('我触摸了你');
   });
   div.addEventListener('touchmove',function() {
       console.log('我在你身上滑动');
   });
   div.addEventListener('touchend',function() {
       console.log('我不触摸你，我离开了')
   });
</script>
```

# 二、移动端TouchEvent触摸事件对象

TouchEvent是一类描述手指在触摸平面（触摸屏、触屏版）的状态和事件变化的对象，这类事件用于描述一个或多个触点，使开发者可以检测触点的移动，触点的增加和减少等等

#### 注意：touchstart、touchend、touchmove都有自己的事件对象

![image-20230302124512137](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302124512137.png)

# 三、移动端拖动元素

![image-20230302124956625](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302124956625.png)

# 四、移动端常用开发框架

![image-20230302141618649](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302141618649.png)

![image-20230302142534737](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20230302142534737.png)

## （一）Bootstrapt的使用

1. 首先要下载Bootstrapt文件
2. 因为Bootstrapt是依赖jQuery的，所以要先引入jQuery
3. 引入之后就可以按照下列步骤操作了