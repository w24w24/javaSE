# 一、目录

1、数组★★★★★★★

2、排序

3、查找

4、多维数组【重点讲解的是二维数组】

# 二、示例：为了解释为什么需要数组？

例：一个养鸡场有6只鸡，它们的体重分别是3kg、5kg、1kg、3.4kg、2kg、50kg。请问这6只鸡的总体重是多少？均体重是多少？请你编一个程序



# 三、数组：Array?【创建数组、初始化数组、排序、增强型for循环、复制数组、二位数组、Arrays】

1、介绍：数组可以存放多个同一数据类型的数据，数组也是一种数据类型，只不过不再是基本数据类型了，而是引用数据类型【后面会详细讲解】

2、养鸡场数组示例

```java
// 例：一个养鸡场有6只鸡，它们的体重分别是3kg、5kg、1kg、3.4kg、2kg、50kg
// 请问这6只鸡的总体重是多少？均体重是多少？请你编一个程序
public class Test {
    public static void main(String[] args) {
        // 6只鸡的体重
        double[] hens = {3,5,1,3.4,2,50};
        // 存储鸡重量的总和
        double totalSum = 0.0;
        for (int i = 0; i < hens.length; i++) {
            totalSum += hens[i];
        }
        System.out.println("鸡的总体重是：" + totalSum);
        // 鸡的平均体重
        System.out.println("鸡的平均体重是：" + (totalSum / hens.length));
    }
}
```

解析：

（1）数组是相同数据类型的有序集合

（2）数组是通过索引来访问的，数组的索引是从0开始的

（3）获取数组的长度可以使用 array.length 方法



# 四、数组的3种定义、使用方式？【动态初始化、静态初始化】

## 一、使用方式1：动态初始化

1、数组的定义：直接在定义数组时候就分配值或者是定义区间

```java
// 数据类型 数组名[] = new 数据类型[大小]
// 以下两种方式都可以使用：
double[] hens = new double[5];
double hens[] = new double[5];

// 说明：创建了一个数组，名字是hens，存放5个double
```

2、说明：这是定义数组的一种方法，为了让大家明白，我画数组内存图说明

```java
int[] a = new int[5];
```

![image-20231218230656244](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231218230656244.png)

定义了一个int型，名字为a的数组，里面存放了5个int，想要得到这个5个int的具体值，就要使用数组的下标来进行访问/引用/索引！！这里要和基本数据类型分开理解，如下：

```java
int a = 20;
```

基本数据类型a，在内存中只有一个格子，里面对应的值就是20，而这个值可以直接通过变量的名字来取到！！但是引用数据类型数组不一样，它需要使用下标记才可以索引和访问到数组里面具体的值

3、示例练习：循环输入5个人的成绩，然后在循环输出这个5个人的成绩

```java
// 需求：循环输入5个人的成绩，然后在循环输出这个5个人的成绩
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        double[] score = new double[5];
        Scanner myScanner = new Scanner(System.in);
        // 循环输入学生的成绩
        for (int i = 0; i < score.length; i++) {
            System.out.println("请输入第"+ (i+1) +"个学生的成绩");
            if(myScanner.hasNextDouble()) {
                score[i] = myScanner.nextDouble();
            }
        }
        // 循环输出学生的成绩
        for (int i = 0; i < score.length; i++) {
            System.out.println("第"+ (i+1) +"个学生的成绩是" + score[i]);
        }
    }
}
```



## 二、使用方式2：动态初始化

1、先声明数组：也就是说，只是给出数组的名字，但是不赋值

```java
// 数据类型[] 数组名字；
double[] a;
```

2、创建数组：在声明数组之后，再进行数组的赋值

```java
// 数组名字 = new 数据类型[大小]
a = new double[5];
```

3、示例题目：

