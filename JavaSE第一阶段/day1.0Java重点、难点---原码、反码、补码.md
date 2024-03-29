# 一、原码、反码、补码？【重点、难点】

介绍：在计算机科学中，原码、反码、补码是用来表示整数的不同方式。通常用于解决整数的表示、运算和溢出等问题，`在java中，所有的数据都是使用补码来表示的`



## 特点与公式：

1、二进制的最高位是符号位：0表示的是正数，1表示的负数（0旋转90度还是0、1旋转90度就是—）

2、正数的原码、反码、补码都是一样的（三码合一）

3、负数的反码 ：除了符号位不变，原码的其它位全部取反（1变为0、0变为1）

4、负数的补码：等于它本身的反码 + 1【注意：这里的+1，是在反码的最低位上+1即可，不需要从右到左每一位都+1】

5、负数的反码：等于它本身的补码-1【注意：这里的-1，是在补码的最低位上-1即可，不需要从右到左每一位都-1】

6、0的反码、补码都是0

7、java中没有无符号数，换言之，java中的数都是有符号的

#### 8、在计算机运算【无论是加减乘除、按位与、按位或等】的时候，都是以补码的方式来运算的

9、当我们看运算结果的时候，要看它的原码

10、给人看的是原码、计算机使用的是补码

# 三、具体探索这三个码呢？【重点、难点】

大家都知道，数据在计算机中是以二进制的形式存储的，这3个码就是用来表示数据的。比如：

```java
byte a = 6; // 正数6
byte b = -6; // 负数6
```



#### 解析：原码

1、正数：对于正数6来说，原码就是0000 0110【因为1字节是8位，所以需要有8个数字；二进制是使用0、1来表示的，所以组合起来就是0000 0110】！反码和补码和原码一致

```java
byte a = 6;
// 原码、反码、补码一致，简称“三码合一”
0000 0110
```

2、负数：对于负数6来说，原码就是1000 0110【因为1字节是8位，所以需要有8个数字；二进制是使用0、1来表示的；最高位（最左边）表示的是符号，0表示正数，1表示负数；所以组合起来就是1000 0110】

```java
byte a = 6;
// 负数的原码就是最高位的符号位置为1：
1000 0110
```

3、不管是byte、int、short还是其它的数字，最高位都是用来表示符号的

```java
负数使用1来表示
正数使用0来表示
```



#### 解析：反码

1、正数的反码：和原码、补码一致，简称“三码合一”

```java
byte a = 6;
// a 的原码、反码、补码都是一致的，如下：
0000 0110
```



2、负数的反码：就是符号位不变，原码的其它位全部取反【是1则变为0，是0则变为1】

```java
byte a = -6;
// a 的原码：
1000 0110
// a 的反码：
1111 1001
```

3、负数的补码：就是在反码的基础上 +1 就行【这里的+1是指在最低位上+1即可，并不是从右到左每一位都要+1】，由于是二进制，所以需要逢2进1

```java
byte a = -6;
// a 的原码：
1000 0110
// a 的反码：
1111 1001
// a 的补码
1111 1010
```

#### 在计算机的加减运算，指的是补码之间的运算！！！【计算机中只有加法，没有减法，减法是通过补码的形式表示的】，负数在计算机中就是以补码的方法参与运算的，简而言之，负数就相当于是补码



## 看到这，请再回到 day0.9 第二节接着复习

