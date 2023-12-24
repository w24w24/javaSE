# 一、程序控制结构？

解析：



目录：

1、顺序控制

2、分支控制（if、else、switch）

3、循环控制（for、while、dowhile，多重循环【重点】）

4、break

5、continue

6、return



# 二、程序流程控制介绍？

定义：在程序中，程序运行的流程控制决定了程序如何运行，是我们必须要掌握的，主要有3大流程控制语句

1、顺序控制

2、分支控制

3、循环控制【难度最大】



# 三、顺序控制？

介绍：程序从上到下，逐行执行，中间没有任何的判断和跳转

示例及其注意事项：

1、java中定义的变量时采用合法的向前引用，如下：

```java
public class Test {
    public static void main(String[] args) {
        int num1 = 12;
        int num2 = num1 + 1;
        System.out.println(num2); // 输出：13
    }
}
```

2、不合法的向前引用，如下：

```java
public class Test {
    public static void main(String[] args) {
        int num2 = num1 + 1;
        int num1 = 12;
        System.out.println(num2); // 输出：报错
    }
}
```



# 四、分支控制if-else？

介绍：让程序有选择的执行，分支控制的3种

## 1、单分支

基本语法：

```java
if(条件表达式) {
     执行代码块;（可以有多条语句）
}
```

说明：当条件表达式为true时，就会执行{}，如果为false，就不执行{}。

特别说明：如果{}只有一条语句的时，则可以省略{}，直接写语句，但是建议使用{}

示例需求：编写一个程序，可以输入人的年龄，如果该同志的年龄大于18岁，则输出"你的年龄大于18岁，请对自己的年龄负责，送入监狱"

```java
// 编写一个程序，可以输入人的年龄
// 如果该同志的年龄大于18岁，输出：你的年龄大于18岁，请对自己的年龄负责，送入监狱
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入您的年龄：");
        int userAge = myScanner.nextInt();
        if(userAge > 18) {
            System.out.println("请对自己的年龄负责，送入监狱");
        }
        System.out.println("程序继续执行...");
    }
}
```



## 2、双分支【只执行一个代码块】

基本语法：

```java
if(条件表达式) {
     执行代码块1;
} esle {
    执行代码块2;
}
```

说明：当条件表达式成立时，就会执行代码块1，如果为不成立，则执行代码块2。

特别说明：如果{}只有一条语句的时，则可以省略{}，直接写语句，但是建议使用{}

示例需求：编写一个程序，可以输入人的年龄，如果该同志的年龄大于18岁，则输出"你的年龄大于18岁，请对自己的年龄负责，送入监狱"；如果该同志的年龄小于18岁，则输出"你的年龄小于18岁，这次就放过你了"

```java
// 编写一个程序，可以输入人的年龄
// 如果该同志的年龄大于18岁，输出：你的年龄大于18岁，请对自己的年龄负责，送入监狱
// 如果该同志的年龄小于18岁，则输出"你的年龄小于18岁，这次就放过你了"
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入您的年龄：");
        int userAge = myScanner.nextInt();
        if(userAge > 18) {
            System.out.println("请对自己的年龄负责，送入监狱");
        } else {
            System.out.println("你的年龄小于18岁，这次就放过你了");
        }
        System.out.println("程序继续执行...");
    }
}
```



## 3、多分支

基本语法：

```java
if(条件表达式) {
     执行代码块1;
} esle if {
    执行代码块2;
}
.... // else if可以有多个
else {
    默认执行代码块;
}
```

说明：当条件表达式成立时，就会执行代码块1，如果为不成立，则执行代码块2，依此类推，假如else if表达式都不成立，则默认执行else

#### 多分支的特点：

1、if流程控制语句只有一个执行入口，不是if就是else if，或者是else

2、在if流程控制语句中，可以没有else if和else