```java
// 需求：循环输入5个人的成绩，然后在循环输出这个5个人的成绩
// 需求：循环输入5个人的成绩，然后在循环输出这个5个人的成绩
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        
        // 先声明
        double[] score;
        // 再创建数组
        score = new double[5];
        
        Scanner myScanner = new Scanner(System.in);
        // 循环输入学生的成绩
        for (int i = 0; i < score.length; i++) {
            System.out.println("请输入第"+ (i+1) +"个学生的成绩");
            if(myScanner.hasNextDouble()) {
                score[i] = myScanner.nextDouble();
            }
        }
        // 循环输出学生的成绩
        for (int i = 0; i < score.length; i++) {
            System.out.println("第"+ (i+1) +"个学生的成绩是" + score[i]);
        }
    }
}
```



## 三、使用方式3：静态初始化

1、初始化数组

```java
// 数据类型[] 数组名字 = {元素值，元素值，元素值.....}
// 这种方式是针对事先知道有多少个具元素的时候使用
int[] a = {1,2,3,4,5,6,7,8,9}
// 上面这种方式等价于下面这种方式
int[] a = new int[9];
int[0] = 1;
int[1] = 2;
int[2] = 3;
....
int[8] = 9;
```

#### 既然都是一样的，为什么不直接使用一种即可呢？

解析：因为在实际开发中，我们的需求可能会不一样，所以选择合适的方法



# 五、数组使用细节和注意事项？

1、数组是多个相同类型数据的组合【有序的集合】，实现对这些数据的统一管理

2、数组中的元素可以是任意数据的类型，包括了基本数据类型和引用数据类型，但是不可以混合使用，除非二者之间可以进行数据类型的转换

```java
// 正确的用法：数据类型相同的多个数据的组合
int[] number = {1,2,3,4,5}
double[] number2 = {1,2,3,4.1,100};
String[] str = {"北京","上海"};
// 错误的用法：不同数据类型的组合
int[] number1 = {1,2,3,'A',4,5}
```

3、数组创建后，如果没有赋值，那么它们的默认值如下：

```java
// 完整示例
public class Test {
    public static void main(String[] args) {
        int[] a = new int[3];
        System.out.println(a[1]);
    }
}

// 以下的以此类推
byte[] b = new byte[1]; // 输出：0
short[] s = new short[1]; // 输出：0
char[] c = new char[1]; // 输出：\u0000
int[] i = new int[1]; // 输出：0
long[] l = new long[1]; // 输出：0
float[] f = new float[1]; // 输出：0.0
double[] d = new double[1]; // 输出：0.0
boolean[] b1 = new boolean[1]; // 输出：false
String[] s1 = new String[1]; // 输出：null
```

4、使用数组的步骤：

```
1、声明数组并开辟空间
2、给数组各个元素赋值
3、使用数组
```

5、数组的下标是从0开始的

6、数组的下标必须在指定的范围内使用，否则报：下标越界异常，比如：

```java
// 有效的下标为0~4，因为数组的下标是从0开始的
int[] arr = new in[5];
```

7、数组属于引用数据类型，数组型数据是对象（Object）

# 六、数组练习题目？

1、创建一个char类型的26个元素的数组，分别放置'A~Z'，然后使用for循环访问并且打印出这26个字母【提示：char数据类型运算：'A' + 1 —> 'B'】

```java
public class Test {
    public static void main(String[] args) {
        // 动态初始化
        char[] letter = new char[26];
        char first = 'A';
        // 使用for循环生成26个字母
        for (int i = 0; i < 26; i++) {
            letter[i] = (char)(first + i);
        }
        // 使用循环遍历输出这26个字母
        for (int i = 0; i < 26; i++) {
            System.out.print(letter[i] + " ");
        }
    }
}
```

2、请求出一个数组int[ ]的最大值{4，-1，9，10，23}，并得到对应的下标

```java
public class Test {
    public static void main(String[] args) {
        int[] arrays = {4, -1, 9, 10, 23,71,3,15};
        // 设置一个值来将数组的第一个数作为最大值
        int max = arrays[0];
        // 接收数组的下标
        int index = 0;
        for (int i = 0; i < arrays.length; i++) {
            // 如果第一个数小于第二个，就把第二个数作为最大值
            if(max < arrays[i + 1]) {
                max = arrays[i + 1];
                index = i + 1;
            }
        }
        System.out.println("数组arrays中的最大值是：" + max);
        System.out.println("下标是：" + index);
    }
}
```



# 七、数组的赋值机制？【值传递和引用传递】★★★★★★★★

