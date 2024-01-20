# 一、Java中的键盘输入？

定义：在编程中，需要接收用户输入的数据，就可以使用键盘输入语句来获取。Input.java，需要一个扫描器（对象），就是Scanner类

步骤：

1、导入Scanner类所在的包，在java.util包下

2、使用new关键字创建Scanner类对象（声明变量）

3、调用里面的功能

#### 需求：从控制台接收用户输入的信息【姓名、年龄、薪水】，然后整体打印出来

思路分析：

1、需要接收用户的键盘输入，所以需要使用到Scanner

2、找到Scanner类所在的包，使用里面的方法来辅助完成

代码示意：

```java
/**
 * 导入Scanner
*/
import java.util.Scanner;

public class Test {
	public static void main(String[] args) {
		// 创建 Scanner 对象
		Scanner myScanner = new Scanner(System.in);

		// 调用Scanner中的next()、nextInt()、nextDouble()方法接收用户的信息输入

		// 用户姓名
		System.out.println("请输入姓名：");
		String userName = myScanner.next(); // next() 表示的是：接收用户输入的字符串
		// 用户年龄
		System.out.println("请输入年龄："); 
		int userAge = myScanner.nextInt(); // nextInt() 表示的是：接收用户输入的年龄
		// 用户薪水
		System.out.println("请输入薪水："); 
		double userSalary = myScanner.nextDouble(); // nextInt() 表示的是：接收用户输入的薪水

		// 整体输出打印
		System.out.println("姓名是：" + userName + "\n" + 
			"
                           年龄是：" + userAge + "\n" + "薪水是：" + userSalary);
	}
}
```



# 二、next()和nextLine()的区别？

#### 一、next()

1、一定要读取到有效的字符，next()方法可以结束输出【也就是说：你必须输入字符，假如不输入，直接按下Enter键，是不会结束程序的】

2、在没有输入任何有效的字符之前，直接使用敲入空白字符，next()方法并不会结束程序

3、当你在输入字符之后，再敲入空白字符，那整个程序就结束了，空白字符就相当于是结束了程序

4、next()方法不会识别输入中的空白字符，会自动将其去掉

```java
// 导入包Scanner类，使用类下面的next()、nextLine()方法
import java.util.Scanner;
public class Test{
    public static void main(String[] args) {
        // 实例化Scanner对象
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请你输入字符：");
        // 在使用之前需要先使用hasNext()或是hasNextLie()方法判断是否还有输入的数据
        if(myScanner.hasNext()) {
            // 使用next()方法来进行接收
            String str = myScanner.next();
            System.out.println("输出的内容是：" + str);
        }
        // 注意：凡是属于IO流的类，如果不进行关闭，会一直占用资源，所以需要进行关闭
        myScanner.close();
    }
}
```



#### 二、nextLine()

1、以Enter为结束符，也就是说nextLine()方法返回的是输入回车之前的所有字符

2、可以获得空白字符

```java
// 导入包Scanner类，使用类下面的next()、nextLine()方法
import java.util.Scanner;
public class Test{
    public static void main(String[] args) {
        // 实例化Scanner对象
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请你输入字符：");
        // 在使用之前需要先使用hasNext()或是hasNextLie()方法判断是否还有输入的数据
        if(myScanner.hasNextLine()) {
            // 使用next()方法来进行接收
            String str = myScanner.nextLine();
            System.out.println("输出的内容是：" + str);
        }
        // 注意：凡是属于IO流的类，如果不进行关闭，会一直占用资源，所以需要进行关闭
        myScanner.close();
    }
}

```

#### 三、练习题目

1、输入整数，如果是，则输出这个整数；如果不是，则提示不是整数

```java
// 导入包Scanner类，使用类下面的next()、nextLine()方法
import java.util.Scanner;
public class Test{
    public static void main(String[] args) {
        // 实例化Scanner对象
        Scanner myScanner = new Scanner(System.in);
        // 从键盘接收数据
        int i = 0;
        float f = 0.0F;
        System.out.println("请输入整数：");
        if(myScanner.hasNextInt()) {
            i = myScanner.nextInt();
            System.out.println("整数数据是：" + i);
        }else {
            System.out.println("输入的不是整数");
        }
        // 关闭IO流
        myScanner.close();
    }
}
```

2、输入小数，如果是，则输出这个小数；如果不是，则提示不是小数

```java
// 导入包Scanner类，使用类下面的next()、nextLine()方法
import java.util.Scanner;
public class Test{
    public static void main(String[] args) {
        // 实例化Scanner对象
        Scanner myScanner = new Scanner(System.in);
        // 从键盘接收数据
        int i = 0;
        float f = 0.0F;
        System.out.println("请输入小数：");
        if(myScanner.hasNextFloat()) {
            f = myScanner.nextFloat();
            System.out.println("输入的小数是：" + f);
        }else {
            System.out.println("输入的不是小数");
        }
        // 关闭IO流
        myScanner.close();
    }
}
```

