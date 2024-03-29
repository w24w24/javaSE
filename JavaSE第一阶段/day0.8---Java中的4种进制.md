# 一、Java中的4种进制？

介绍：

1、二进制：使用0、1来表示，满2进1；以ob、oB开头，不区分大小写【b、B的意思是Binary，二进制的意思】

2、十进制：0-9，满10进1

3、八进制：0-7，满8进1，以数字0开头表示

4、十六进制：0-9及A/a-F/f表示10-15，满16进1，以0x或0X表示，此处的A/a、F/f也是不区分大小写的

```java
// 二进制
int n1 = 0b1010; // 输出：10
// 十进制
int n2 = 1010; // 输出：1010
// 八进制
int n3 = 01010; // 输出：
// 十六进制
int n4 = 0x10101; // 输出：
```



图表示意：

| 阿拉伯数字 | 十进制 | 十六进制 | 八进制 | 二进制 |
| ---------- | :----: | :------: | :----: | :----: |
| 0          |   0    |    0     |   0    |   0    |
| 1          |   1    |    1     |   1    |   1    |
| 2          |   2    |    2     |   2    |   10   |
| 3          |   3    |    3     |   3    |   11   |
| 4          |   4    |    4     |   4    |  100   |
| 5          |   5    |    5     |   5    |  101   |
| 6          |   6    |    6     |   6    |  110   |
| 7          |   7    |    7     |   7    |  111   |
| 8          |   8    |    8     |   10   |  1000  |
| 9          |   9    |    9     |   11   |  1001  |
| 10         |   10   |   A/a    |   12   |  1010  |
| 11         |   11   |   B/b    |   13   |  1011  |
| 12         |   12   |   C/c    |   14   |  1100  |
| 13         |   13   |   D/d    |   15   |  1101  |
| 14         |   14   |   E/e    |   16   |  1110  |
| 15         |   15   |   F/f    |   17   |  1111  |
| 16         |   16   |    10    |   20   | 10000  |
| 17         |   17   |    11    |   21   | 10001  |

解析：每一个进制的表示方法都代表前面的阿拉伯数字

下面这几个章节我们将学习进制之间的转换



# 二、进制的转换【基本功】

###### 第一组：

1、二进制转换十进制

2、八进制转换十进制

3、十六进制转换十进制

###### 第二组：

1、十进制转换二进制

2、十进制转八进制

3、十进制转换十六进制

###### 第三组：

1、二进制转八进制

2、二进制转十六进制

###### 第四组：

1、八进制转二进制

2、十六进制转二进制

#### 是不是看着很多？其实不需要这么复杂，只需要这样这样理解即可

#### 1、其它进制转为十进制【三——————五】

#### 2、十进制转换为其它进制【六—————八】

#### 3、二进制转换为其它进制【九——————十】

#### 4、其它进制转换为二进制【十一—————十二】



# 三、其它进制（二）转十进制？ 

二进制转十进制规则：从最低（右边）开始，将每个位上的数提取出来，乘以2的位数减去1次方，然后求和，就可以得到二进制转换十进制的数

案例：请将0b1011转换为十进制的数

```java
// 二进制转十进制公式拆分：
0b1011 = 1 * 2的(1-1)次方 + 1 * 2的(2-1)次方 + 0 * 2的(3-1)次方 + 1 * 2的(4-1)次方
// 计算转换出来的和
 1 + 2 + 0 + 8 = 11
// 所以最后的ob1011的十进制数是 11
```



# 四、其它进制（八）转十进制？

八进制转十进制规则：从最低位（右边）开始，将每个位上的数提取出来，乘以8的（位数-1）次方，然后求和

案例：请将0234转换为十进制的数

```java
// 八进制转十进制公式拆分:
0234 = 4 * 8^0 + 3 * 8^1 + 2 * 8^2
// 计算转换出来的和
4 + 24 + 128 = 156
// 所以最后的0234的十进制数是 156
```

# 五、其它进制（十六）转十进制？

十六进制转十进制规则：从最低位（左边）开始，将每个位上的数提取出来，乘以16的（位数-1）次方，然后求和