1、值传递/值拷贝：出现在基本数据类型赋值中，这个赋的值就是具体的数据，而且赋完值之后，不会相互影响

```java
int n1 = 10;
int n2 = n1;
n2 = 80;
System.out.println(n1); // 输出：10
System.out.println(n2); // 输出：80

// 因为n1和n2都是基本数据类型，所以二者之间是值传递/值拷贝，传递完毕之后，二者之间互不影响
```

2、引用传递/地址拷贝：出现在引用数据类型钟，这个赋的值就不是具体的值了，而是地址了，二者会相互影响

```java
int[] n1 = {1,2,3};
int[] n2 = n1;
n2[1] = 10;
System.out.println(n1); // 输出：10,2,3!!这里的n1按照逻辑来说是不会变化的呀？为什么会变呢？因为数组不是基本数据类型，所以在进行赋值的时候，不是值传递，而是引用传递【引用传递：就是赋值地址，而不是具体的值】
System.out.println(n2); // 输出：10,2,3
```

3、这里解释为什么值传递/值拷贝和引用传递/地址拷贝修改后，会不一样的【涉及到计算机内存中的栈和堆】

![image-20231219215737745](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231219215737745.png)

解析：

（1）值传递/值拷贝：int n1 = 10是直接在内存中开辟一个空间用来存放值；当把n1赋值给到n2时，是把n1的值赋值给n2；当去修改n2的时，是不会影响n1的

（2）引用传递/地址拷贝：int[ ] arr1 = {1,2,3}是先在堆中开辟一个空间，用来存放arr1的地址的，arr1的值不是放在栈中的，而是放在堆中的；栈中的arr1地址指向堆中的一个空间，堆中的这个空间里面有三个格子，是用来存放arr1的3个元素值/数组元素的！当把arr1赋值给arr2的时候，并不是直接将arr1在堆中的具体数组元素给到arr2的，而是将arr1在栈中的地址复制一份，给到arr2，以致于arr2和arr1的地址都是同一个，都指向堆中的空间。当修改arr2[1]的时候，就直接修改了堆中的元素值，因为arr1也是指向这个元素的，所以arr2的变化会影响到arr1的变化



# 八、数组的拷贝？【new关键字的使用】

解析：在七章节中我们讲到了，arr2的修改会影响arr1的元素值！如果我只想拷贝元素值，当我去修改arr2的时候，不会影响到arr1，这应该怎么做呢？

#### 【这个时候就使用到了数组拷贝，即只拷贝数组的元素值，和arr1的空间和地址是相互独立的，即使修改arr2，也不会影响arr1】

1、new关键字的使用，因为使用new，就是在计算机内存中新开辟了一块空间和地址，将这个空间和地址赋值给到arr2！！这个空间和地址是独立的，不会影响到啊arr1![image-20231219222017118](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231219222017118.png)



```java
public class Test {
    public static void main(String[] args) {
        int[] arr1 = {1,2,3};
        // 使用new关键字在堆中开辟一个新的空间，使arr1和arr2数据空间分离
        int[] arr2 = new int[arr1.length];
        // 然后使用循环将arr1中的元素值赋给arr2即可
        for (int i = 0; i < arr1.length; i++) {
            arr2[i] = arr1[i];
        }
        System.out.println(arr2[2]); // 输出：3
        // 当我们修改arr2中的元素值的时候，arr1是不会变化的
        arr2[2] = 10;
        System.out.println(arr1[2]); // 输出：10
        System.out.println(arr2[2]); // 输出：3
    }
}
```

2、需求：把数组的元素内容翻转，如下：

arr{ 11，22，33， 44, 55，66} —>  arr{66，55，44，33，22，11}

（1）思路1：利用第三个临时变量来接收，然后赋值即可

