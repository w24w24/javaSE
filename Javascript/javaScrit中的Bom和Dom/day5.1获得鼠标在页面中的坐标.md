# 获得鼠标在页面中的坐标

解析：event代表事件的状态，跟事件相关的一系列事件的集合，现阶段我们主要是用鼠标事件对象MouseEvent和键盘事件KeyborderEvent

## 一、鼠标事件对象

1. e.clientX：返回鼠标相对于浏览器窗口可视化的x坐标【client：客户端】

2. e.clientY：返回鼠标相对于浏览器窗口可视化的y坐标

   ```javascript
   <script>
       //使用e.client得到可视化区域的x、y坐标
       document.addEventListener('click',function(e){
           console.log(e.clientX);
           console.log(e.clientY);
       });
   </script>
   ```

   #### 解析：使用client，无论窗口有多大，元素的位置都是相对于可视化区域的边框来计算的，即使元素变化，坐标也不会变化

3. e.pageX：返回鼠标相对于文档页面的x坐标，IE9+支持【重点】

4. e.pageY：返回鼠标相对于文档页面的y坐标，IE9+支持【重点】

   ```javascript
   <script>
       //使用e.page得到页面文档的x、y坐标
       document.addEventListener('click',function(e){
           console.log(e.pageX);
           console.log(e.pageY);
       });
   </script>
   ```

   #### 解析：使用page，坐标是根据页面文档的长度来计算的，页面中的元素大小相同，位置相对于页面相同，但是坐标是不相同的

5. e.screenX：返回鼠标相对于电脑屏幕的x坐标

6. e.screenY：返回鼠标相对于电脑屏幕的y坐标

   ```javascript
   <script>
       //使用e.screen得到页面文档的x、y坐标
       document.addEventListener('click',function(e){
           console.log(e.screenX);
           console.log(e.screenY);
       });
   </script>
   ```