示例：

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        // 用户输入比赛分数
        System.out.println("请你输入大赛分数：");
        double score = myScanner.nextDouble();
        if(score > 8.0) {
            System.out.println("现在您已经进入到决赛了，请输入性别：");
            char gender = myScanner.next().charAt(0);
            if(gender == '男') {
                System.out.println("您已进入男子组");
            } else if(gender == '女') {
                System.out.println("您已进入女子组");
            } else {
                System.out.println("您输入的性别有误");
            }
        } else {
            System.out.println("您未进入决赛，已被淘汰");
        }
    }
}
```

# 三、分支控制switch？

基本语法：

```java
switch(表达式) {
    case 常量1:
       语句块1;
    break;

    case 常量2:
       语句块2;
    break;

    case 常量3:
       语句块3;
    break;
    ....

    case 常量n:
       语句块n;
    break;

    default:
        defalut 语句块;
}
```

switch解读：

1、switch关键字，表示switch分支

2、表达式对应一个具体的值【所有的表达式都对应一个具体的值】

3、case 常量1：当switch中的表达式值和常量1的值相等的时候，就执行语句块1。其它的case 常量以此类推

4、break表示的是退出这个switch结构，并不是退出整个程序

5、如果一个switch中的表达式一个都没有匹配上case 常量中的任何一个，就默认执行default

switch流程图：

![image-20231125181247491](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231125181247491.png)

1、当switch中的表达式和case 常量中的任何一个值匹配，就会去执行case中相应的代码块

2、当遇到break的时候，程序就会退出switch程序

3、假如在执行case 常量中的代码块的时候，如果没有break，就会`穿透`到下一个case代码块执行出，不会再去判断case 常量是否相等。除非遇到break才会跳出switch程序

示例：

1、请编写一个程序，该程序可以接收一个字符，比如：a、b、c、d、e、f、g

2、a表示周一、b表示周二、c表示周三....

3、根据用户的输入显示相应的信息，要求使用switch完成

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入字符(a-g)：");
        char week = myScanner.next().charAt(0);
        switch(week) {
            case 'a':
                System.out.println("今天是周一");
            break;
            case 'b':
                System.out.println("今天是周二");
            break;
            case 'c':
                System.out.println("今天是周三");
            break;
            case 'd':
                System.out.println("今天是周四");
            break;
            case 'e':
                System.out.println("今天是周五");
            break;
            case 'f':
                System.out.println("今天是周六");
            break;
            case 'g':
                System.out.println("今天是周天");
            break;
            default:
                System.out.println("您输入的信息有误");
        }
    }
}
```

# 四、switch细节及其注意事项？

#### 1、表达式数据类型，应该和case后的常量类型一致，或者可以是自动转换比较的类型，比如输入的是字符，而常量是int

```java
public class Test {
    public static void main(String[] args) {
        int a = 20;
        switch(a) {
            case "a":
                System.out.println("输出12");
            break;
            case 20:
                System.out.println("输出13");
            break;
        }
    }
}
```

解析：a的数据类型是int，而case中常量1的数据类型是String，造成了数据类型不一致，也不可以自动进行类型的转换，所以报错，不可以运行

#### 2、switch（表达式）中表达式的`返回值`【具体的值】必须是：byte、short、int、char、enum、String数据类型

```java
public class Test {
    public static void main(String[] args) {
        double a = 20.0;
        switch(a) { // 这里的a属于double类型，所以直接报错
            case 20.0:
                System.out.println("输出12");
            break;
            case 23.5:
                System.out.println("输出13");
            break;
        }
    }
}
```

#### 3、case中的句子必须是常量，而不能是变量

```java
public class Test {
    public static void main(String[] args) {
        int a = 20;
        switch(a) {
            case a: // 这里的a是变量，20是常量；只可以使用常量20，不可以使用变量a
                System.out.println("输出12");
            break;
            case 23:
                System.out.println("输出13");
            break;
        }
    }
}
```

解析：变量和常量？

1、常量：就是一个具体的值，不可以再被赋值

```java
int a = 20;
// 这里的20就是常量
```

2、变量：可以被重新赋值

```java
int a = 30;
a = 50;
// 这里的a就是变量
```

#### 4、default句子是可选的，当没有匹配的case时，执行default

#### 5、break语句是用来执行完一个case分支后使程序跳出switch语句块；如果没有写break，程序会往下穿透执行到switch结尾，直到遇到break或者是switch执行完毕



# 五、练习题？

