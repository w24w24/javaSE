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

