# 一、方法/成员方法【二者的说法虽然不同，但是指向的东西是同一个】

介绍：在某些情况下，我们需要定义成员方法（简称：方法）。比如人类：除了有属性外（姓名、年龄、身高），我们人类还有一些行为，比如：说话、跑步、......通过学习之后，还可以做数学题

这个时候只有使用<span style="color:red">成员方法/方法</span>才能完成，所以这就引出了成员方法/方法

示例：在Person类中添加speak方法，输出“我是一个好人”

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Person p1 = new Person();
        // 调用方法
        p1.speak();
    }
}
// 定义Person类
class Person {
    // 定义speak
    // 注意：定义了方法，但是不进行调用，是没有任何意义的！！
    public void speak() {
        System.out.println("我是一个好人！");
    }
}
```

#### <span style="color:red">方法解读</span>

```java
// public：表示方法是公开的，可以被外部访问
// void：表示方法没有返回值【后面会具体的叙述和解释】
// speak()：speak是方法名！()是形式参数列表,可以接收调用者传入参数
// {}：是方法体，里面写入我们想要执行的代码

public void speak() {
    System.out.println("我是一个好人");
}
```



# 二、练习题目？

1、需求：添加cal方法，可以计算1+...+1000的结果【自己写的】

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        UserMathClass answer = new UserMathClass();
        // 调用方法
        answer.cal();
    }
}
// 定义一个数学类
class UserMathClass {
    public void cal() {
        // 这个方法可以计算1~100的和
        int start = 1;
        int end = 1000;
        int sum = 0;
        for (int i = start; i <= end; i++) {
            sum += i;
        }
        // 打印计算出来的值
        System.out.println(start + "~" + end + "的和是：" + sum);
    }
}
```

2、需求：添加cal2方法，可以接收用户的输入n，并且计算1+....+n的结果【自己写的】

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        // 创建对象
        UserMathClass answer = new UserMathClass();

        // 接收用户输入
        Scanner userInput = new Scanner(System.in);
        System.out.println("请你输入一个数字：");
        int userInputNumber = userInput.nextInt();
        System.out.println("您输入的数字是" + userInputNumber + "，即将为你计算1~" + userInputNumber + "的和");
        // 调用方法
        answer.cal(userInputNumber);
    }
}
// 定义一个数学类
class UserMathClass {
    public void cal(int userInputNumberValue) {
        // 这个方法可以计算1~100的和
        int start = 1;
        int end = userInputNumberValue;
        int sum = 0;
        for (int i = start; i <= end; i++) {
            sum += i;
        }
        // 打印计算出来的值
        System.out.println(start + "~" + end + "的和是：" + sum);
    }
}
```

#### 3、<span style="color:red">示例：添加成员方法getSum，可以计算两个数的和</span>

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        UserMath p1 = new UserMath();
        // 这里只是调用了getSum方法，但是却没有接收return返回的值
        p1.getSum(10,20);
        // 想要接收，就需要像下面这样
        // 这里使用了returnRes来进行接收，所以return的值是返回给returnRes的
        int returnRes = p1.getSum(10,20);
        System.out.println(returnRes); // 输出：30
    }
}
// 创建类
class UserMath {
    public int getSum(int num1,int num2) {
        int res = num1 + num2;
        // 将这个数据使用return返回，返回给谁呢？【谁接收就返回给谁】
        // return 这里并不是返回给getSum，而是先向外暴露，谁接收了就返回给谁
        return res;
    }
}
```

#### <span style="color:red">解析：</span>

```java
// public：表示方法是公开的，可以被外部代码使用
// int：表示方法执行之后，会有一个int类型的返回值
// getSum：是方法名字
// (int num1,int num2)：形式参数列表，有2个形参，可以接收用户传入的两个参数
// return：表示把res的值，返回出去【注意：返回出去的值必须被接收，否则会报错，上述例子使用了returnRes来进行接收】
class UserMath {
    public int getSum(int num1,int num2) {
        int res = num1 + num2;
        return res;
    }
}
```



# 三、方法调用机制？★★★★★★必须要理解这个部分，否则不能学会后面的方法

解析：简而言之就是调用方法的时候，内存中发生了什么！

示例1、在创建的对象中调用了方法

```java
Person p1 = new Person();
	int returnRes = p1.getSum(10,20);
	System.out.println(returnRes);
```