1、使用switch将小写类型的char型转换为大写（键盘输入 ）。只是转换a、b、c、d，其它的输出“other”

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入字符(a-d)：");
        char userInput = myScanner.next().charAt(0);
        switch(userInput) {
            case 'a':
                System.out.println('A');
            break;
            case 'b':
                System.out.println('B');
            break;
            case 'c':
                System.out.println('C');
            break;
            case 'd':
                System.out.println('D');
            break;
            default:
                System.out.println("other");
        }
    }
}
```

2、对于学生成绩大于60分的，输出“合格”，低于60分的，输出“不合格”（注：输入的成绩不能大于100），提示：成绩/60

思路分析：

1、这道题可以使用分支来完成，但是要求使用switch

2、这里我们需要进行一个转换【为什么需要转换：因为switch中，表达式必须是具体的值，不像if分支中可以是区间】：

（1）如果成绩在[60,100]，则(int)(成绩/60) = 1

（2）如果成绩在[0,60)，则(int)(成绩/60) = 0

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入成绩(0-100):");
        double score = myScanner.nextDouble();
        // 因为成绩需要限定在0-100之间，所以这里先要进行数据校验
        // 只有当输入的数据在这[0，100]，才执行switch逻辑语句
        if(score >= 0 && score <= 100) {
            switch((int)(score/60)) {
                case 0:
                    System.out.println("不及格");
                break;
                case 1:
                    System.out.println("合格");
                break;
            }
        } else {
            System.out.println("输入的成绩不在可查询范围内");
        }
    }
}
```

3、根据指定月份，打印该月份所属的季节：3、4、5属于春季，6、7、8属于夏季，9、10、11属于秋季、12、1、2属于冬季【提示：使用穿透，不使用break终止程序】

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入季节(1-12):");
        int month = myScanner.nextInt();
        switch(month) {
            case 3:
            case 4:
            case 5:
                System.out.println(month + "属于春季");
                break;
            case 6:
            case 7:
            case 8:
                System.out.println(month + "属于夏季");
                break;
            case 9:
            case 10:
            case 11:
                System.out.println(month + "属于秋季");
                break;
            case 12:
            case 1:
            case 2:
                System.out.println(month + "属于冬季");
                break;
            default:
                System.out.println("输入月份有误");
        }
    }
}
```



# 六、switch和if的比较？【如何判断使用哪一个】

1、如果判断的具体数值不多，而且符合char、byte、short、int、String、enum者6种类型，虽然两个语句都可以使用，但是建议使用switch

2、其它情况：对区间的判断对结果boolean类型判断，使用if-else更多











# 七、for循环控制？

介绍：听名字就是让你的代码可以循环的执行

实际需求：编写一个程序，打印1万句“你好！java”

```java
// 传统方式：直接一句一句的打印，但是这不可能
// 使用循环的方式进行打印输出
```

#### 一、基本语法

```java
for (循环变量初始化;循环条件;循环变量迭代) {
    循环操作(可以有多条语句);
}
/*
循环变量初始化：用来规定从哪一个值开始执行
循环条件：用来控制for的循环范围，值是true或是false
循环变量迭代：用来变化for循环的次数
*/

