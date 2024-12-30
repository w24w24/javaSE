# 一、复制文件【2种方式】

## 一、先读取，再创建

```js
const fs = require('fs');

// 读取文件
let data = fs.readFileSync('./演示.txt');

// 将读取到的data文件写入新的文件中
if(data) {
  fs.writeFileSync('./演示.txt_2', data);
  console.log('写入成功');
}else {
  console.log('写入失败~');
}
```

## 二、流式复制（使用流式读取，流式复制）



```js
const fs = require('fs');

// 创建流式读取
let rs = fs.createReadStream('./演示.txt');

// 创建流式写入
let ws = fs.createWriteStream('./演示_2.txt');

// 绑定data事件：读取到一个rs数据，就在ws中写入一个数据
rs.on('data', chunk => {
  ws.write(chunk);
  console.log('success');
});
// 等待所有数据读取完毕，给与提示
rs.on('end', () => {
    console.log('数据全部读取完毕~')
})



// 上述可以简写为下面：
const fs = require('fs');

// 创建流式读取
let rs = fs.createReadStream('./演示.txt');

// 创建流式写入
let ws = fs.createWriteStream('./演示_2.txt');

// 将rs读取到的数据给到ws
rs.pipe(ws);
// pipe的意思是管道的意思
```

# 二、哪一种读取方式更好？

解析：

1、第一种方式是将所有的数据全部读取到内存中，这样会占用特别多的内存空间【不太好】

2、第二种方式是流式读取，会一点一点的读取数据，这样占用的内存空间会比较小【比较好】

内存占用演示：

```js
const fs = require('fs');
const process = require('process');

/** 
 * 第一种读取方式
*/

// 读取文件
let data = fs.readFileSync('./演示.txt');
// 将读取到的data文件写入新的文件中
if (data) {
  fs.writeFileSync('./演示_1.txt', data);
  console.log('写入成功');
} else {
  console.log('写入失败~');
};
// 查看内存使用量
console.log(process.memoryUsage());

/**
 * 第二种读取方式
 */

// 创建流式读取
let rs = fs.createReadStream('./演示.txt');
// 创建流式写入
let ws = fs.createWriteStream('./演示_2.txt');
// 绑定data事件：读取到一个rs数据，就在ws中写入一个数据
rs.on('data', chunk => {
  ws.write(chunk);
  console.log('success');
});
// 上面的函数是一个异步回调函数，所以需要等待所有的数据读取完毕，再进行下一步操作
rs.on('end', () => {
  // 查看内存使用量
  console.log(process.memoryUsage());
})
```

