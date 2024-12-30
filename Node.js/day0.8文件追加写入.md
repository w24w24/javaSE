# 一、_fs模块：文件追加写入

解析：追加写入就是在一个文件里面添加新的数据

1、语法：

```
1、fs.appendFile(file路径，data[, options]要写入的数据，callback异步回调函数)

2、fs.appendFileSync(file路径，data[, options]要写入的数据)
```

2、二者的返回值都是undefined

```js
const fs = require('fs');
// 追加文件
const res1 = fs.appendFileSync('./名言警句.txt','\r\n选其善者而改之，其不善者而从之');
const res2 = fs.appendFile('./名言警句.txt','\r\n你好，世界！');
console.log(res1); // undefined
console.log(res2); // undefined
```

# 二、appendFile/appendFileSync追加写入

1、appendFile：appendfile的作用是在文件尾部追加内容，appendFile语法和writeFile语法完全相同，但是需要添加一个参数{flag: 'a'}【a的意思是appendFile追加；还有w，意思是writeFile写入；还有一个是r，意思是readFile读取】。文件追加多数使用在`日志、用户登录时间`等场景

```js
// appendFile文件追加写入
const fs = require('fs');
// 追加文件
fs.appendFile('./名言警句.txt','\r\n选其善者而改之，其不善者而从之', err => {
  if(err) {
    console.log('追加失败~~');
    return;
  }
  console.log('追加成功')
})


// writeFile文件写入，携带{flag: 'a'}参数，和appendFile的作用是一样的
const fs = require('fs');
// 追加文件
fs.writFile('./名言警句.txt','\r\n选其善者而改之，其不善者而从之', {flag: 'a'} ,err => {
  if(err) {
    console.log('追加失败~~');
    return;
  }
  console.log('追加成功')
})
```



2、appendFileSync：appendFileSync的作用也是在尾部追加内容，只是是同步代码，没有回调函数

```js
const fs = require('fs');
// 追加文件
fs.appendFileSync('./名言警句.txt','\r\n选其善者而改之，其不善者而从之');
```

