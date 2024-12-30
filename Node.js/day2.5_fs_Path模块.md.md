# 一、path模块

path提供了`操作路径`的功能，下面是几个常用的API：

| API                                  | 说明                       |
| ------------------------------------ | -------------------------- |
| path.resolve                         | 拼接规范的绝对路径【常用】 |
| path.sep【separate：单独的、分开的】 | 获取操作系统的路径分割符   |
| path.parse                           | 解析路径并且返回对象       |
| path.basename                        | 获取路径的基础名称         |
| path.dirname                         | 获取路径的目录名           |
| path.extname                         | 获取路径的扩展名           |

# 二、使用path

代码示意：

```js
// 1、导入path模块
const path = require('path');

// 2、使用path模块下的方法
path.resolve(__dirname, './座右铭.txt')
```

#### <span style="color:red">注意：`./`或者是`不写./`是相对路径；`/`是绝对路径</span>

```js
// 相对路径
(./座右铭.txt) 等价于 (座右铭.txt)

// 绝对路径
/座右铭.txt
```

# 三、path.resolve

这个方法是用来规范拼接符号的。为什么需要规范拼接符号？【有时候，我们的路径是`./座右铭.txt`，有时候又是`D:\program`，其中/和\是不规范的，我们在书写代码的时候，需要去规范这两个符号，所以需要使用到path.resolve()方法】

## 1、语法格式

```js
// 引入path模块
const path = require('path');

// 使用path.resolve来规范路径
const res = path.resolve(__dirname, './座右铭.txt');
console.log(res); // D:\index.html/test
```

## 2、参数解析

```
__dirname：是系统的绝对路径

./座右铭.txt：是文件所在的相对路径

path.resovle(__dirname, './座右铭.txt')：是将__dirname绝对路径和./座右铭.txt相对路径拼接起来
```

# 四、path.sep

path.sep是用来分辨不同操作系统中的路径分割符的

```
在windows中的路径分割符：\

在linux中的路径分割符：/
```

# 五、其它方法

```js
const fs = require('fs');
const path = require('path');

// 自定义一个路径
let str = 'D:\\nodeJS\\13-path\\代码\\path.js';

// path.parse()方法解析路径，返回一个对象
console.log(path.parse(str));

// path.basename()方法获取路径的基础名称
console.log(path.basename(str));

// path.dirname()方法获取路径的目录名
console.log(path.dirname(str));

// path.extname()方法获取路径的扩展名
console.log(path.extname(str));
```





#### <span style="color:red">注意： __ dirname是文件夹的绝对路径、 __ filename是文件的绝对路径</span>

```
__dirname：查看文件夹的绝对路径

__filename：查看文件的绝对路径
```

