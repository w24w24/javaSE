# 一、相对路径的Bug与解决

1、相对路径的参照物：命令行的工作目录

![image-20241007210145880](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20241007210145880.png)

2、绝对路径“全局变量”保存的是：所在文件的所在目录的绝对路径【如：D:\program....】



# 二、运行时路径Bug出现

当我们在外部运行代码、查看文件、写入文件的时候，如果命令行目录和执行代码的目录不在同一个目录下，那么就会报错

如何解决呢？

# 三、运行路径Bug解决

利用`__dirname`查看文件的绝对路径，然后拼接上相对路径即可，这样即使命令行目录和运行目录不同，都不会产生

代码演示：

```js
const fs = require('fs');

// 之所以“/index.html”不写为“./index.html”，是因为__dirname后面没有“/符号”
fs.writeFileSync(__dirnamer + '/index.html', 'love');
```

