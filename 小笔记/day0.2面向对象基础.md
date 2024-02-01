# 一、面向对象

面向对象编程：一种通过对象的方式，将现实世界映射到计算机模型中的一种编程方式

## 一、类class和实例instance

只要理解了class和instance，基本上就明白了什么是面向对象编程了

```java
import java.util.Arrays;
public class Test {
    public static void main(String[] args) {
        // 1、Person name是指：创建了一个person类型的变量，名字为name，并且指向了new Person()
        // 2、new Person()是指：创建了一个Person实例，并且被前面的name指向了
        Person ming = new Person();
        ming.name = "亚索";
        ming.age = 23;
        System.out.println("姓名是：" + ming.name + "\n年龄是：" + ming.age);
    }
}

// 定义一个Person类(class也是一种数据类型)
class Person {
    public String name; // 字段：描述Person这个类的特征
    public int age; // 字段：描述Person这个类的特征
}
// 注意：只定义类，但不实例化，这样是没有任何意义的
```

#### 实例化：其实就是对照class类模板，在instance实例中进行赋值、给数据

#### 结论：

1、在OOP中，class和instance是“模板”和“实例”的关系

2、定义class就是定义一种数据类型，对应的instance就是这种数据类型的实例

3、class中定义的字段field，在instance中都会拥有自己的字段field，不会相互影响

4、通过关键字new创建新的instance，然后使用变量来指向它，即可通过变量来引用这个instance

5、访问实例字段的方法是：`变量名.字段名`

6、指向instance的变量都是引用变量，例如：ming



## 二、方法

#### 1、为什么需要使用到方法？【public修饰符引起的】

```java
import java.util.Arrays;
public class Test {
    public static void main(String[] args) {
        Person ming = new Person();
        ming.name = "亚索";
        ming.age = -99;
        System.out.println(ming.age); // -99
    }
}

class Person {
    public String name;
    public int age;
    public String grade;
}
/*
1、在上述中，我们直接将Person类的field直接使用了public暴露给了外部
2、这样会破坏代码的封装性，也就是容易被外部攻击，例如：
ming.age = -99;
3、这样的情况是可能发生的，而且年龄是不可能为负数的
4、所以就引出了“方法”这个概念
 */
```

#### 结论：直接去操作在instance中操作class中的field容易造成逻辑混乱，为了避免外部代码直接去访问field，我们必须解决这个问题！而这个问题的产生就是public修饰符

## 2、使用private修饰符去代替public修饰符，解决外部代码直接访问class中的field的问题，如下：

```java
import java.util.Arrays;
public class Test {
    public static void main(String[] args) {
        Person ming = new Person();
        ming.name = "亚索";
        ming.age = -99;
        System.out.println(ming.age); // 报错
    }
}

class Person {
    private String name;
    private int age;
    private String grade;
}
```

解析：但是代码直接报错了，这是为什么？

这是因为我们使用private来修饰class中的field，导致外部代码无法访问class类中的field，如何解决呢？

这个时候就需要使用method来让外部代码可以间接的修改class中的field

#### 为什么method可以解决private无法向外暴露的问题呢？

底层原理：Java规定，如果使用了private对属性进行封装，想要在外部访问私有属性，按照java的设计原则，必须提供getter和setter方法

1、getter方法：主要用于属性内容的获取

2、setter方法：主要用于进行属性内容的设置和修改

3、private实现封装的最大特征是：只允许本类访问，不允许外部类访问

```java
public class Test {
    public static void main(String[] args) {
        Person ming = new Person();
        // name
        ming.setName("亚索");
        String name = ming.getName();
        System.out.println("姓名是：" + name);
        // age
        ming.setAge(23);
        int age = ming.getAge();
        System.out.println("年龄是：" + age);
    }
}

// 新建一个Person类
class Person {
    // Person类中有2个field，被private修饰
    private String name;
    private int age;

    // 因为使用private修饰的field无法被外部的代码访问
    // 所以需要使用到private，所以必须使用getter、setter方法
    public String getName() {
        return this.name;
    }
    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return this.age;
    }
    public void setAge(int age) {
        if(age < 0 || age > 100) {
            throw new IllegalArgumentException("invalid age value");
        }
        this.age = age;
    }
}
```