```java
// 把数组元素内容翻转
public class Test {
    public static void main(String[] args) {
        int[] arr = {11,22,33,44,55,66,77};
        // 规律：把arr[0] 和 arr[5] 交换：[66,22,33,44,55,11]
        // 规律：把arr[1] 和 arr[4] 交换：[66,55,33,44,22,11]
        // 规律：把arr[2] 和 arr[3] 交换：[66,55,44,33,22,11]
        // 一共要交换3次: 3 = arr.length / 2
        // 每次交换时，对应的下标是 arr[i] 和 arr[arr.length - 1 - i]
        int len = arr.length;
        int temp = 0;
        for (int i = 0; i < len / 2; i++) {
            // 首先将arr.length-1-i的元素值赋值temp
            temp = arr[len - 1 - i];
            // 翻转：再将arr[i]赋值给arr[arr.length-1-i]
            arr[len-1-i] = arr[i];
            // 再temp赋给arr[i]
            arr[i] = temp;
        }
        // 输出：翻转后的数组
        for (int i = 0; i < len; i++) {
            System.out.print("翻转后的数组是：" + arr[i] + " ");
        }
    }
}
```



# 九、数组扩容？

需求：实现动态的给数组添加元素效果，实现对数组扩容

（1）原始数组使用静态分配 int[ ] arr = {1,2,3}

（2）增加的元素4，直接放在数组的最后 arr  = {1,2,3,4}

（3）增加一个方法，询问用户是否还进行添加 y/n？如果继续添加，则继续添加，如果不继续添加，则直接退出

先进行元素的添加：

```java
// 数组扩容
public class Test {
    public static void main(String[] args) {
        // 原始数组
        int[] arr = {1,2,3,4,5,6,7,8,9};
        // 新建一个数组
        int[] newArr = new int[arr.length+1];
        // 使用for循环，将arr中的元素值给到newArr中
        for (int i = 0; i < arr.length; i++) {
            newArr[i] = arr[i];
        }
        newArr[newArr.length-1] = 10;
        // 现在再将arr的地址指向newArr
        arr = newArr;
        // 遍历数组
        for (int i = 0; i < newArr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

再进行方法的添加：

```java
// 数组扩容
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        // 实例化Scanner
        Scanner myScanner = new Scanner(System.in);
        // 原始数组
        int[] arr = {1,2,3,4,5,6,7,8,9};
        // 新建一个数组
        int[] newArr = new int[arr.length+1];
        // 使用for循环，将arr中的元素值给到newArr中
        do {
            for (int i = 0; i < arr.length; i++) {
                newArr[i] = arr[i];
            }
            // 提示用户输入
            System.out.println("请输入想要添加的数字：");
            // 用户输入的元素值进行添加
            int userInput = myScanner.nextInt();
            newArr[newArr.length-1] = userInput;
            // 现在再将arr的地址指向newArr
            arr = newArr;
            // 遍历数组
            for (int i = 0; i < newArr.length; i++) {
                System.out.print(arr[i] + " ");
            }
            // 询问用户是否继续添加
            System.out.println("\n是否继续进行添加：y/n");
            char key = myScanner.next().charAt(0);
            if(key == 'n') {
                break;
            }
        }while(true);
        System.out.println("您已成功退出...");
    }
}
```

#### 提示：这种数组扩容的效率还是比较低的，因为它无法动态增长，后面我们还会学习链表，链表扩容就非常的方便

## 一、数组扩容是非常缓慢的，为什么这么说？

1、数组扩容每次都需要去开辟一个新的数组

```java
// 原始数组
int[] oldArr = {1,2,3,4,5};
// 新开辟的数组
int[] newArr = new int[oldArr.length + 1];
```

2、开辟完成之后，还要将oldArr的数组元素拷贝给到newArr数组

```java
// 原始数组
int[] oldArr = {1,2,3,4,5};

// 新开辟的数组
int[] newArr = new int[oldArr.length + 1];

