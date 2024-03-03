# 一、面向对象编程（中级）

学习目录：

1、IntelliJ IDEA

2、包

3、访问修饰符

4、封装★★★★★

5、继承★★★★★

6、多态★★★★★

7、super

8、overwrite

9、Object类详解

10、断点调试



# 二、ItelliJ IDEA创建项目？

第一步：new project

第二步：给项目起名字，起完名字之后就是看存放路径了，如果你自己建了文件，想把这个项目放在这个文件中，请你一定要在存放路径之后添加：`\项目名字`



# 三、认识ItelliJ IDEA产生的文件？

1、src：是源文件，即.java源码文件

2、out：是src下的类编译之后的字节码文件，即.class字节码文件【out中有多少个class文件取决于你在src的.java源文件中写了多少个class类，一个class类就对应一个.class字节码文件】



# 四、IntelliJ IDEA快捷键？

1、自动补全代码：alt + /

2、自动运行代码：alt + R

3、构造器快捷生成：alt + W

4、查看类的继承关系：ctrl + H（学习继承之后是非常有用的）

5、快速查找方法位于哪一个类：ctrl + B或者ctrl + 鼠标点击（学习继承之后是非常有用的）

6、自动导入包：alt + Enter







# 五、包？

应用场景：现在有两个程序员共同开发一个java项目，程序员xiaoming想要定义一个Dog类，程序员xiaoqing也想要定义一个Dog类。两个程序员为此还吵了起来，怎么办呢？

#### <span style="color:red">它们为什么会吵起来？</span>

解析：因为在同一个文件夹下面不允许有相同的类名，这个时候就引出了“包”

## 一、包的作用？

1、区分相同名字的类

2、当类很多的时候，可以很好的管理类

3、控制访问范围

## 二、包的基本语法？

```
package com.hspedu;
```

解析：package是一个关键字，表示打包；com.hspedu表示包名

## 三、包的分类？

包分类：系统提供的包、程序员自定义的包



# 六、包的本质？

报的本质：实际上就是创建不同的文件夹/目录来保存类文件

包示意图：

![image-20240227193658778](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240227193658778.png)



# 七、包快速入门？

需求：创建一个com包，然后在包下面定义相同的Dog类，然后再创建一个use包，在use包下定义Test类测试包的引入和使用

第一步：创建包

```
点击file，然后new一个Package
```

第二步：命名

```
在命名的时候，要以com开头，这个com就相当于是文件夹的一级目录
示例：
com.xiaoming
com.xiaoqing
```

第三步：在二级目录xiaoming、xiaoqing下创建Dog类

第四步：按照上述方式再在com下创建一个use包，并且创建Test类

第五步：开始导入包进行测试

1、这是xiao ming包

```java
package com.xiaoming; // 这是包的标识，代表com下有一个xiaoming包，包里面有Dog类

public class Dog {
    public void test() {
        System.out.println("xiaoming");
    }
}
```

2、这是xiaoqing包

```java
package com.xiaoqing; // 这是包的标识，代表com下有一个xiaoqing包，包里面也有Dog类

public class Dog {
    public void test() {
        System.out.println("xiaoqing");
    }
}
```

3、这是use包：将use包下的Test设置为main主方法来测试xiaoming和xiaoqing

```java
package com.use;
// 导入xiaomingn包下的Dog类
import com.xiaoming.Dog;
// 如果还想要使用xiaoqing包下的Dog类，则不能再使用import导入

public class Test {
    public static void main(String[] args) {
        // 这里创建的对象是xiaoming的
        Dog dog = new Dog();
        dog.test(); // 输出：xiaoming

        // 想要使用xiaoqing下的Dog类，不能使用import导入，直接写明路径。因为再使用import导入，编译器无法判断类名相同的Dog类
        com.xiaoqing.Dog dog1 = new com.xiaoqing.Dog();
        dog1.test();
    }
}
```

#### <span style="color:red">解析：</span>

（1）为什么第一次使用xiaoming的时候需要使用import导入？

解析：因为这是固定语法，import表示的是导入

（2）为什么第二次使用xiaoqing的时候不需要使用import导入呢？

解析：假如再使用import导入，虽然包名不一样，但是Dog类是一样的。在创建完对象的时候，编译器是不知道你创建的Dog是谁的，就会给你默认为xiaoming中的Dog

```java
// 导入包
import com.xiaoming.Dog;
import com.xiaoqing.Dog;

// 使用包
Dog dog1 = new Dog();
Dog dog2 = new Dog();
```

（3）如何解决这个问题呢？

解析：第一次导入xiaoming包后，后面想要再使用同一级类包，则在创建对象的时候直接写明路径即可

