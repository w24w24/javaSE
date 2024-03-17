# 一、super用来访问父类中的属性、方法、构造器！

介绍：super代表的是父类的引用，用于访问父类的属性、方法、构造器

<span style="color:red">1、super可以用来访问父类中的属性，但是不能访问父类中被private修饰的属性，语法是：super.属性名字</span>

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        
    }
}

// 父类
class Father {
    // 属性
    public String name = "jack";
    private int age = 24;
    int score = 98;
    protected int grade = 4;
}
// 子类
class Son extends Father {
    // 使用super来访问父类中不被private修饰的属性
    public Son() {
        System.out.println(super.name);
        System.out.println(super.score);
        System.out.println(super.grade);
        System.out.println(super.age); // 报错，super无法访问父类中被private修饰的属性
    }
}
```

<span style="color:red">2、super可以用来访问父类中的方法，但是不能访问被private修饰的方法，语法是：super.方法名字</span>

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {

    }
}

// 父类
class Father {
    // 方法
    public void test1() {
        System.out.println("我是test1");
    }
    protected void test2() {
        System.out.println("我是test2");
    }
    void test3() {
        System.out.println("我是test3");
    }
    private void test4() {
        System.out.println("我是test4");
    }
}
// 子类
class Son extends Father {
    // 使用super来访问父类中的方法，super必须在构造器使用
    public Son() {
        super.test1();
        super.test2();
        super.test3();
        super.test4(); // 报错，因为super无法访问被private修饰的方法
    }
}
```

<span style="color:red">3、super可以用来访问父类的构造器，且必须放在构造器的第一行。语法是：super([构造器参数],[构造器参数],...)</span>

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        Son son = new Son("tom");
    }
}

// 父类
class Father {
    // 父类的无参构造
    public Father(String name) {
        System.out.println("我的名字是：" + name);
    }
}

// 子类
class Son extends Father {
    public Son(String name) {
        // 使用super在子类的构造器中访问父类的构造器
        // 且super必须放置在子类构造器的第一行
        super("jack");
        System.out.println("我的名字是：" + name);
    }
}
```

### <span style="color:red">注：super可以用来访问父类中的属性、方法、构造器，的但是前提是属性、方法、构造器不被private修饰</span>



# 二、super给编程带来的便利/细节？

1、调用父类构造器的好处（分工明确，父类属性由于父类初始化，子类属性由子类初始化）

```java
// 为什么说分工明确？
// 解答：自己类的属性，在自己类的构造器中就进行初始化。只是在使用的时候会使用super去访问父类构造器，本质还是自己在自己的范围内做自己的事情

package com.Extend;

public class Test {
    public static void main(String[] args) {
        Son son = new Son("tom",15);
    }
}

// 父类
class Father {
    // 属性
    private String name;
    private int age;
    // 在自己的构造器中初始化自己的属性
    public Father(String name, int age) {
        this.name = name;
        this.age = age;
        System.out.println(name);
        System.out.println(age);
    }
}

// 子类
class Son extends Father {
    // Son类的私有属性
    private String name;
    private int age;
    public Son(String name, int age) {
        // 只是在使用的时候会使用super去访问父类构造器
        super("jack", 24);
        // 在自己的构造器中初始化自己的属性
        this.name = name;
        this.age = age;
        System.out.println(this.name);
        System.out.println(this.age);
    }
}
```

2、当子类中有和父类中的成员（成员是指：属性和方法）重名时【你肯定疑惑为什么会没有构造器？因为构造器只允许使用自己的类名来命名，所以不可能存在构造器】，为了访问父类的成员，必须通过super。如果没有重名，使用super、this或者是直接访问，都是一样的效果

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        B b = new B();
    }
}
class A {
    public String name = "jack";
    public int age = 24;
}
class B extends A {
    public String name = "tom";
    public int age = 15;

    // 在这里访问父类中的属性
    public B() {
        System.out.println(this.name); // 输出：tom
        System.out.println(super.name); // 输出：jack
    }
}


// 使用this进行访问，先从自己类中查找，如果子类中没有，则向上查找，如果有，并且可以访问，则直接访问
// 使用super进行访问，是直接从父类中开始查找，如果有，并且可以访问，则直接访问。如果没有，则直接报错
```

3、super的访问不局限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用super去访问爷爷类的成员；如果多个基类（上级类）中都有同名的成员，使用super去访问的时候遵循就近原则。A—>B—>C，当然了，在访问的时候也要遵循访问权限的相关规则



# 三、super和this的比较

#### 一、super和this的对比【全部理解了，并且可以使用了】

| No.  | 区别点     | this                                                     | super                                        |
| ---- | ---------- | -------------------------------------------------------- | -------------------------------------------- |
| 1    | 访问属性   | 访问本类中的属性，如果本类中没有，则从父类中继续进行查找 | 直接从父类属性开始访问                       |
| 2    | 调用方法   | 访问本类中的方法，如果本类中没有，则从父类中继续进行查找 | 直接从父亲方法开始访问                       |
| 3    | 调用构造器 | 调用本类的构造器，必须放在构造器的首行                   | 调用父类的构造器，必须放置在子类构造器的首行 |
| 4    | 特殊情况   | 表示当前的对象                                           | 在子类中访问父类对象                         |

#### 二、学习完继承之后，类的定义又进一步完善了，学习情况如下：

1、认识class类：成员变量

```java
class 类名 {
    成员变量;
}
```

2、认识class类：成员方法

```java
class 类名 {
    成员变量;
    成员方法;
}
```

3、认识class类：构造方法/构造器

```java
class 类名 {
    成员变量;
    构造方法;
    成员方法;
}
```

4、认识包package：使用包、导入包、包的层级关系

```java
package 包名;

class 类名 {
    成员变量;
    构造方法;
    成员方法;
}
```

5、继承extends，了解了在继承的中子类与父类

```java
package 包名;

class 子类类名 extends 父类类名 {
    成员变量(属性);
    构造方法(构造器);
    成员方法(成员函数);
}
```

#### <span style="color:red">........并没有完毕，下面还有</span>
