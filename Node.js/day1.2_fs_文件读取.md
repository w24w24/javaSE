# 一、_fs模块：文件读取

文件读取顾名思义，就是通过程序从文件中取出其中的数据，我们可以使用下面的方式：

| 方法             | 说明     |
| ---------------- | -------- |
| readFile         | 异步读取 |
| readFileSync     | 同步读取 |
| createReadStream | 流式读取 |

代码示例：

```js
// 引入fs模块
const fs = require('fs');

// 1、同步读取文件
fs.readFile('./演示.txt', (err, data) => {
  if(err) {
    console.log('文件读取失败',err);
    return;
  }
  console.log(data.toString());
})

// 2、异步读取文件
let data = fs.readFileSync('./名言警句.txt');
console.log(data.toString());
```

