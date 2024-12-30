# 一、文件删除

解析：在Node.js中，我们可以使用unlink或者是unlinkSync来删除文件

## 语法一：

```node.js
语法1：fs.unlink(path, callback);

语法2：fs.unlinkSync(path);
```

## 语法二：

```
语法1：fs.rm(path, callback);

语法2：fs.rmSync(path);
```

## 2、参数说明：

1、path：文件的路径

2、callback：操作后的回调

## 3、代码示例

```js
const fs = require('fs');


// unlink和unlinkSync
fs.unlink('../我已经被重命名了.txt', (err) => {
  if(err) throw err;
  console.log('删除成功~');
});
fs.unlinkSync('../我已经被重命名了.txt');


// rm和rmSync
fs.rm('../我已经被重命名了.txt', (err) => {
  if(err) {
      console.log('删除失败~');
      return;
  };
  console.log('删除成功~');
});
fs.rmSync('../我已经被重命名了.txt');
```

