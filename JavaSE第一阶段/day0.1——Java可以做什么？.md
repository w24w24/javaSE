本套Java课程为三个阶段，涵盖了Java基础的方方面面。

第一阶段:建立编程思想(包括:基本语法、数组、排序和查找、面向对象编程、零钱通、房屋出租系统、迷宫、八皇后、汉诺塔 )

第二阶段:提升编程能力(包括: 枚举和注解、Exception、常用类、集合、泛型、线程、IO流、坦克大战) 

第三阶段: 增强分析需求，代码实现能力(包括: 网络编程、反射、Mysql、JDBC和连接池、正则表达式、Java8 Java11 新特性、马踏棋盘、满汉楼、多用户通信系统)

# 一、Java 可以做什么？

第一：明确 JavaSE 就是Java基础，是JavaEE和JavaME的基础，所以必须要学好JavaSE

#### 一、javaEE是什么？

javaEE，java平台企业版（Java Platform Enterprise Edition），之前称之为Java 2 Platform Enterprise Edition（J2EE），2018年3月改名为Jakarta EE（这个名称应该是没有得到民众的认可），是sun公司为企业级应用推出的标准平台，用来开发B/S架构软件，JavaEE可以说是一种框架，也可以说是一种规范。JavaEE是java应用最广泛的部分【B/S：即浏览器/服务器结构。Browser指的是Web浏览器，极少数事务逻辑在前端实现，但主要事务逻辑在服务器端实现。B/S架构的系统无须特别安装，只有Web浏览器即可。】

#### 二、javaEE和javaSE的区别与联系？

javaEE是在javaSE的基础上构建的，是对javaSE的扩展和延申，增加了一些更便捷的应用框架。除了EE和SE，还有为移动端而生的javaME，但目前的应用不算广泛

#### 三、javaEE主要技术？

javaEE号称有13种核心技术，他们分别是：JDBC、JNDI、EJB、RMI、Servlet、JSP、XML、JMS、Java IDL、JTS、JTA、JavaMail、JAF

简单介绍下需要重点关注的技术：

1、JDBC（Java Database  Connectivity ，JDBC）：Java数据库连接，是java语言中用来规范客户端程序如何来访问数据库的应用程序接口，提供了诸如：查询、更新数据库中数据的方法

2、JNDI（Java Naming and Directory Interface,JNDI）：是java的一个目录服务应用程序界面（API），它提供了一个目录系统，并将服务名称与对象关联起来，从而使得开发人员在开发过程中可以使用名称来访问对象

3、EJB（Enterprise JavaBean，EJB）：是一个用来构筑企业级应用的服务器端可被管理组件，不过这个东西在Spring问世后凉凉了，知道是什么就可以了

4、Servlet（Server Applet，Servlet）：是用java编写的服务器端程序，其主要的功能在于交互式的浏览和修改数据，生成动态的web内容

5、JSP（JavaServer Pages）：是由sun公司主导创建的一张动态网页技术标准，JSP部署于网络服务器上，可以响应客户端发送的请求，并根据内容动态的生成HTML、XML或其它格式文档的web网页，然后返回给请求者

#### 四、JavaEE框架

JavaEE拥有广泛市场的原因之一就是使用多种框架来使开发变得简单，对于框架的选择有多种，目前比较常见的框架组合是SSH和SSM，另外Spring本身也提供了多层次的框架可以选择

#### SSH

Structs +  Spring + Hibernate

##### SSM

Spring + SpringMVC + MyBatis

# 二、Java就业方向

1、JavaEE：可以做电商、团购、众筹、sns（社交网络）、教育、金融、搜索

2、大数据软件工程师：大数据应用工程师、大数据挖掘工程师、大数据分析与挖掘

3、Android软件工程师：android平台

# 三、Java开发场景举例？【场景举例是为了说明JavaSE的重要性】

1、SSM：Spring轻量级的容器框架、SpringMVC分层的Web开发框架、MyBatis持久化框架

2、Android核心代码

3、大数据-hadoop

# 四、Java的应用领域？

1、企业级应用：主要指复杂的大企业的软件系统、各种类型的网站。应用领域包括金融、电信、交通、电子商务等，如：京东、淘宝、搜狐

2、Android的应用：Android应用程序使用Java进行开发，Android开发水平的高低很大程度上取决于Java语言核心能力是否扎实，如：王者荣耀、天气预报、电视机上的视频播放器

3、移动领域应用：主要表现在消费和嵌入式领域，是指在各种小型设备上的应用，包括车顶盒、车载的大屏影音娱乐设备、汽车通信设备、扫码的POS机等

# 五、Java语言的重要特点？

1、面向对象：Java语言是面向对象的（OOP）

2、语言健壮：Java的强类型机制、异常处理、垃圾的自动回收机制等都是Java程序健壮性的重要保证