/*
1、进入for循环，先看循环变量初始化是否符合循环条件，一般都是符合的，不然这个循环就没有意义
2、循环条件为真，直接进入到{}内部的循环操作，而不是先执行循环变量迭代
3、{}内部的循环操作完毕，执行循环变量迭代，再去循环条件中判断循环变量迭代是否为真
4、如果为真，就再执行循环操作；如果为假，就结束for循环
*/
```

解析：

1、for是关键字，表示循环控制

2、for有4要素：循环变量初始化、循环条件、循环变量迭代、循环操作

3、循环操作：这里可以有多条语句，也就是我们要循环执行的代码

4、如果循环操作只有1条语句，可以省略{}，但是不建议这样做，因为代码不清晰

示例及其解析：

```java
public class Test {
    public static void main(String[] args) {
        for (int i = 1;i <= 10;i++) {
            System.out.println("韩顺平java教育" + i);
        }
    }
}
```

解析：当程序进入i=1的时候，会去判断i是否小于等于10，如果小于等于，就会去执行{}里面的代码，而不是先执行i++。当执行完毕{}里面的代码之后，才会执行i++，然后再判断i是否小于等于10，如果小于等于10，再执行{}里面的代码，如果大于10，则不执行，之后则退出for循环，之后的代码继续执行

# 八、for循环细节？

1、循环条件是返回一个布尔值的表达式【也就是说：所有的循环条件，无论再复杂，最终都是要返回布尔值】

2、for循环中的初始化和变量迭代可以写到其它地方，但是两边的分号不能省略

```java
public class Test {
    public static void main(String[] args) {
        int i = 1; // 这里是循环初始化
        for (;i <= 10;) {
            System.out.println("韩顺平java教育" + i);
            i++; // 这里是循环迭代
        }
        System.out.println(i); // 输出：11
    }
}
```

3、循环初始值可以有多条初始化语句，但要求类型一致，并且中间使用逗号隔开；循环变量迭代也可以有多条变量迭代语句，中间也是使用逗号隔开

```java
public class Test {
    public static void main(String[] args) {
        int count = 3;
        for(int i = 0,j = 0;i < count;i++,j+= 2) {
            System.out.println("i=" + i + "j=" + j);
        }
    }
}
```

4、在执for循环的时候，要学会使用内存分析法、流程图来认识代码的执行输出流程

# 九、for循环练习题？

1、打印1~100之间所有是9的倍数的整数，并且统计个数及其总和【化繁为简、先死后活】

（1）化繁为简：就是将总的需求拆分为一个个小部分去实现，组合起来就是这个需求

```java
// 打印1~100之间的数
// 这些数必须是9的倍数的整数
// 还要统计是9的倍数的整数的个数
// 再统计9的倍数的整数的总和
public class Test {
    public static void main(String[] args) {
        int sum = 0;
        for(int i = 1;i <= 100; i++) {
            if(i % 9 == 0) {
                System.out.println(i + "是9的倍数的整数");
                System.out.println(sum += i);
            }
        }
    }
}
```

（2）先死后活：就是先写出固定的程序，之后再根据复用性去升级改进

```java
// 为了适用，不能将区间固定死在1~100之间，这样做是为了方便后续的修改
// 为了适用，不能将倍数固定死在9，因为后期可能会变为其它的
public class Test {
    public static void main(String[] args) {
        int count = 0; // 个数
        int sum = 0; // 总和
        int start = 1; // 开始区间
        int end = 100; // 结束区间
        int multiple = 9; // 可以被整除的倍数
        for(int i = start;i <= end;i++) {
            if(i % multiple == 0) {
                count++;
                sum += i;
            }
        }
        System.out.println("可以被" + multiple + "整除的数有：" + count +"个");
        System.out.println("可以被" + multiple + "整数的数的总和是：" + sum);
    }
}
```

2、完成下面表达式的输出：

![image-20231127105647244](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231127105647244.png)

```java
// 化繁为简：就是将总体需求拆分为一个个的小部分去实现
// 先死后活：就是先写死程序，再该进，让其复用性更高
public class Test {
    public static void main(String[] args) {
        int sum = 0;
        int start = 10;
        int end = 50;
        for (int i = start;i <= end;) {
            for (int j = end;j >= start; j--) {
                sum = i + j;
                System.out.println(i + "+" + j + "=" + sum);
                i++;
            }
        }
    }
}
```



# 十、while循环控制？

基本语法：

```java
循环变量初始化;
while(循环条件){
    循环体(语句);
    循环变量迭代;
}
```

说明：

1、while循环也是有4要素：循环变量初始化、循环条件、循环体、循环变量迭代

2、只是4要素放的位置和for循环不一样

示例需求：使用while完成输出10句"我还是像以前一样爱你！"

```java
// 化繁为简：就是将总体需求拆分为一个个的小部分去实现
// 先死后活：就是先写死程序，再该进，让其复用性更高
public class Test {
    public static void main(String[] args) {
        int i = 1; // 次数统计
        int numberOfTimes = 10; // 打印次数
        while(i <= numberOfTimes) {
            System.out.println("我还是像以前一样爱你！" + i);
            i++;
        }
    }
}
```

# 十一、while循环细节？

```java
循环变量初始化;
while(循环条件){
    循环体(语句);
    循环变量迭代;
}
```

1、循环条件返回的是一个布尔表达式

2、while循环是先判断再执行语句

# 十二、while循环控制练习？

1、打印1~100之间所有可以被3整除的数【使用while】

```java
// 化繁为简：就是将总体需求拆分为一个个的小部分去实现
// 先死后活：就是先写死程序，再该进，让其复用性更高
public class Test {
    public static void main(String[] args) {
        int i = 1; // 开始范围
        int endNum = 100; // 结束范围
        int intDivision = 3; // 整除
        while(i <= endNum) {
            if(i % intDivision == 0) {
                System.out.println(i + "是可以被3整除的数！");
            }
            i++;
        }
    }
}
```



# 十二、do-while循环？

基本语法：

```java
循环变量初始化;
do{
    循环体(语句);
    循环变量迭代;
}while(循环条件);
```

说明：

1、do-while是关键字

2、do-while循环也有4要素：循环变量初始化、循环条件、循环体、循环变量迭代

3、先执行，后判断，也就是说，至少会执行一次

4、最后的while有一个分号

5、while和do-while的区别：要钱

```
while:
你去要钱，先问给不给？1、不给，那就一直打到它还钱位置；2、给，直接走
do-while：
你去要钱，不问给不给，直接打，打到他给，然后走了
```

示例：使用do-while输出10句“hello,java!”

```java
// 化繁为简：就是将总体需求拆分为一个个的小部分去实现
// 先死后活：就是先写死程序，再该进，让其复用性更高
public class Test {
    public static void main(String[] args) {
        int number = 1;
        do{
            System.out.println("hello,java!" + number);
            number++;
        }while(number <= 10);
    }
}
```



# 十三、do-while循环练习题？

1、打印1~100的值

```java
// 化繁为简：就是将总体需求拆分为一个个的小部分去实现
// 先死后活：就是先写死程序，再该进，让其复用性更高
public class Test {
    public static void main(String[] args) {
        int number = 1;
        do{
            System.out.println(number);
            number++;
        }while(number <= 100);
    }
}
```

2、计算1~100的和

```java
public class Test {
    public static void main(String[] args) {
        int start = 1;
        int end = 100;
        int sum = 0;
        do {
            sum += start;
            start++;
        } while(start <= end);
        System.out.println("1~100之间的和是：" + sum); // 输出：5050
    }
}
```

3、统计1~200之间，可以被5整除，但是不能被3整除的数

```java
public class Test {
    public static void main(String[] args) {
        int start = 1; // 开始值
        int end = 200; // 结束值
        int canDivision = 5; // 可以被整除
        int canNotDivision = 3; // 不可以被整除
        do {
            if((start % canDivision == 0) && (start % canNotDivision != 0)) {
                System.out.println(start + "可以被5整除，不能被3整除！");
            }
            start++;
        } while(start <= end);
    }
}
```

6、如果李三一直不还钱，则老韩将一直使出闪电五连鞭，直到李三说还钱为止

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        char answer = ' ';
        do{
            System.out.println("你还钱吗？y/n");
            answer = myScanner.next().charAt(0);
            if(answer == 'n') {
                System.out.println("他说不还钱！");
            } else {
                System.out.println("他说还钱！");
            }
        } while(answer != 'y');
        System.out.println("既然你还钱了，那我就放过你吧！");
    }
}
```



