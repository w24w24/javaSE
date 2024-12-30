# 一、_fs模块：文件流式写入：createWriteStream('文件路径及其名称')

解析：文件流式写入是`一边将文件内容写入缓存，一边由消费者去读取，不用先将整个文件写进内存，从而节省空间`

```js
// 步骤1：先创建一个流式通道【可以不用，但是要有，后面可以随时使用】

// 步骤2：使用write方法，往这个文件中写入内容【write方法可以多次且重复使用】

// 步骤3：使用完毕之后关闭流式通道，避免内存占用
```

代码演示：

```js
const fs = require('fs');

// 先创建一个流是文件，作为备用
const ws = fs.createWriteStream('./演示.txt');

// 使用write写入内容
ws.write('半亩方塘一鉴开，');
ws.write('天光云影共徘徊。');
ws.write('\r\n问渠哪得清如许，');
ws.write('为有源头活水来。');

// 关闭流式管道
ws.close();
```



# 二、createWriteStream流式文件写入和wirteFile文件写入的区别

1、createWriteStream流式文件写入举例：

```
Jack不会做西红柿炒鸡蛋，于是打电话询问Jerry
Jerry告诉Jack第一步该去洗西红柿，期间Jack会频繁的询问Jerry
Jack不会挂断电话，这个电话链接了Jack和Jerry，就叫做流式写入

上述例子就是：createWriteStream流式文件
优势：适合于大文件的写入、频繁写入
```

2、wirteFile文件写入举例：

```
Jack拿水杯去接水，接完水就关闭了水龙头
这个时候水杯和水龙头就断开了链接

上述例子就是：wirteFile文件写入
优势：适合于一次性文件的写入、写入频率较低的场景
```

