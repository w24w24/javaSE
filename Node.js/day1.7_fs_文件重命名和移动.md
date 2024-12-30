# 一、文件重命名和移动

解析：重命名就是将已有的文件的“名字进行更改”【当你更改名字的时候，可以将更改后的新文件放置和旧文件同一个目录下，也可以重新指定目录，这也是“文件的重命名和移动这一章节联系在一起的原因”】

# 二、语法【共2种】

解析：在Node.js中，我们可以使用rename或者是renameSync来移动或者是重命名文件或者是文件夹

## 1、语法：

```node.js
语法1：fs.rename(oldPath, newPath, callback)

语法2：fs.renamesync(oldPath, newPath)
```

## 2、代码展示：

```js
const fs = require('fs');

fs.rename('./演示_1.txt', '../我已经被重命名了.txt', (err) => {
  if(err) {
    console.log('操作失败~');
    return;
  }
  console.log('操作成功')
})

// oldPath：当前文件的路径
// newPath：文件新的路径
// callback：操作后的回调
```

## 3、参数说明：

1、`./演示_1.txt`是原文件的路径和名字，`../我已经被重命名了.txt`是新文件的路径和名字

2、还有一个回调函数，这个回调函数只有一个参数，就是err，是用来处理成功或者是失败之后的操作的