# 十四、多重、嵌套循环控制？【重点、难点】

介绍：

1、将循环放在另一个循环里面，就是形成了嵌套循环，其中，for、while、do-while均可作为外层循环或者是内层循环。【建议：一般使用2层循环嵌套即可，最多不要超过3层，否则，代码的可读性很差】

```java
// 1、for循环嵌套for循环
for (int i = 0; i < xxx; i++) {
     for (int j = 0; j < xxx; j++) {  
     }
}
// 2、while嵌套for循环
while(xxx) {
      for (int i = 0; i < xxx; i++) {
      }
}
// 3、其它的以此类推，谁做外层循环，内层循环都可以
```

2、多重、嵌套循环的实质：其实就是将内层循环作为外层循环的循环体。只有当内层循环的条件为false时，才会完全跳出内层循环，才可以结束外层循环的`当次`循环，开始外层循环的下一次循环。【典型示例：99乘法表，当外层为1的时候，内层要全部执行到9才会终止外层为1的循环；接着又会执行外层为2，内层又需要全部执行到9才会终止外层为2的循环，以此类推，直到99乘法表结束】

```java
public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 9; i++) {          //总共9行
            for (int j = 1; j <= i ; j++) {     //第 i 行有 j 列
                System.out.print(i + "*" + j + "=" + (i*j) + "\t"); // \t 制表符
            }
            System.out.println();               //每一行输出结束后换行
        }
    }
}
```

#### 多重、嵌套循环：外层执行一次，内层要走完所有流程，直到内层自己的条件为false，才结束外层循环的这一次循环。

3、设外层循环次数为m次，内层为n次，则内层循环体实际上需要执行m*n次

