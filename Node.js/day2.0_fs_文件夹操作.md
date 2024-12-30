# 一、文件夹的基本操作

解析：借助Node.js的能力，我们可以对文件夹进行创建、读取、删除等操作

| 方法                | 说明       |
| ------------------- | ---------- |
| mkdir/mkdirSync     | 创建文件夹 |
| readdir/readdirSync | 读取文件夹 |
| rmdir/rmdirSync     | 删除文件夹 |

# 二、创建文件夹

解析：在Node.js中，我们可以使用mkdir/mkdirSync来创建文件夹

语法：

```
语法1：fs.mkdir(path[, options], callback)

语法2：fs.mkdirSync(poath[, options])
```

代码示例：

```js
const fs = require('fs');


// mkdir单个创建文件夹
fs.mkdir('./素材拍摄', (err) => {
  if(err) {
    console.log('创建失败~');
    return;
  }
  console.log('创建成功~');
})

//mkdir递归创建文件夹，recursive就是递归的意思【递归创建就是连续创建】
fs.mkdir('./a/b/c', {recursive: true}, err => {
    if(err) {
        conosle.log('创建失败');
    }
    console.log('创建成功')
})
```



# 三、读取文件夹

解析：在Node.js中，我们一般使readdir来读取文件

语法：

```js
语法1：fs.readdir(path[, options], callback) // callback即 (err, date) {...}
语法2：fs.readdirSync(path[, options])
```

代码示例：

```js
// 引入fs模块
const fs = require('fs');

// 读取文件
fs.readdir('./', (err, date) => {
  if(err) {
    console.log('读取失败', err);
  }
  console.log(date);
})


// 读取文件
const date = fs.readdirSync('../node');
console.log(date);
```



# 四、删除文件夹

解析：在Node.js中，我们可以使用rmdir/rmdirSync【或者是rm/人mSync】。rm和rmSync是未来用来代替rmdir和rmdirSync的

语法：

```
语法1：fs.rmdir(path[, options], callback)

语法2：fs.rmdirSync(path[, options])

语法3：fs.rm(path[, options], callback)

语法4：fs.rmSync(path[, options])
```

代码示例：



```js
// 引入fs模块
const fs = require('fs');


// 下面这种方式是无法进行删除的，因为a文件夹中还有文件
fs.rmdir('./a', err => {
  if(err) {
    console.log('删除失败', err);
      return;
  }
  console.log('删除失败');
})


// 如果要删除，必须使用递归删除，也就是启用recursive: true
// 但是未来时间内，rmdir这个方法可以会被移除，使用rm来替代rmdir，所以尽可能使用rm来删除文件夹
fs.rmdir('./a', {recursive: true}, err => {
  if(err) {
    console.log('删除失败', err);
      return;
  }
  console.log('删除失败');
})


// rm代替rmdir删除文件夹
fs.rm('./a', {recursive: true}, err => {
    if(err) {
        console.log('删除失败~');
        return;
    }
    console.log('删除成功~');
})
```

