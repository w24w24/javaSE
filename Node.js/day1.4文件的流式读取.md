# 一、_fs模块：文件的流式读取

语法格式：

```js
const fs = require('fs');

// 创建读取流
const rs = fs.createReadStream('./演示.txt');

// 开始读取数据
rs.on('data', chunk => {
  console.log(chunk.length);
})

// 读取结束提示信息
rs.on('end', () => {
  console.log('读取完成~');
})
```