```java
public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 7 ; i++) { // 第一层循环7
            for (int j = 1; j <= 2 ; j++) { // 第二层循环2
                System.out.println("ok"); // 输出：ok 2*7=14次
            }
        }
    }
}
```



# 十五、多重、嵌套循环练习？

需求：

1、统计3个班级的学生成绩，每个班级有5个学生，求出各个班级的平均分还有所有班级的平均分【学生的成绩需要从键盘输入】

2、再统计3个班的及格人数，每个班有5个同学

思路分析：

1、不要一上来就写代码，要分析需求

2、不要批量使用需求中的数据，要先转化在可操作范围内再进行加工

3、所有代码需要一步一步走，不要批量去写

4、写代码不需要从上到下、完全按照顺序书写

```java
// 统计3个班级的学生成绩，每个班级有5个学生
// 1、求出各个班级的平均分、所有班级的平均分【学生的成绩需要从键盘输入】
// 2、再统计3个班的及格人数，每个班有5个同学
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        double allGradeSumScore = 0;
        int passNumber = 0;
        for (int i = 1; i <= 3; i++) {
            double gradeSum = 0;
            for (int j = 1; j <= 5; j++) {
                System.out.println("请输入"+i+"班第"+j+"个学生的成绩：");
                double score = myScanner.nextDouble();
                if(score >= 60) {
                    passNumber++;
                }
                gradeSum += score;
            }
            double gradeAverage = gradeSum / 5;
            System.out.println(i + "班级总成绩是：" + gradeSum);
            System.out.println(i + "班级平均成绩是：" + gradeAverage);
            allGradeSumScore += gradeSum;
        }
        System.out.println("所有班级平均分是：" + allGradeSumScore / 10);
        System.out.println("及格人数是：" + passNumber);
    }
}
```



# 十六、空心金字塔？【深度理解多重循环】

1、因为懒，所以直接给出完整版的，想要写出这个效果，需要从矩形——半个金字塔——整个金字塔——镂空金字塔开始写

```java
public class Test{
    public static void main(String[] args) {
        // 将层数作为变量
        int totalLevel = 20;
        // 输出层数
        for (int i = 1; i <= totalLevel; i++) { // i表示层数
            // 在输出星星之前，还需要输出空格，空格 = 增层数 - 当前层
            for (int k = 1; k <= totalLevel - i; k++) {
                System.out.print(" ");
            }
            // 输出星星
            for (int j = 1; j <= 2 * i - 1; j++) {
                // 当前行的第一个位置是*，最后一个位置也是-，最后一层是*
                // 所以就要进行判断位置
                if(j == 1 || j == 2 * i - 1 || i == totalLevel) {
                    System.out.print("*");
                }else { // 其它情况输出空格
                    System.out.print(" ");
                }
            }
            System.out.println(" ");
        }
    }
}
```



# 十七、跳转控制语句：break？

1、需求：随机生成一个1—100的数，直到生成97这个数，看看你一共用了几次？

2、公式提示：使用 (int)(Math.random()*100) + 1

3、用法解析：

```
Math.random()方法的含义：
1、在Math类中，有一个生成随机数的random方法
2、使用这个一个方法生成的随机数字色数据类型是double，生成数字范围在大于等于0.0，小于1.0，即：[0.0,1.0)
```

4、公式提示解析：

```
这里为什么要使用Math.random()*100 + 1呢？
解析：
1、Math.random()是随机生成[0.0,1.0)之间的随机数字
2、Math.random()*100是随机生成[0.0,100.0)之间的数字
3、我们需求是生成[1,100]之间的随机数字，所以使用：Math.random()*100 + 1即可生成所需区间的随机数字
```

5、需求示例：

```java
// 随机生成一个1—100的数
public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 100; i++) {
            int randomNumber = (int)(Math.random()*100) + 1;
            if(randomNumber == 97) {
                System.out.println("这是在第" + i + "次生成了97");
                break;
            }
            System.out.println("第" + i + "次生成的数字是：" +  randomNumber);
        }
    }
}
```

#### 注意：一旦遇到break，就退出循环【注意是整个循环】

例如：循环输出1~10之间的数字，当第3次输出的时候，就终止程序

```java
// 需求：循环输出1~10之间的数字，当第3次输出的时候，就终止程序
public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if(i == 3) {
                break;
            }
            System.out.println("输出了" + i); // 输出：1和2
            // 为什么不输出3呢？
            // 因为在i等于3的时候，遇到了break，导致整个for循环都终止了，于是3不会被输出
        }
    }
}
```



