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