```java
// 导入xiaoming包
import com.xiaoming.Dog;
public class Test {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.test(); // 输出：xiaoming
        // 想要使用xiaoqing下的Dog类，不能使用import导入，需要写明路径
        com.xiaoqing.Dog dog1 = new com.xiaoqing.Dog();
        dog1.test();
    }
}
```



# 八、包的命名？

## 一、命名规则？

1、只能包含数字、字母、下划线、小圆点，但是不能使用数字开头，不能是关键字或是保留字

```
包示例：
demo.class.exec1; // 错误，因为含有了关键字class
demo.12a; // 错误，因为使用了数字开头
demo.ab12.oa; // 正确
```

## 二、命名规则？

1、一般是小写字母 + 小圆点：com.公司名字.项目名字.业务模块名

```
示例：
com.hspedu.oa.model;
com.hspedu.oa.controller
```

2、一般包名都是有含义的，并且开发人员可以快速定位

```
com.sina.crm.user; // 用户模块
com.sina.crm.order; // 订单模块
com.sina.crm.utils; // 工具类
```

# 九、java中常使用的包？

解析：一个包下面包含很多的类，java中常用的包有下面几种：

1、java.lang.*：是java的基础包，这个包不需要导入，java默认已经导入，直接使用即可

2、java.util.*：是系统提供的工具包、工具类，例如使用Scanner

3、java.net.*：网络包，做网络开发的

4、java.awt.*：是做java界面开发的，GUI编程



# 十、包的使用细节？

## 一、如何导入包？

解析：两种方式，一种是用到什么包导入什么包，另一种是一次性全部导入

```java
// 需求，使用Scanner接收用户的输入和输出
import java.util.Scanner; // 因为需要使用到，所以只导入Scanner
import java.util.*; // 虽然需要使用到Scanner，但是一次性将包全部导入了
```

提问：既然有两种包导入方式，使用哪一种会好一点呢？

<span style="color:red">推荐使用什么包下的类，就导入具体的，不要使用*号一次性导入。原因是：java的开发者也是这样使用的</span>

需求：导入一个Arrays包，使用Arrays下的sort( )方法对数组元素进行排列

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {1,-0,-3,4,9,12,5};
        Arrays.sort(arr);
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + "\t");
        }
    }
}
```



## 二、包的注意事项和使用细节？

1、package的作用是声明当前类所在的包，需要放在class的最上面，一个类中最多只允许有一个package

```java
package com.xiaoming;

public class Main {
    public static void main(String[] args) {
        
    }
}
```



2、import指令，位置放在package的下面，在类定义的前面，可以有多句，并且没有顺序要求

```java
package com.xiaoming;
import java.util.Arrays;
import java.util.Scanner;
import java.awt.*;
public class Main {
    public static void main(String[] args) {

    }
}
```





# 十一、访问修饰符？

基本介绍：java提供了4种修饰符号控制方法和属性（成员变量）的访问权限

## 一、4种访问修饰符

1、公开级别：public修饰，对外公开

2、受保护级别：用protected修饰，对子类和同一个包中的类公开

3、默认级别：没有任何的修饰符号，向同一个包的类公开

4、私有级别：用private修饰，只有类本身可以访问，不对外公开

## 二、4种访问修饰符的访问范围

解析：在测试的时候注意字面意思，不要将乱建包，乱引用

#### <span style="color:red">注意：同一个包下面的类可以直接进行引用，不需要再使用import引入</span>

| 序号 | 访问级别 | 访问控制修饰符 | 同类 | 同包 | 子类 | 不同包 |
| ---- | -------- | -------------- | ---- | ---- | ---- | :----- |
| 1    | 公开     | public         | √    | √    | √    | √      |
| 2    | 受保护   | protected      | √    | √    | √    | ❌      |
| 3    | 默认     | 没有修饰符     | √    | √    | ❌    | ❌      |
| 4    | 私有的   | private        | √    | ❌    | ❌    | ❌      |



# 十二、访问修饰符的注意事项？

1、修饰符可以用来修饰类中的属性、成员方法以及相关类

```java
class Test {
    public int num1= 100;
    protected int num2 = 200;
    int num3 = 300;
    private int num4 = 400;
 }
```



2、只有默认的和public才能修饰类，并且遵循上述访问权限的特点

```java
// 这是使用public来修饰class
public class Main {
    public static void main(String[] args) {

    }
}
// 这是使用默认的修饰符来修饰class
class Test {
    
}
```

3、因为没有学习继承，因此在关于子类的访问权限中，我们再讲解完毕子类后，再回头讲解

4、成员方法的访问规则和属性是完全一致的