## 一、break：终止循环的细节和注意事项？

1、break出现在多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块

```java
// 第一层标签label
lable1:
for(int i = 0;i < 4;i++) {
    // 第二层标签label
	lable:
	for(int j = 0,j <= 10;j++) {
		if(j == 2) {
			break label1;
		}
	}
	System.out.println("i = " + i);
}
```

解析：

（1）break语句+标签可以指定退出哪层

（2）label1是标签，由于程序员确定，名字可以自定义

（3）break指定到哪个label就退出最近的循环区域

（4）但是建议是实际的开发中，尽量不要使用标签

（5）如果没有指定break，就默认退出最近的循环体



# 十八、练习题目？

1、需求：实现登录验证，有3次机会，如果用户名为”丁真“，密码”666“，则提示成功登录，否则提示还剩余几次机会【`这道题是由是由自己完成的`】

```java
// 需求：实现登录验证
// 有3次机会
// 如果用户名为”丁真“，密码”666“，则提示成功登录
// 否则提示还剩余几次机会
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);

        for (int i = 3; i >= 0; i--) {
            String userName = "";
            int userPassword = 0;
            // 3次登录次数耗尽，退出登录循环
            System.out.println("当前登录次数剩余：" + i + "次");
            if(i == 0) {
                System.out.println("登录次数已耗尽，请5分钟后重试");
                break;
            }

            // 提示用户输入用户名
            System.out.println("请输入用户名：");
            if(myScanner.hasNext()) {
                String userInputName = myScanner.next();
                // 判断输入的名字是否合法
                if(userInputName.charAt(0) == '丁' && userInputName.charAt(1) == '真') {
                    userName = userInputName;
                }
            }

            // 提示用户输入密码
            System.out.println("请输入密码：");
            if(myScanner.hasNextInt()) {
                int userInputPassword = myScanner.nextInt();
                // 判断输入的名字是否合法
                if(userInputPassword == 666) {
                    userPassword = userInputPassword;
                }
            }

            // 用户名、密码正确，也要退出登录循环
            if(userName.equals("丁真") && userPassword != 0) {
                System.out.println("登录成功");
                break;
            } else {
                System.out.println("登录失败，请重试");
            }
        }
    }
}
```

#### 涉及到一个字符串方法的比较：equals

1、格式

```java
String nam = "贾宝玉";
boolean judge = "林黛玉".equals(name);
// 也可以使用：boolean judge = name.equals("林黛玉"); 但是推荐使用第一种
// 为什么推荐第一种呢？答案：因为可以避免空指针【这里暂时不展开讲解】
```



# 十九、跳转控制语句：continue？

1、介绍：continue用于结束本次循环，继续执行下一次循环【注意：是结束本次循环】

```java
public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            if(i == 2) {
                System.out.println("被跳过了");
                continue;
            }
            System.out.println("我爱你");
        }
    }
}
```

2、continue出现在多层嵌套的循环体语句中的时候，可以通过标签指定要跳过哪一次层循环，使用方法和前面的break是一样的

3、continue的基本语法：

```java
{
    ....
    continue；
    ....    
}
```

#### 注意：continue跳到出的本次的所有循环，即使是continue后面还有语句，都不会再输出了，直接跳出本次循环！

4、练习题

```java
public class Test {
    public static void main(String[] args) {
        int i = 1;
        while(i <= 4) {
            i++;
            if(i == 2) {
                continue;
            }
            System.out.println("i = " + i); // 输出：3、4、5
        }
    }
}
```

# 二十、跳转控制语句：return？

1、介绍：return使用在方法中，表示跳出所在的方法，在讲解方法的时候，会详细的介绍，这里我们简单的提一下。注意：如果return写在main方法中，直接退出整个程序，因为main方法是程序的入口

2、注意和break、continue对比起来记忆，就比较好理解了

```java
public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            if(i == 3) {
                System.out.println("韩顺平教育" + i);
                return; // 因为在这里就直接退出了，所以输出2次：hello world、1次韩顺平教育
            }
            System.out.println("hello world");
        }
        System.out.println("go to");
    }
}
```



# 二十一、流程控制语句与循环结合练习题？

