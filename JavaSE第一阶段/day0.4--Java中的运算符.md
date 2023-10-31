目录：

1、运算符介绍

2、算数运算符

3、关系运算符

4、逻辑运算符

5、赋值运算符

6、三元运算符

7、运算符优先级

8、二进制★★★★

9、位运算符★★★★



# 一、运算符介绍?

运算符是一种特殊的符号，用以表示数据的运算、赋值和比较

1、算数运算符

2、赋值运算符

3、关系运算符【比较运算符】

4、逻辑运算符

5、位运算符【需要二进制基础】

7、三元运算符

# 二、算术运算符？

算数运算符是对数值类型的变量进行运算的，在java程序中使用得非常多

![image-20231023220329635](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20231023220329635.png)

重点讲解除法/、模%、加加++



# 三、java中除法/的使用？

注意：java中除法的使用技巧在于数据的类型【整数和整数相除，只可以得到整数！！浮点数和整数相除，得到的是浮点数！！】

```java
public class Test{
    public static void main(String[] args) {
        System.out.println(10 / 4); // 输出：2【因为10和4都是int类型，得到的也必须是Int类型】
        system.out.println(10.0 / 4); // 输出：2.5【因为10.0是double类型是，所以可以取到小数点后面的数字】
        double d = 10 / 4; // 输出：2.0，因为10和4都是int类型，但是前面使用了double来进行接收，所以是double类型
    }
}
```



# 四、取模%？

公式：a % b = a - a / b * b【所有的取模都是运用这一个公式进行计算】

```java
public class Test {
    public static void main(String[] args) {
        System.out.println(10 % 3 ); // 输出：1
        System.out.println(-10 % 3 ); // 输出：-1
        System.out.println(10 % -3); // 输出：1
    }
}
```



# 五、自增 ++？

1、作为独立的语句使用：前 ++ 和后 ++ 是完全一样的

```java
++i = i + 1;
i++ = i + 1; 
```

2、和表达式子结合使用：前 ++ 和 后 ++ 是不一样的

```java
// 后置加加：先赋值，再自增—— a = b; b = b + 1
int b = 10;
int a = b++;
System.out.println(a); // 输出：10
System.out.println(b); // 输出：11

// 前置加加：先自增，再赋值——b = b + 1;a = b
int b = 10;
int a = ++b;
System.out.println(a); // 输出：11
System.out.println(b); // 输出：11
```