// 使用for循环将oldArr的数组元素拷贝到newArr
for (int i = 0; i < arr.length; i++) {
    newArr[i] = arr[i];
}
```

3、假如数组的元素量非常的大，数据特别多，这种扩容的方式就不适用于了



# 十、数组缩减？

需求：有一个数组{1，2，3，4，5，6，7，8，9，10，25}，可以将该数组进行缩减，提示用户是否进行缩减，每次缩减的是最后一个元素，当缩减了只是剩下最后一个元素的时候，提示用户，不能再进行缩减了

示例：自己写的，可能会有错误的地方，但是满足题目的需求是没有问题的

```java
// 数组删减
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,8,9,10,11,25};
        Scanner myScanner = new Scanner(System.in);
        do{
            System.out.println("是否删除最后一个元素：y/n");
            char userInput = myScanner.next().charAt(0);
            if(userInput == 'y') {
                if(arr.length == 1) {
                    System.out.println("已经是最后一个元素了，无法删除！");
                    break;
                }
                int[] newArr = new int[arr.length-1];
                    for (int i = 0; i < newArr.length; i++) {
                        newArr[i] = arr[i];
                    }
                arr = newArr;

                // 测试输出元素的个数
                for (int i = 0; i < arr.length; i++) {
                    System.out.print(arr[i] + " ");
                }
                System.out.println();
            }else {
                break;
            }
        }while(true);
        System.out.println("您已经成功退出...");
    }
}
```



# 十一、排序？

介绍：排序是将多个数据，依照指定的顺序进行排列的过程【这个顺序可以是：从小到大、从到到小】

排序的分类：

1、内部排序：指将需要处理的所有数据都加载到内部存储器中进行排序【如：交换式排序法、选择式排序法、插入时排序法】

2、外部排序：数据量过大，无法全部加载到内存中，需要借助外部存储进行排序【如：合并排序法、直接合并排序法】



# 十二、冒泡排序？

需求：我们将5个无序：24、69、80、57、13，使用冒泡排序法将其排成一个从小到大的有序数列

1、分析冒泡排序

```
数组：[24,69,80,57,13]

第一轮排序：目标是把整个数组中最大的数放在最后
第1次比较：[24,69,80,57,13]
第2次比较：[24,69,80,57,13]
第3次比较：[24,69,57,80,13]
第4次比较：[24,69,57,13,*80*]

第二轮排序：目标是把整个数组中第二大的数放在倒数第二位
第1次比较：[24,69,57,13,*80*]
第2次比较：[24,57,69,13,*80*]
第3次比较：[24,57,13,*69*,*80*]

第三轮排序：目标是把整个数组中第三大的数放在倒数第三位
第1次比较：[24,57,13,*69*,*80*]
第2次比较：[24,13,*57*,*69*,*80*]

