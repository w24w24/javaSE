# 一、查看资源状态

在Node.js中，我们可以使用stat或者是statSync来查看资源的详细信息

语法：

```
语法1：fs.stat(path[, options], callback)

语法2：fs.statSync(path[, options])
```

参数说明：

```
path：文件夹路径

options：选项配置（可选）

callback：操作后的回调
```

示例代码：

```js
// 引入fs模块
const fs = require('fs');


// 异步查看文件夹资源状态
fs.stat('../node', (err, data) => {
  if(err) {
    console.log('操作失败');
  }
  console.log(data);
})

// 同步查看文件夹资源状态
// 同步查看文件夹资源状态
const res = fs.statSync('../node')
console.log(res);
```

结果值对象结构：

```
size：文件体积

birthtime：创建时间

mtime：最后修改时间

isFile：检测是否为文件

isDirectory：检测是否为文件夹
```

