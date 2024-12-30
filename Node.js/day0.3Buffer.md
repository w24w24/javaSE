# 一、buffer

图示：

![image-20240813223218648](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240813223218648.png)

解析：Buffer译为`缓冲区`，是一个类似于Array的对象，用于表示固定长度的字节序列

通俗：Buffer就是一段固定长度的内存空间，用于处理二进制数据

#### Buffer的作用：是Node.js的一个API，用来`处理二进制流数据`或者`与之进行交互`，无需require，全局使用，用于操作网络协议、数据库、图片和文件I/O等一些大量二进制数据的场景

# 二、Buffer的特点

1、Buffer的大小是固定的，且无法进行调整

2、Buffer性能较好，可以直接对于计算机内存进行操作

3、Buffer表示的每个元素大小为1字节，如果超出了这个字节，开发者还设置了字节范围，则会显示乱码


