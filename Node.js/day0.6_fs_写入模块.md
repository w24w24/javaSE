学习路线图：

![image-20240815202308076](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240815202308076.png)

# 一、_fs模块：文件写入

fs：file System文件系统

示例需求：新建一个文件，名字为“座右铭.txt”，写入内容为“人生自古谁无死，留取丹心照汗青”

```js
/**
 *需求：新建一个文件，名字为“座右铭.txt”，写入内容为“人生自古谁无死，留取丹心照汗青”
 * */ 

// 先导入fs，fs是一个默认的全局模块，不需要下载，直接导入即可
const fs = require('fs');
// 创建文件
fs.writeFile('./座右铭.txt','人生自古谁无死，留取丹心照汗青', err =>{
  if(err) {
    console.log('写入失败...');
    return;
  }
  console.log('写入成功！')
})
```

参数解析：

1、require是固定语法，用来导入模块

2、fs.writeFile(file, data, options, callback)`【file是写入的文件名字、data是写入的内容、options是选项设置、callback是写入成功或者失败的回调函数】`

#### <span style="color:red">注意：fs的文件写入就像是`我们使用wps工作保存文件一样`</span>