3、跨平台：Java语言是跨平台的，即程序员编写好的 .java文件编译为 .class文件后，既可以运行在windows系统上，又可以运行在linux系统上

4、属于解释型语言：Java和Javascript、php一样是属于解释型语言【解释型语言与编译型语言的区别：解释型语言编译后不可以被机器直接执行，需要一个解释器来执行。编译型语言编译后直接就是二进制的机器码，可以直接被机器执行】

#### 注意：解释型语言和编译型语言，谁性能更高呢？【说不准，这个取决于性能和代码】

# 六、Java运行机制及其运行过程？

1、Java的核心机制：Java虚拟机（Java Virtual Machine）

简而言之，当你编写完一个Java程序之后，想要在不同的平台上运行，就需要经过JVM虚拟。JVM是跨平台运行的基本保证！

# 七、什么是JDK、JRE？

#### 1、JDK的基本介绍

JDK的全称是（Java Development Kit ）Java开发工具包。

JDK = JRE + Java的开发工具【java、javac、javadoc、javap】

JDK是提供给开发人员使用的，其中包含了Java的开发工具包，也包括了JRE，所以安装了JDK，就不用再安装JRE了。

#### 2、JRE的基本介绍

JRE的全称是（Java Runtime Environment）java运行时环境

JRE = JVM + Java的核心类库

JRE包括Java虚拟机（JVM）和Java程序所需要的核心类库等，如果想要运行一个开发好的Java程序，只需要安装JRE即可



# 八、Java中的文件？

在 Java中，.java文件是源文件，.class文件是字节码文件

# 九、什么是编译？

javac Hello.java

1、有了java源文件，通过编译器将其编译为JVM可以识别的字节码文件

2、在该源文件的目录下，通过javac编译工具对Hello.java文件进行编译

3、如果程序没有错误，没有任何提示，但是在当前目录下会出现一个Hello.class文件，该文件称之为字节码文件，也是可执行的java程序

```java
// 解释型语言和编译型语言
// 1、解释型语言：就是不能直接被计算机执行，必须要一个编译器才可以执行
// 提问：为什么解释型语言不可以被直接执行？
// 回答：因为解释型语言不是字节码，而计算机执行的时候需要字节码文件，所以解释型语言不可以被直接执行
// 2、编译型语言：可以被字节码文件直接执行，不需要编译器
// 提问：为什么编译型语言可以被直接执行
// 回答：因为编译型语言编译之后直接就是字节码文件，而计算机执行的恰好是字节码文件，所以可以被直接执行
```

# 十、什么是运行？

1、有了可执行的java程序（Hello.class字节码文件）

2、通过运行java.exe文件对字节码文件进行执行【本质是：java.exe将.class文件装载到JVM机执行】

3、java程序开发的注意事项：对修改后的.java文件需要重新进行编译，生成新的.class文件之后，再进行执行，才能生效

# 十一、Java开发注意事项和细节说明？

1、Java源文件是以 .java为扩展名的，源文件的基本组成是类（class），如：本类中的Hello类

2、Java应用程序的执行入口是main方法，他有固定的书写格式：

```java
public static void main(String[] args) {...}
```

3、Java语言严格区分大小写

4、Java方法是由一条条语句构成的，每个语句以";"结束

5、大括号都是成对出现的，缺一不可

6、一个源文件中最多只能有一个public类，其它类的个数不限

```java
// 只允许有一个 public 类
public class Hello {
    public static void main(String[] args) {
        // ...
    }
}
// 其它类的个数是不限的
class Dog{
    //...
}
class Tirger{
    //...
}
....
```



7、如果源文件包含一个public类，则文件名必须按该类名命名

```java
// 源文件包含一个 public 的 Hello 类
public class Hello {
    // ...
}
// 那么Java的文件名字就必须是以 Hello 来命名
```

8、一个源文件中最多只能有一个public类，其它类的个数不限，也可以将main方法写在非public类中，然后指定运行非public类，这样入口方法就是非public的main方法

```java
// public 类
public class Hello {
    public static void main(String[] args) {
        // ...
    }
}

// 非 public 类
class Dog {
    public static void main(String[] args) {
        // ...
    }
}
class Tirger {
    public static void main(String[] args) {
        // ...
    }
}

*想要运行非public类，将文件编译为.class文件后，直接像运行public类一样，运行非public类即可*
```



# 十二、学习心得体会？

#### 第一步：需求

1、工作需要

2、跳槽、对方要求

3、技术控

#### 第二步：看看能否使用传统的技术解决

1、能解决，但是不完美

2、解决不了

#### 第三步：引出我们学习的新技术和知识点

#### 第四步：学习新技术的或者知识点的基本原理和基本语法（不要考虑细节）

#### 第五步：快速入门（基本程序，crud【增删改查】）

#### 第六步：开始研究技术的注意事项、使用细节、使用规范、如何优化==》没有止境，技术魅力