示例2、定义了Perosn类

```java
class Person {
    public int getSum(int num1,int num2) {
        int res = num1 + num2;
        return res;
    }
}
```

示例3、使用一张内存图来解释发生了上述示例发生了什么

![image-20240111200816537](https://github.com/w24w24/javaSE/blob/master/Images/%E6%96%B9%E6%B3%95%E8%B0%83%E7%94%A8%E6%9C%BA%E5%88%B6.png)

解析：示例1在调用示例2中的方法的时候发生了什么？

（1）首先会执行Person p1 = new Person( );因为这个语句是在main主方法中的，所以会在栈中开辟一个空间叫做mian栈

（2）接着执行第二句话：int returnRes = p1.getSym(10,20);这个语句会先执行右边p1.getSum(10,20)

（3）执行p1.getSum(10,20)的时候，又会重新在栈中开辟一个新的空间，暂时就叫做getSum栈【原本没有名字的，而是一个地址！这里为了方便理解给一个名字】

（4）开辟完毕之后，就会执行参数赋值，执行的时候会跳转到Person类中！即把10，20给到Person类中的int num1，int num2，然后在执行int res = num1 + num2

<span style="color:red">（5）接着执行return res，将res返回出去，返回出去给谁呢？</span>

<span style="color:red">解析：返回给到p1.getSum(10,20);但是p1.getSum(10,20)又被returnRes接收，所以returnRes就是接收者！我们通常就是说将res的值返回给到returnRes这个接收者</span>

（6）一旦return完毕之后，这个getSum栈就会被销毁【即被编译器释放】

（7）当System.out.println(returnRes);也执行完毕了，整个main方法也退出了，退出之后main栈也会被销毁！main方法退出了，意味着整个程序也就退出了！

#### 小结：

1、当程序执行到方法的时候，就会开辟一个独立的空间（栈空间：main栈、getSum栈）

2、当方法执行完毕，或者执行到return语句时，就会返回

3、返回到待用调用方法的地方

4、返回之后，继续执行调用方法语句后面的代码

5、当main方法（栈）执行完毕之后，整个程序就退出了





# 四、为什么需要方法？【目的：简化代码，提高代码的复用性】

## 一、使用传统方式进行遍历数组

示例：遍历一个二维数组{{1,2,3},{4,5,6,},{7,8,9}}，需要你将其打印出来【不使用方法，使用传统的循环遍历方式】

```java
public class Test {
    public static void main(String[] args) {
        // 原始数组
        int[][] arr = {{1,2,3},{4,5,6,},{7,8,9}};
        // 使用双重for循环进行遍历
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

1、需求：让你将这个数组，再次遍历

```java
public class Test {
    public static void main(String[] args) {
        // 原始数组
        int[][] arr = {{1,2,3},{4,5,6,},{7,8,9}};
        // 使用双重for循环进行遍历
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
        
        // 使用双重for循环再次进行遍历
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

2、需求：让你将这个数组，再次遍历

```java
public class Test {
    public static void main(String[] args) {
        // 原始数组
        int[][] arr = {{1,2,3},{4,5,6,},{7,8,9}};
        // 使用双重for循环进行遍历
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
        
        // 使用双重for循环再次进行遍历
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
        
        // 使用双重for循环再次进行遍历
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

#### 结论：传统的方式无法胜任需求了

1、使用传统的复制粘贴，次数少还行，假如次数是1w次呢？假如需要添加某些元素呢？

2、代码冗杂度非常高，而且复用性不高

## 二、使用方法进行遍历数组

1、定义一个类，专门来遍历输出二维数组的元素值

```java
public class Test {
    public static void main(String[] args) {
        int[][] arr = {{1,2,3},{4,5,6,},{7,8,9}};
        MyTools myTools = new MyTools();
        // 第一次调用
        myTools.printArr(arr);
        // 第二次调用
        myTools.printArr(arr);
        // 第三次调用
        myTools.printArr(arr);
        // 第四次调用
        myTools.printArr(arr);
        // 第n次调用
        ......
    }
}

// 定义一个类：用来循环遍历输出数组
class MyTools {
    public void printArr(int[][] map) {
        for (int i = 0; i < map.length; i++) {
            for (int j = 0; j < map[i].length; j++) {
                System.out.print(map[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

#### 结论：使用方法，节省了代码量，代码的复用性也变高了！nice

#### <span style="color:red">方法的好处：</span>

1、提高代码的复用性

2、可以将实现的细节封装起来，然后供其它的开发者来进行调用即可！其它开发者并不用关心你的方法的具体是怎么实现的，可以提高开发的效率

# 五、方法的定义？

语法格式：

```
访问修饰符 返回数据类型 方法名字（形参列表） {// 方法主体
	语句块；
	return 返回值;
}
```

<span style="color:red">解析：</span>

1、形参列表：表示成员方法输入cal(int n)，getSum(int num1,int num2)

2、返回数据类型：表示成员方法输出，void表示没有返回值

3、方法主体：表示为了实现某一个功能的代码块

4、return语句不是必须的【体现在没有返回值，为void的时候】

5、老韩提示：结合前面的示例来进行理解，这样就是比较容易学会了



# 六、方法的使用细节1—整体概述？

1、访问修饰符：作用是控制方法的使用范围【访问修饰符总共有4个：默认修饰符、public、protected、private】<span style="color:red">会在面向对象编程（中级）中讲解，请耐心学习</span>

#### 返回数据类型：

1、一个方法最多有一个返回值！思考：假如我想要有多个返回值呢？【使用数组】

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        GetSum arrRes = new GetSum();
        // 调用方法
        int[] result = arrRes.sum(10,20);
        // 输出这个方法计算出来的和、差
        System.out.println("和是：" + result[0]);
        System.out.println("差是：" + result[1]);
    }
}
// 新建计算类
class GetSum {
    // 定义方法：计算和、计算差
    public int[] sum(int num1,int num2) {
        // 使用数组来进行返回多个值
        int[] res = new int[2];
        res[0] = num1 + num2;
        res[1] = num1 - num2;
        return res;
    }
}
```

2、返回类型可以为任意类型，包含基本数据类型和引用数据类型（数组，对象）

```java
return 10; // 10是int类型，属于是基本数据类型
return res; // 上述示例中的res就是数组，属于是引用数据类型
return result; // 假设result = "小明"，属于是String类，同样也是属于引用数据类型
```

3、如果方法要求有返回数据类型，则方法体中的`最后执行语句必须为return值`；而且要求返回值类型必须和return的值类型是一致的或兼容【兼容就是可以进行转换】

```java
public class Test {
    public static void main(String[] args) {
        GetSum arrRes = new GetSum();
        int[] result = arrRes.sum(10,20);
        System.out.println("和是：" + result[0]);
        System.out.println("差是：" + result[1]);
    }
}
class GetSum {
    public int[] sum(int num1,int num2) { // int[]就是方法要求有返回数据类型
        int[] res = new int[2];
        res[0] = num1 + num2;
        res[1] = num1 - num2;
        return res; // 这里return的值res就是和int[]是一致的，都是数组，二者不允许其中一个是其它数据类型，必须对应起来
    }
}
```

4、如果方法是void，则方法中可以没有return语句，或者是只写return，不在后面跟任何值

```java
public class Test {
    public static void main(String[] args) {
        PrintClass res = new PrintClass();
        res.print();
    }
}
// 创建一个打印类：打印”我爱你“三个字
class PrintClass {
    public void print() {
        System.out.println("我爱你");
        return; // 或者可以不写
    }
}
```

5、方法名字：请遵循驼峰命名法，最好是见名知义，表达出该功能的意思即可！比如：得到两个数的和是getSum，这也是在实际开发中遵循的规范



# 七、方法的使用细节2—参数列表？

1、一个方法可以有0个参数，也可以有多个参数，中间使用逗号隔开。比如：

```java
class Example {
    public void getSum(int num1,int num2) {
        ....
    }
}
```

2、参数类型可以为任意类型，包含基本类型和引用类型

```java
class Example {
    public void example(int[] map, int num1, String answer) {
        .....
    }
}
```

3、调用带参数的方法的时候，一定`对应着参数列表传入相同类型或兼容类型`的参数

```java
public class Test {
    public static void main(String[] args) {
        Example example = new Example();
        // int[] map实际参数
        int[] map = {1,2,3};
        // int num1实际参数
        int num1 = 20;
        // String answer实际参数
        String answer = "小明";
        // 对照着class example模板中的形式参数传入对应的实际参数
        example.example(map,num1,answer);
    }
}
class Example {
    // 方法中定义的形式参数
    public void example(int[] map, int num1, String answer) {
        .....
    }
}

// 注意：形式参数和实际参数的类型一定要对应或者是兼容【可以转换的数据类型】，否则无法编译
```

4、在方法定义时的参数称为`形式参数【形参】`，在方法调用时传入的参数称之为`实际参数【实参】`，实参和形参的类型要一致或者是兼容、个数、顺序必须一致

```java
// 方法定义：就是在类中书写方法的模板
class Example {
    // 定义方法
    public void getSum(int num1,int num2) {
        ....
    }
}

// 调用方法：就是在main主方法中使用方法
Public class Test{
    public static void main(String[] Args) {
        Example example = new Example();
        // 调用方法
        example.getSum();
    }
}
```

5、<span style="color:red">方法体</span>里面写完成功能的具体语句，可以输入、输出、变量、运算、分支、循环、方法调用，但是里面不能再定义方法！即方法里面不允许再定义方法

```java
class Example {
    // 这是example方法
    public void example(int[] map, int num1, String answer) {
        // 这是getSum方法
        public void getSum(int num3, int num4) {
            .....
        }
    }
}

// 注意：上述getSum方法无法嵌套在example方法中
```

#### <span style="color:red">注意：方法体中不允许再嵌套方法【禁止套娃】</span>



# 八、方法的使用细节3—方法调用细节？

1、同一个类中的方法调用：直接调用即可

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Example a = new Example();
        a.m1();
    }
}

// 同一个类中的方法调用：直接调用即可
class Example {
    // m1方法
    public void m1() {
        System.out.println("我是m1的方法");
        // 我在这里直接调用m2的方法
        m2();
    }
    // m2方法
    public void m2() {
        System.out.println("我是m2的方法");
    }
}
```

2、跨类中的方法A类调用B类方法：需要通过对象名字进行调用。比如：对象名.方法名(参数)

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        A a = new A();
        a.m1();
    }
}
// A类
class A {
    // m1方法
    public void m1() {
        System.out.println("我是m1的方法");
        // 想要在A类中调用B类中的方法，本质就是：在调用类中创建对象去进行调用
        B b = new B();
        b.m2();
    }
}
// B类
class B {
    // m2方法
    public void m2() {
        System.out.println("我是m2的方法");
    }
}
```

#### <span style="color:red">注意：跨类调用本质就是类与对象的关系【虽然是类与类的呈现】</span>

3、特别说明一下：跨类的方法调用和方法的访问修饰符有关，先暂时这么提一下，后面我们讲解到`访问修饰符`时，还需要再细说【访问修饰符：public、默认修饰符(public)、protected、private】

# 九、方法练习题？

1、需求：编写类AA，有一个方法，判断一个数是奇数还是偶数，返回boolean

```java
// 需求：编写类AA方法，用来判断一个数是奇数还是偶数，返回boolean
public class Test {
    public static void main(String[] args) {
        AA a =new AA();
        int number = 7;
        // 因为我们的方法返回的是boolean类型，所以可以直接将方法调用作为if语句的条件进行使用！这在实际开发中非常常见的
        if(a.isOdd(number)) {
            System.out.println(number + "是奇数");
        }else {
            System.out.println(number + "是偶数");
        }
    }
}
// AA类
class AA {
    public boolean isOdd (int number) {
        boolean result = number % 2 != 0 ? true : false;
        return result;
    }
}
```

2、需求：根据给出的行、列、字符，生成对应的效果。比如：4行4类的*

```java
// 需求：根据给出的行、列、字符，生成对应的效果。比如：4行4类的*
public class Test {
    public static void main(String[] args) {
        Generate res = new Generate();
        // 定义需要传入的实际参数：row、column、c
        int row = 4;
        int column = 4;
        char c = '*';
        res.result(row,column,c);
    }
}
// Generate
class Generate {
    // 使用for循环来做
    // 根据行、列、字符，生成对应的效果
    // 定义需要传入的形式参数：row，column，c
    public void result(int row, int column, char c) {
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < column; j++) {
                System.out.print(c);
            }
            // 控制换行
            System.out.println(" ");
        }
    }
}
```

# 十、方法的传参机制1——基本数据类型的传参机制？★★★★★★

方法的传参机制对于我们今后的编程是非常重要的，一定要搞得清清楚楚、明明白白！

基本案例演示方法的传参机制：使用方法来交换2个变量

1、这是`基本数据类型的传参机制`示例

```java
public class Test {
    public static void main(String[] args) {
        Example example = new Example();
        int a = 10;
        int b = 20;
        example.swap(a,b);
        System.out.println("a=" + a + "\tb=" + b);
    }
}
class Example {
    public void swap(int a,int b) {
        // 这是没有交换之前a，b的值
        System.out.println("a=" + a + "\tb=" + b);
        int temp = a;
        a = b;
        b = temp;
        // 这是交换之后a，b的值
        System.out.println("a=" + a + "\tb=" + b);
    }
}
```

#### <span style="color:red">解析：</span>

1、先执行Example example = new Example();会将Example类中的属性、方法【此类中只有方法swap】加载到堆中的方法区中

2、加载完毕之后会在堆中创建一个空间【因为new就是创建空间】，然后随机生成一个地址，这个地址被example指向

3、然后执行int a = 10；int b = 20；因为是基本数据类型，所以会在栈中使用变量与值的形式直接存储

4、接下来执行example.swap(a,b)，因为swap方法是example指向的地址中的方法，所以执行到这里的时候，会自动到堆中寻找swap这个方法，并且将a = 10，b = 20传递进去

5、在Example类中的swap方法的形式参数a、b接收到了来自main方法中的实际参数a、b，先执行第一个输出语句，然后执行swap的方法体，创建一个临时变量temp，将a和b进行交换，然后再执行一个输出语句

6、当Example类中的swap方法执行完毕了所有语句【因为我们只是调用了swap方法，所以只会执行swap中的语句，其它方法中的语句不会执行，即使它们同属于Example类】，就会跳转回到main方法中接着执行输出语句

7、当main方法中的所有语句都执行完毕了，那么整个程序也就退出了

#### <span style="color:red">实在不理解的话，可以结合day1.5面向对象编程中的第九章：类与对象的分配机制？★★★★★★ 来进行理解和学习</span>



# 十一、方法的传参机制2——引用数据类型的传参机制？★★★★★★

案例演示`引用数据类型的传参机制`

1、需求：在B类中编写一个方法test100，可接收一个数组，然后再test100方法中修改数组，看看原来的数组是否会变化？

```java
// 公共的Test类，即main主方法
public class Test {
    public static void main(String[] args) {
        B b = new B();
        int[] arr = {5,6,7};
        System.out.println("这是在test100中的数组");
        b.test100(arr);
        System.out.println();
        // 调用了方法，所以检测一下数组是否被改变
        System.out.println("这是在main方法中的数组");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
// 创建B类
class B {
    public int[] test100(int[] arr) {
        arr[0] = 100;
        // 遍历这个数组，查看数组是否发生改变了
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        // 因为有返回值类型，所以需使用return将arr返回出去
        return arr;
    }
}
```

<span style="color:red">解析：会发生变化</span>

数组是引用数据类型，不是在栈中采用值类型的形式进行数值传递，而是采用地址拷贝的方法进行传递的！所以上述的test100方法中修改了数组arr[0]的元素值为100，因为是地址拷贝，地址指向的都是同一个数组，所以输出的arr[0]都是被修改过后的100

2、需求：B类中编写一个方法test200，可以接收一个Person(age,salary)对象，在方法中修改该对象的属性，看看原来的对象是否会发生变化

```java
// 公共的Test类，即main主方法
public class Test {
    public static void main(String[] args) {
        B b = new B();
        Person p = new Person();
        p.name = "TheShy";
        b.test200(p);
        System.out.println(p.name);
    }
}
// 创建B类
class B {
    // 创建一个test200方法，用来修改Person对象的name属性
    public void test200(Person p) {
        // 将Person对象中的name修改为“李相赫”
        p.name = "李相赫";
        System.out.println(p.name);
    }
}
// 创建Person类
class Person {
    String name;
    int age;
    int salary;
}
```

<span style="color:red">解析：同理也会发生变化</span>

原理和第一个示例是一致的

3、验证是否听懂？【例题】

简略：其实就是基本数据类型、引用数据类型、new关键字代表的含义

（1）基本数据类型使用的是值传递/值拷贝

（2）引用数据类型使用的是地址拷贝/引用传递

（3）new关键字会在内存中新开辟一个空间，并且将变量值指向这个空间，这样原来的地址就和新开辟空间的地址独立开来了



# 十二、方法练习题——克隆对象？

1、编写MyTools类，编写一个方法可以打印二位数组的数据

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        MyTools myTools = new MyTools();
        int[][] arr = {{1,2,3},{4,5,6},{7,8,9}};
        myTools.printTwoDimensionalArr(arr);
    }
}
// MyTools类
class MyTools {
    public void printTwoDimensionalArr(int[][] exampleArrays) {
        for (int i = 0; i < exampleArrays.length; i++) {
            for (int j = 0; j < exampleArrays[i].length; j++) {
                System.out.print(exampleArrays[i][j] + " ");
            }
        }
    }
}
```

2、需求：编写一个方法copyPerson，可以复制一个Person对象，返回复制的对象【要求：clone对象之后，得到的新对象和原来的对象是两个独立的对象，只是它们的属性相同】<span style="color:red">★★★★★★</span>

```java
public class Test {
    public static void main(String[] args) {
        Person p = new Person();
        p.name = "TheShy";
        p.age = 23;

        MyTools myTools = new MyTools();
        Person p1 = myTools.copyPerson(p);

        System.out.println("p的属性值 age = " + p.age + "\np的属性值 name = " + p.name);
        System.out.println("==============================");
        System.out.println("p1的属性值 age = " + p1.age + "\np1的属性值 name = " + p1.name);
    }
}

class MyTools {
    public Person copyPerson(Person p) {
        // 新建一个对象
        Person newP = new Person();
        newP.name = p.name; // 把原来对象的名字赋给p2.name
        newP.age = p.age; // 把原来对象的年龄赋给p2.age
        newP.name = "李相赫";
        newP.age = 27;
        return newP; // 将这个对象返回出去
    }
}
class Person {
    String name;
    int age;
}
```



# 十三、方法递归调用？★★★★★★

1、基本介绍：递归就是方法自己调用自己，而且在每次调用的时候传入不同的变量【递归有助于编程者解决复杂性问题，同时可以让代码变得更加简洁】

#### <span style="color:red">递归调用的本质：就是方法的调用</span>

语法格式如下：

```java
// 这是一个方法
class Person{
    public int print(int number1,int number2) {
        // 这是很多的语句
        .....
        // 这是方法自己调用自己
        print(参数，参数);
    }
}
```

2、递归可以解决什么问题？

解析：

（1）各种数学问题，比如：8皇后问题，汉诺塔，阶乘问题，迷宫问题，球和篮子的问题(google编程大赛)；

（2）各种算法中也会使用到递归，比如：快排、归并排序、二分查找、分治算法等

（3）将用栈解决的问题【使用了递归之后，会使得代码非常的简洁】

# 十四、递归执行机制？★★★★★★

#### <span style="color:red">注意：递归执行的时候，每一次都会完整的执行一遍方法，注意是完整的执行一遍</span>

示例：打印问题

1、图片内存分析

![image-20240121181037783](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240121181037783.png)

2、代码分析

```java
public class Test {
    public static void main(String[] args) {
        T t = new T();
        t.test(4); // 输出：2
    }
}
// 递归方法
class T {
    public void test(int n) {
        if(n > 2) {
            test(n - 1);
        }
        System.out.println("n = " + n);
    }
}
```

解析：

（1）先在栈中执行main主方法，创建一个对象T t = new T()，会在队中开辟一个空间，并且这个空间会有一个地址，这个地址会被t指向，这里创建对象就结束了。然后执行t.test(4)

（2）因为是方法的调用，所以会在main主方法之外再开辟一个栈空间来执行test方法，因为使用了递归，也就是方法自己调用自己，所以当test每一次递减的时候，都会新开一个栈空间来执行test方法

（3）当所有的递归函数结束调用的时候，产生的栈空间都会被销毁，从而重新进入main主方法中进行执行

（4）当main方法中的所有语句都执行完毕的时候，整个程序就退出执行了



示例：阶乘问题

1、图片同上一致

![image-20240123204707854](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240123204707854.png)

2、代码分析

```java
public class Test {
    public static void main(String[] args) {
        T t = new T();
        int res = t.factorial(5);
        System.out.println(res);
    }
}
// 递归方法
class T {
    public int factorial(int n) {
        if(n == 1) {
            return 1;
        }else {
            return factorial(n - 1) * n;
        }
    }
}
```

#### <span style="color:red">解析：</span>

（1）先在main方法中创建了一个对象，这个对象在创建的时候就在堆中开辟了一个空间

（2）接着执行了t.factorial(5)，因为是调用了方法，所以会重新开辟一个空间来执行这个方法

（3）在main主方法中，我们传递了一个实际参数5，在执行factorial方法的时候，会去新开一个栈来执行方法。代码开始进行判断，因为不符合if语句，所以会执行else中的代码块

（4）遇到else中的方法自己调用自己，又会接着再去开辟一个空间，再进行判断，依旧是else中的代码，又遇到方法自己调用自己，所以这个时候再开一个栈来执行

（5）当n的值符合if语句中的值的时候，就会将这个方法进行返回给调用者【注意：这里的调用者就是一层一层传递下来的方法调用】，所以递归会形成如下形式：

1的递归：1

2的递归：1*2

3的递归：1 * 2 * 3

........

#### <span style="color:red">自主总结：</span>

方法的调用：就是使用原先定义好的方法。在使用方法的时候，可以往里面传入参数，也可以不传入参数，这一切需要取决于方法在定义的时候是否定义了形式参数，如果定义了，就必须要传入参数，没有定义则不需要传入参数

方法的返回值：其实就是谁使用了这个函数，就将这个函数传递给谁【这个地方要和原来理解的区分开，并不是单纯的创建一个变量来接收方法，就认为返回值就是给方法！这个变量的作用只是为了更好的使用方法的返回值而定义的】

#### 方法有很多的变化形式，需要弄懂方法在堆和栈中的执行和创建，这样理解起来就不会有困难

#### <span style="color:red">自主总结：</span>

（1）执行一个独立的方法的时候，就创建一个新的受保护的独立空间(栈空间)

（2）方法的局部变量是独立的，不会相互影响，比如n变量

（3）如果方法中使用的是引用类型变量(比如：数组)，就会共享该引用数据类型的数据

（4）递归必须向退出递归的条件逐渐逼近(也就是我们在循环语句中使用的条件)，否则就是无限的递归，无限递归就会出现栈溢出：StackOverflowError【也叫做“死递归”】

（5）当一个方法执行完毕，或者是遇到return，就会返回。返回的规则是：谁调用<span style="color:red">【即谁创建了这个栈，方法的返回值就返回给谁】</span>，就将结果返回给谁，同时当方法执行完毕或者返回时，该方法也就执行完毕【也就是系统将自动销毁这个栈，释放栈空间出来】



# 十五、使用递归斐波那契—递归练习题？

1、需求：给你一个整数n，请你使用递归的方式求出斐波那契数

斐波那契数规则：1，1，2，3，5，8，13....

（1）当n的值是1的时候，斐波那契数是1

（2）当n的值是2的时候，斐波那契数是1 

（3）当n的值大于等于的时候，斐波那契数是前两个数的和

<span style="color:red">这里就是一个递归的思路</span>

2、代码示例

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Fibonacci fibonacci = new Fibonacci();
        int number = 7;
        int res = fibonacci.fibonacci(-1);
        if(res != -1) {
            System.out.println("当数字是" + number + "的时候，对应的斐波那契数是：" + res);
        }
    }
}
// 斐波那契类
class Fibonacci {
    public int fibonacci(int n) {
        if(n >= 1){
            if(n == 1 || n == 2) {
                return 1;
            }else {
                return fibonacci(n-1) + fibonacci(n-2);
            }
        }else {
            System.out.println("输入的值必须大于等于1");
            // 这里必须给返回值，否则会报错，给-1的返回值是因为方法要求的类型是int
            return -1;
        }
    }
}
```

2、需求：猴子吃桃子，有一堆桃子，猴子第一天吃了其中的一半，并再多吃了1个！以后每天猴子都吃其中的一半，然后再多吃一个。当到第10天的时候，想再吃时（即还没吃），发现只有一个桃子了。问：最初总共有几个桃子？

```java
public class Test {
    public static void main(String[] args) {
        Fibonacci fibonacci = new Fibonacci();
        int day = 1;
        int peachNum = fibonacci.fibonacci(day);
        // 因为上面的peachNum调用了fibonacci.fibonacci()，所以会有返回值
        // 因此这里的peachNum != -1 就是类中的else返回回来的值，不要理解错了
         if(peachNum != -1) {
             System.out.println("第" + day + "天桃子有" + peachNum + "个");
         }
    }
}
// Fibonacci类
class Fibonacci {
    public int fibonacci(int day) {
        if(day == 10) { // 第10天只有一个桃子
            return 1;
        }else if (day >= 1 && day <= 9) {
            return (fibonacci(day + 1) + 1)*2;
        }else {
            System.out.println("输入的天数有误");
            return -1;
        }
    }
}
```

#### <span style="color:red">总结：</span>

（1）递归就是找规律，然后让方法自己调用自己实现一些想要实现的功能

（2）注意使用方法的时候，如果让方法有返回值，可以去利用这个返回值在main主方法中作鉴权

（3）写一段代码的时候，一定要分析需求，这个需求不一定是自己想的，也可以去网络上寻找相关的想法，或者是借助AI，不必一直为难自己去想，这样会阻止自己的学习过程和学习目标

#### 注意：一定要进行代码分析，分析完毕，使用什么技术，使用什么方式写代码都是必须了然于胸

# 十六、老鼠出迷宫？

需求：建立一个棋盘，使用二维数组，让老鼠出迷宫

1、小球得到的路径，和程序员设置的找路策略有关，即：找路的上下左右的顺序相关

```java
public class Test {
    public static void main(String[] args) {
        // 1、建立墙壁，一个8行7列的墙壁wall
        int[][] wall = new int[8][7];
        // 最上面的一层、最后面的一层都是墙壁，使用1来表示
        for (int i = 0; i < 7; i++) {
            wall[0][i] = 1;
            wall[7][i] = 1;
        }
        // 左右两边也是墙壁,使用1来表示
        for (int i = 0; i < 8; i++) {
            wall[i][0] = 1;
            wall[i][6] = 1;
        }
            wall[3][1] = 1;
            wall[3][2] = 1;
        // 地图情况
        for (int i = 0; i < wall.length; i++) {
            for (int j = 0; j < wall[i].length; j++) {
                System.out.print(wall[i][j] + " ");
            }
            System.out.println();
        }

        // 新建这个对象
        T t = new T();
        t.findWay(wall,1,1);

        System.out.println("=========找路的情况如下=========");
        for (int i = 0; i < wall.length; i++) {
            for (int j = 0; j < wall[i].length; j++) {
                System.out.print(wall[i][j] + " ");
            }
            System.out.println();
        }
    }
}

// 建立一个类，用来帮助老鼠出迷宫
class T {
    // 使用递归回溯的思想来解决问题
    // 思路分析：
    // 1、如果找到，就返回true，否则返回false
    // 2、map就是二维数组，即表示迷宫
    // 3、i，j就是老鼠的位置，相当于x和y，来确定老鼠的位置
    // 4、因为我们是使用递归找路，所以先规定map数组的的各个值的含义
    // 5、0表示可以走，1表示障碍物，2表示可以走，3表示走过，但是走不通就是死路
    // 6、当map[6][5] = 2，就说明找到通路了，就可以结束，否则就继续寻找
    // 7、先确定老鼠的找路策略：下——>右——>上——>左
    public boolean findWay(int[][] map, int i, int j) {
        if(map[6][5] == 2) { // 说明已经找到
            return true;
        }else {
            if(map[i][j] == 0) { // 当前这个位置是0，说明可以走
                // 我们假设可以走通
                map[i][j] = 2;
                // 因为可以走通，所以直接使用找路策略
                // 找路策略：下——>右——>上——>左
                if(findWay(map,i + 1,j)) { // 先走下
                    return true;
                }else if(findWay(map,i,j - 1)) { // 向左
                    return true;
                }else if(findWay(map,i,j + 1)) { // 向右
                    return true;
                }else if(findWay(map,i - 1,j)) { // 向上
                    return true;
                }else {
                    // 如果上述的方向都无法走通的话，那么就说明这个线路是错的
                    // 既然是错误的，那么上述的假定路线就是map[i][j] = 2就要被替换
                    // 替换为map[i][j] = 3，即路线无法走通，而且返回值是false
                    map[i][j] = 3;
                    return false;
                }
            }else { // map[i][j] = 1,2,3
                return false;
            }
        }
    }
}
```

2、改变找路策略，看看小球的路径是否会发生变化

<span style="color:red">解析：改变找路策略，小球的路径会发生变化！这是因为找路策略判断的路径发生了vi变化，所以小球的路径一定会发生变化</span>

