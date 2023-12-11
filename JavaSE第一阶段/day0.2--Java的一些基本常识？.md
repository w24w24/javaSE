# 一、Java常用的转义字符？

1、\t：一个制表位，实现对齐的功能

```java
public class Hello{
	public static void main(String[] args) {
		System.out.println("中国\t美国\t日本");
	}
}
```

2、\n：换行符，实现换行

```java
public class Hello{
	public static void main(String[] args) {
		System.out.println("中国\n美国\n日本");
	}
}
```

3、\ ：转义字符【注意：\ 是一个转义字符，想要输入 \ ，就是需要使用到它】

4、\ ": 一个''

5、\ \：一个 \

6、\r：一个回车【注意：\r 会回到本行的最前面，并且用\r后面的字符替掉换前面的所有字符】

```java
public class Hello{
	public static void main(String[] args) {
		System.out.println("谭磊是你最爱的！\r不知道");
	}
}
```

#### 实际运用例子：

```java
public class Hello{
	public static void main(String[] args) {
		System.out.println("书名\t作者\t价格\t销量\n三国\t罗贯中\t120\t1200");
	}
}
```



# 二、注释（comment）？

介绍：用于注解和说明解释程序的文字就是注释，注释提高了代码的可阅读性；

Java中的注释类型：单行注释、多行注释、文档注释

1、文档注释【主要讲解文档注释】

第一步：在.java文件中使用文档注释

```java
/**
 * @author 谭磊
 * @version 1.0
*/

public class Hello {
	public static void main(String[] args) {
		Syste.out.println("这是关于文档注释");
	}
}
```

第二步：在.java文件目录下使用dos命令生成doc注释

```java
javadoc -d f:\\temp -author -versions Hello.java
```

语法诠释：

javadoc -d 的意思是生成doc文档注释；

f:\ \temp 的意思是在f盘符下的temp文件夹中；

-author 、-version的意思是生成这两个选项的doc文档注释

Hello.java的意思是指生成这个.java文件中的doc注释

第三步：在生成好的temp目录下的index.html文件中查看生成好的doc文档注释目录



# 三、Java代码规范？

1、类、方法的注释，要以javadoc的方式来书写

2、非Java Doc 的注释，往往是给代码的维护者看的，着重告诉读者为什么要这样写，如何修改，注意什么问题等

3、只使用 tab操作，让代码可以向右边移动；使用shift + tab，让代码可以向左边移动

4、Java的源文件使用utf-8编码进行保存

5、代码编写分为次行风格和行尾风格，但是推荐使用行尾风格



# 四、悬挂Javadoc注释【Dangling Javadoc Comment】？

产生原因：在Java的开发过程中，我们常常会使用Javadoc注释来为代码提供文档说明。然而，有时候我们可能会忘记及时更新这些注释，或者删除了相应的代码却忘记删除注释，导致出现了悬挂Javadoc注释。

示例：不会产生悬挂javadoc注释

```java
/**
 * @author 谭磊
 * @version 1.0
 */
public class Test {
    public static void main(String[] args) {
        ....
    }
}
```

示例：会产生悬挂javadoc注释

```java
/**
 * @author 谭磊
 * @version 1.0
 */
```

#### 也就是说，当你使用javadoc注释的时候，没有在javadoc注释之后有内容/代码，就会产生悬挂javadoc注释