1、需求：某人有100,0000元，每经过一次路口，需要缴费，规则如下：当现金>5000,0时，每次缴%5；当现金<=5000,0时，每次缴1000。计算这个人可以经过少次路口，要求：使用 while和break完成

```java
// 某人有100,0000元，每经过一次路口，需要缴费，规则如下：
// 1、当现金>5000,0时，每次缴%5
// 2、当现金<=5000,0时，每次缴1000
// 需求：计算这个人可以经过少次路口，要求：使用 while和break完成
public class Test {
    public static void main(String[] args) {
        double money = 100000;
        int count = 0;
        while(true) {
            if(money > 50000) {
                money = money - money * 0.05;
                count++;
            }else if(money >= 1000) {
                money -= 1000;
                count ++;
            }else {
                break;
            }
        }
        System.out.println(count);
        System.out.println("余额还有" + money);
    }
}
// 可以过62次
// 还剩余：767.497.....
```

2、需求：需求：实现判断一个整数，属于哪一个范围：大于0、小于0、等于0

```java
// 需求：实现判断一个整数，属于哪一个范围：大于0、小于0、等于0
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入整数：");
        if(myScanner.hasNextInt()) {
            int userInputNumber = myScanner.nextInt();
            if(userInputNumber > 0) {
                System.out.println("您输入的：" + userInputNumber + "大于0");
            }else if(userInputNumber < 0) {
                System.out.println("您输入的：" + userInputNumber + "小于0");
            }else {
                System.out.println("您输入的：" + userInputNumber + "等于0");
            }
        }
    }
}
```

3、需求：判断一个年份是否为闰年

```java
// 需求：判断一个年份是否为闰年
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入年份：");
        if(myScanner.hasNextInt()) {
            int userInputYear = myScanner.nextInt();
            if(userInputYear % 4 == 0) {
                System.out.println("您输入的：" + userInputYear + "是闰年");
            }else {
                System.out.println("您输入的：" + userInputYear + "是平年");
            }
        }
    }
}
```

4、需求：判断一个数是否是水仙花数。水仙花数：是指一个3位数，其各个位上数字的立方和等于它本身。例如：153 = 1 * 1 * 1  +  5 * 5 * 5  +  3 * 3 * 3

```java
// 需求：判断一个数是否是水仙花数
// 水仙花数：是指一个3位数，其各个位上数字的立方和等于它本身
// 例如：153 = 1*1*1 + 5*5*5 + 3*3*3
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入水仙花数(3位整数)：");
        if(myScanner.hasNextInt()) {
            int userInputNumber = myScanner.nextInt();
            // 个位数字
            int ge = userInputNumber % 10;
            // 十位数字
            int shi = (userInputNumber/10) % 10;
            // 百位数字
            int bai = (userInputNumber/100) % 10;
            if(userInputNumber ==(ge * ge * ge + shi * shi * shi + bai * bai * bai)) {
                System.out.println("您输入的" + userInputNumber + "是水仙花数");
            }else{
                System.out.println("您输入的" + userInputNumber + "不是水仙花数");
            }
        }
    }
}
```

#### 这里涉及到一个取到数字位的方法：

（1）个位、十位、百位、千位...

```java
int number = 153;
// 个位
int gewei = (number/1) % 10;
// 十位
int gewei = (number/10) % 10;
// 百位
int gewei = (number/100) % 10;
// 千位
int gewei = (number/1000) % 10;
// 3万位
int gewei = (number/10000) % 10;
.....
```

5、需求：输出1~100之间的所有不被5整除的数字，每5个一行

```java
public class Test {
    public static void main(String[] args) {
        // 统计输出的个数
        int count = 0;
        // 输出的数字
        for (int i = 1; i <= 100; i++) {
            if(i % 5 != 0) {
                count++;
                System.out.print(i + " ");
                if(count%5 == 0) {
                    System.out.println();
                }
            }
        }
    }
}
```

6、需求：输出a~z小写字母。输出Z~A大写字母【利用ASCII做】

```java
public class Test {
    public static void main(String[] args) {
        // 输出a~z小写的26个字母
        for (char c1 = 'a'; c1 <= 'z'; c1++) {
            System.out.print(c1 + " ");
        }

        System.out.println();

        // 输出Z~A大写的26个字母
        for (char c1 = 'Z'; c1 >= 'A';c1--) {
            System.out.print(c1 + " ");
        }
    }
}
```