第四轮排序：目标是把整个数组中第四大的数放在倒数第四位
第1次比较：[*13*,*24*,*57*,*69*,*80*]
```

2、冒泡排序特点

```
1、我们一共有5个元素
2、一共进行了4轮排序，可以看成是外层循环
3、每一轮排序可以确定一个数的位置。比如：第一轮排序确定一个最大的数，第二轮排序确定第二大的数，以此类推
4、当进行比较的时候，如果前面的数大于后面的数，就进行交换
5、每轮排序结束后，下一次排序的次数都在减少，比如示例：4——>3——>2——>1
```

3、代码示例：先死后活

```java
// 遵循先死后活原则
public class Test {
    public static void main(String[] args) {
        // 需要进行处理的数组
        int[] arr = {24,69,80,57,13};
        // 临时变量来进行转换
        int temp = 0;

        /*
        第一轮排序：目标是把整个数组中最大的数放在最后
        第1次比较：[24,69,80,57,13]
        第2次比较：[24,69,80,57,13]
        第3次比较：[24,69,57,80,13]
        第4次比较：[24,69,57,13,*80*]
         */
        // 使用for循环来进行数值之间的交换
        for (int j = 0; j < arr.length-1; j++) { // 4次比较
            // 如果前面的数大于后面的数，就进行交换
            // 直观理解：[400,10]
            if(arr[j] > arr[j+1]) {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println("=====第一轮=====");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }

        /*
        第二轮排序：目标是把整个数组中第二大的数放在倒数第二位
        第1次比较：[24,69,57,13,*80*]
        第2次比较：[24,57,69,13,*80*]
        第3次比较：[24,57,13,*69*,*80*]
         */
        for (int j = 0; j < arr.length-2; j++) { // 3次比较
            // 如果前面的数大于后面的数，就进行交换
            // 直观理解：[400,10]
            if(arr[j] > arr[j+1]) {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println();
        System.out.println("=====第二轮=====");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }

        /*
        第三轮排序：目标是把整个数组中第三大的数放在倒数第三位
        第1次比较：[24,57,13,*69*,*80*]
        第2次比较：[24,13,*57*,*69*,*80*]
         */
        for (int j = 0; j < arr.length-3; j++) { // 2次比较
            // 如果前面的数大于后面的数，就进行交换
            // 直观理解：[400,10]
            if(arr[j] > arr[j+1]) {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println();
        System.out.println("=====第三轮=====");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }

        /*
        第四轮排序：目标是把整个数组中第四大的数放在倒数第四位
        第1次比较：[*13*,*24*,*57*,*69*,*80*]
         */
        for (int j = 0; j < arr.length-4; j++) { // 1次比较
            // 如果前面的数大于后面的数，就进行交换
            // 直观理解：[400,10]
            if(arr[j] > arr[j+1]) {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
        System.out.println();
        System.out.println("=====第四轮=====");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

4、代码示例：化繁为简

```java
public class Test {
    public static void main(String[] args) {
        // 需要进行处理的数组
        int[] arr = {24,69,80,57,13};
        // 临时变量来进行转换
        int temp = 0;
        // 化繁为简，使用for循环包裹
        for (int i = 0; i < arr.length-1; i++) { // 外层循环是4次
            for (int j = 0; j < arr.length-1- i; j++) { // 4次比较——3——2——1
                // 如果前面的数大于后面的数，就进行交换
                // 直观理解：[400,10]
                if(arr[j] > arr[j + 1]) {
                    temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
            System.out.println();
            System.out.println("=====第"+ (i+1) +"轮=====");
            for (int j = 0; j < arr.length; j++) {
                System.out.print(arr[j] + " ");
            }
        }
    }
}
```



# 十三、查找？

解析：在java中，我们常用的查找有两种

1、顺序查找

2、二分查找

```
什么是二分查找？
解析：
1、就是在一个有序的数列中【数组就是数列】中，从这个数列的中间来进行查找
2、如果中间这个数不是，并且系统自动将这个数和需要查找的元素进行对比
3、假如需要查找的元素大于这个中间数，那么就往右边开始查找
4、假如需要查找的元素小于这个中间数，那么就往左边开始查找
```

#### 顺序查找需求：有一个数列：{"白眉鹰王","金毛狮王","紫衫龙王","青翼蝠王"}，从键盘接收用户输入的值，判断数组序列中是否含有这个值，如果有，就提示用户有，并且给出下标，如果没有，就告诉用户没有

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        // 定义一个开关
        int index = -1;
        String[] nameGame = {"白眉鹰王","金毛狮王","紫衫龙王","青翼蝠王"};
        System.out.println("请你输入想要查找的名字：");
        String userInputName = myScanner.next();
        for (int i = 0; i < nameGame.length; i++) {
            if(userInputName.equals(nameGame[i])) {
                System.out.println("已经为你查找到" + nameGame[i]);
                System.out.println("下标是" + i);
                index = i;
                break;
            }
        }
        if(index == -1) {
            System.out.println("对不起，无法查询到" + userInputName);
        }
    }
}
```

#### 注意：这里面涉及到一个很重要的编程思想或者是编程技巧，那就是使用一个标识符来判断这个程序是否执行成功了，如上述例题中的index，如果成功了，就将index更改为i，即数组的下标，如果不成功，则不进行更改



# 十四、二维数组入门？

二维数组的应用场景：比如我们开发一个五子棋游戏，棋盘就是需要二维数组来进行表示【想象一下棋盘】

1、二维数组示例：请你使用二维数组来输出如下的图形

0 0 0 0 0 0

0 0 1 0 0 0

0 2 0 3 0 0 

 0 0 0 0 0 0

```java
public class Test {
    public static void main(String[] args) {
        // 原始数组
        int[][] arr = {
                {0,0,0,0,0,0},
                {0,0,1,0,0,0},
                {0,2,0,3,0,0},
                {0,0,0,0,0,0}};
        // 遍历数组
        for (int i = 0; i < arr.length; i++) { // 第一层是一维数组
            for (int j = 0; j < arr[i].length; j++) { // 二维数组里的元素值又是一维数组
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

#### 注意：二维数组中的元素值是一个一维数组



# 十五、二维数组的使用？

## 一、使用方式1：动态初始化【同时声明和初始化】

```
语法：类型[][] 数组名 = new 类型[大小][大小]
示例：int[][] arr = new int[2][3];
```

1、二维数组在内存中的存在方式和表示方法

![image-20231225224955706](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231225224955706.png)

解析：

```
1、二维数组也是引用数据类型，所以也是遵循引用的是地址的规则
2、在栈中，存储变量名arr存放的是地址，这个地址指向的是堆中的数据
3、因为是二维数组，数组中的元素值又是一维数组，所以在堆中数据的依旧不是具体的值，而是地址，这个地址又指向堆中的另一个地址，在这个地址中，存放的才是具体的值
```

示例：输出`int[][] arr = new int[ 2 ][ 3 ]`的值，并且将`arr[1][1]`赋值为8

```java
public class Test {
    public static void main(String[] args) {
        // twoDimensionalArrays
        int[][] arr = new int[2][3];
        arr[1][1] = 8;
        // 遍历数组
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println(); // 换行
        }
    }
}
```

## 二、使用方式2：动态初始化【声明和初始化分开】

解析：先声明数组，再初始化数组

```java
// 声明数组
int[][] arr;
// 初始化数组
arr = new int[][];
```

#### 既然都是数组的声明和初始化，为什么会有数组的声明、初始化连写和分开这2种形式呢？

解析：在实际开发中，我们有时候并不想直接去初始化数组，而是等待用户有操作的时候才去初始化数组，这个时候就会将数组的声明和初始化分开

## 三、使用方式3：动态初始化—列数不确定

解析：列数不确定的意思是“二维数组中的一维数组的元素值是不确定的”

需求：使用code完成下列需求

|  i/j  | j = 0 | j = 1 | j = 2 |
| :---: | ----- | ----- | ----- |
| i = 0 | 1     |       |       |
| i = 1 | 2     | 2     |       |
| i = 2 | 3     | 3     | 3     |

解析：创建二维数组，二维数组中的一维数组的元素值会变化

```java
public class Test {
    public static void main(String[] args) {
        // 创建一个二维数组
        int[][] arr = new int[3][];
        /*
        1、上述创建的二维数组只有3个元素，但是这个3个元素又是一维数组
        2、而且这3个元素还没有开辟空间，是null
         */
        // 给二维数组中的元素值（即一维数组）开辟空间
        for (int i = 0; i < arr.length; i++) {
            arr[i] = new int[i+1];
            // 开辟完空间之后还需要给一维数组赋值
            for (int j = 0; j < arr[i].length; j++) {
                arr[i][j] = i + 1;
            }
        }
        // 遍历数组
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

## 四、使用方式4：静态初始化

1、语法格式：

```java
数据类型 数组名[][] = {{值1，值2，值3....}，{值1，值2，值3....}，{值1，值2，值3....}，{}....}；
```

2、访问：直接使用数组的下标进行访问即可

3、错误示例：类型不匹配，因为二维数组中有元素不是一维数组

```java
int[][] arr = {{1,2,3},{4,5,6},100}; // 报错，因为100不是一维数组，而是基本数据类型
```

4、正确示例：类型匹配，二维数组中的元素值都是一维数组

```java
int[][] arr = {{1,2,3},{4,5,6},100}; // 正确，所有元素值都是一维数组
```

#### 注意：二维数组中的所有元素值都必须是一维数组，不允许是其它的形式，否则将出现错误



# 十六、练习题目？

1、需求：需求：遍历该二维数组{{4,6},{1,4,5,7},{-2}}，并且得到这个二维数组的和

```java
public class Test {
    public static void main(String[] args) {
        // 二维数组的遍历
        int[][] arr = {{4,6},{1,4,5,7},{-2}};
        // 需求：遍历该二维数组，并且得到这个二维数组的和
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                sum += arr[i][j];
            }
        }
        System.out.println("数组arr的和是：" + sum);
    } 
}
```

# 十七、杨辉三角？

规律：

1、第一行有一个元素，第n行有n个元素

2、每一行的第一个元素和最后一个元素都是1、

3、从第三行开始，对于非第一个元素和最后一个元素的元素值，有如下规律：不是第一个元素和最后一个元素，这个元素等于前一列位置的元素加前一位元素

```
arr[i][j] = arr[i-1][j] + arr[i-1][j-1];

// 示例:不是第一个元素和最后一个元素，这个元素等于前一列位置的元素加前一位元素

1	
1	1	
1	2	1	
1	3	3	1	
1	4	6	4	1	
1	5	10	10	5	1	
1	6	15	20	15	6	1	
1	7	21	35	35	21	7	1	
1	8	28	56	70	56	28	8	1	
1	9	36	84	126	126	84	36	9	1
```

代码示例：

```java
public class Test {
    public static void main(String[] args) {
        // 杨辉三角
        int[][] yangHui = new int[10][];
        for (int i = 0; i < yangHui.length; i++) {
            // 给一维数组开空间
            yangHui[i] = new int[i+1];
            // 给一维数组赋值
            for (int j = 0; j < yangHui[i].length; j++) {
                // 每行的第一个元素和最后一个元素都是1
                if(j == 0 || j == yangHui[i].length - 1) {
                    yangHui[i][j] = 1;
                }else { // 否则就是中间的元素
                    // 中间的元素等于上一列的同位置 元素加前一个元素
                    yangHui[i][j] = yangHui[i-1][j] + yangHui[i-1][j-1];
                }
            }
        }
        // 输出
        for (int i = 0; i < yangHui.length; i++) {
            for (int j = 0; j < yangHui[i].length; j++) { // 遍历输出这一行之后
                System.out.print(yangHui[i][j] + "\t");
            }
            System.out.println(); // 换行
        }
    }
}
```



# 十八、二维数组的使用细节和注意事项？

1、一维数组的声明方式

```java
int[] oneDimensional = new int[];
// 或者
int oneDimensional[] = new int[];
```

2、二维数组的声明方式

```java
int[][] twoDimensional = new int[][];
// 或者
int[] twoDimensional[] = new int[][];
// 或者
int twoDimensional[][] = new int[][];
```

3、二维数组实际上是由多个一维数组组成的，它的各个一维数组的长度可以相同，也可以不相同。比如：map [ ] [ ] = {{1,2},{3,4,5},{6,7,8,9}}，其中map[0]是含有2个元素的一维数组，map[1]是含有3个元素的一维数组，我们将这种称之为列数不等的二维数组

```java
// 列数不等的二维数组
int map[][] = {{1,2},{3,4,5},{6,7,8,9}};
```



# 十九、二维数组练习？

示例：声明int[]x, y[];，下面选项可以通过编译的是

```java
int[]x,y[];
// 解析上面的int[]x,y[]的含义
int[]x; // 一维数组
int[]y[]; // 二维数组
```

示例：String [] str = new String{"a","b","c"}的写法是否是正确的?

```java
// 这里考察的是new的特征
new是用来定义数组的长度的，如果有具体的值了，就不能使用new了！！
简单理解：new String{"a","b","c"}和前面的数组类型不匹配
// 如果依旧想要使用这种方法，就需要像下面这样写
String [] str = new String[]{"a","b","c"};
```

示例：String [] str = new String[3]{"a","b","c"}的写法是否是正确的?

```java
注意：在使用上述方式进行静态初始化数组的时候，不需要给具体的数值3，因为这个数值是编译器自动进行编译的，不需要手动给上去！假如明确给出之后，会直接报错！
```

1、给这个数组{10,12,45,90}增加一个元素23，使得其依旧呈升序排列

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = {10,12,45,90};
        int insertNum = -1;
        int index = -1;
        // 定位
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] >= insertNum) {
                index = i;
                break;
            }
        }
        // 扩容
        int[] newArr = new int[arr.length+1];
        for (int i = 0,j = 0; i < newArr.length; i++) {
            if(index != i) {
                newArr[i] = arr[j];
                j++;
            }else {
                newArr[i] = insertNum;
            }
        }
        arr = newArr;
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