案例：请将0x23A转换为十进制的数【这里的A配合上表，表示的是数字10】

```java
// 十六进制转十进制公式拆分:
0x23A = 10 * 16^0 + 3 * 16^1 + 2 * 16^2
// 计算转换出来的和
10 + 48 + 512 = 570
// 所以最后的0x23A的十进制数是 570
```

练习题：

1、请将0b110001100转换为10进制【396】

```java

```

2、02456转换为十进制【1326】

```java

```

3、0xA45转换为10进制【2629】

```java
```



# 六、十进制转换其它进制（二）？

十进制转二进制规则：将该数不断除以2，直到商为0为止，然后将每步骤得到的余数倒过来，就是对应的二进制

案例：请将34转为二进制【oB100010】

![image-20231120194849396](https://github.com/w24w24/javaSE/blob/master/Images/%E8%BF%9B%E5%88%B6%E8%BD%AC%E6%8D%A2.png)

解析：注意，只写了0B100010是不对的，因为在电脑中，一个字节是8位，但是0B100010只有6位，0B是不算的，所以会自动添加两位，也就是两个00在高位作为补充，最终的答案是 0B00100010



# 七、十进制转换其它进制（八）？

十进制转八进制规则：将该数不断除以8，直到商为0为止，然后将每步骤得到的余数倒过来，就是对应的八进制

案例：请将131转为八进制【0203】



# 八、十进制转换其它进制（十六）？

十进制转十六进制规则：将该数不断除以16，直到商为0为止，然后将每步骤得到的余数倒过来，就是对应的八进制

案例：请将237转为八进制【0xED】



练习：

1、123转换为二进制？【0B01111011】

```java
```

2、678转换为八进制？【01246】

```java
```

3、8912转为十六进制？【0x22D0】

```java
```



# 九、二进制转其它进制（八）？

二进制转八进制规则：从低位开始，将二进制数每三位【这是因为2的三次方刚好是8】一组，转成对应的八进制数即可

案例：请将0b11010101转成八进制

十进制：213

八进制：0325

```java
public class BinaryChange {
    public static void main(String[] args) {
        // 进制转换
        int binaryChange = 0b11010101;
        /*
        1、从右往左，每三位一组，转换为对应的八进制即可
         */
        System.out.println(binaryChange); // 注意：这里输出的是十进制213，213的八进制就是0325

    }
}
```

# 十、二进制转为其它进制（十六进制）？

二进制转十六进制规则：从低位（右边往左边）开始，每四位一组【这是因为2的4次方刚好是16】，转换为对应的十六进制即可

案例：请将0b11010101转换为十六进制

```java
public class BinaryChange {
    public static void main(String[] args) {
        // 进制转换
        int binaryChange = 0b11010101;
        /*
        1、从右往左，每四位一组，转换为对应的十六进制即可
         */
        System.out.println(binaryChange); // 注意：这里输出的是二进制213，213的十六进制就是0xD5
    }
}
```

练习：

1、0b11100101转换成八进制【0345】

```java
```

2、0b1110010110转换成十六进制【Ox396】

```java
```



# 十一、八进制转二进制？

八进制转换二进制规则：将八进制的每1位，转成对应的`一个3位`【注意：必须是3位，因为2的3次方才等于8；要是转换出来没有3位，在高位补0来填充即可】的二进制数即可

案例：请将0237转换为二进制

```java
拆分：0237
7 = 111
3 = 011（虽然3=11，但是不满足对应的3位，在高位补0，所以是011）
2 = 010（同理在高位补0，就是010）
```



# 十二、十六进制转换二进制？

十六进制转二进制的规则：将十六进制数每一位，转成`对应的4位`的一个二进制数即可

案例：请将0x23B转成二进制【0010 0011 1011】

```java
拆分：0x23B
B = 11(10#)==>1011(2#)
3 = 0011（虽然3=11，但是不满足对应的4位，在高位补0，所以是0011）
2 = 0010（同理在高位补0，就是0010）
```



