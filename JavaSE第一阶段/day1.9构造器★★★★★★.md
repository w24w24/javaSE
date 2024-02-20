# 一、构造器？【构造方法也叫做“构造器”】

需求：前面我们在创建人类对象的时候，是先把一个对象创建好之后，再给他的年龄和姓名赋值，如果现在我要求，在创建人类对象的时候，就直接指定这个对象的年龄和姓名，该怎么做？【这个时候就可以使用构造器】

基本语法：

```java
[修饰符] 方法名(形参列表) {
    方法体;
}
```

说明：

1、使用中括号括起来的修饰符可以是默认值不写，也可以写成private、protected、public

2、构造器没有返回值，即构造器不需要使用return语句

3、构造器的方法名和类名必须是一致的

4、构造器的参数列表和成员方法是一样的规则

5、构造器的调用是由系统完成的，不需要程序员手动调用



# 二、基本介绍？

构造方法又是叫做构造器（constructor），是类的一种特殊方法，它主要的作用是完成对新对象的初始化，它有以下几个特点

1、方法名和类型相同

2、没有返回值，也就是不需要return

3、在创建对象的时候，系统会自动调用该类的构造器完成对象的初始化



# 三、构造器快速入门？

需求：来解决创建对象的时候就指定年龄和姓名，简单理解就是在new Person对象的时候就传递参数

```java
public class Test {
    public static void main(String[] args) {
        // 因为使用了构造器，所以可以直接在这里传递参数
        Person p1 = new Person("smith",25);
        System.out.println(p1.name);
        System.out.println(p1.age);
    }
}

class Person {
    // 全局属性
    String name;
    int age;

    // 构造器
    public Person(String pName,int pAge) {
        // 构造器被调用的时候，我们的这个对象已经存在了，构造器只是完成属性的初始化
        System.out.println("构造器被调用，完成了对象的初始化~");
        name = pName;
        age = pAge;
    }
}

// 使用构造器的好处是可以随意更改传递进来的参数，而不用找半天在哪一个类中，然后慢慢去修改
```



# 四、构造器细节和注意事项？

1、一个类可以定义多个不同的构造器，即构造器重载

比如：我可以再给Person类定义一个构造器，用来创建对象的时候，只指定人名，不指定年龄

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象，在创建的时候就是初始化属性
        Person p1 = new Person("smith",25);
        Person p2 = new Person("tom");
    }
}

class Person {
    // 全局变量/属性
    String name;
    int age;

    // 第1个构造方法
    public Person(String pName,int pAge) {
        System.out.println("调用了构造方法，对象已经存在~");
        name = pName;
        age = pAge;
    }

    // 第2个构造方法
    public Person(String pName) {
        name = pName;
    }
}
// 因为重载是方法名字相同，但是参数列表不同，这里的构造方法名字相同，但是参数列表不同，所以构成了重载
```

2、构造器名要和类名相同。假如不相同，那就是成员方法/方法，既然是成员方法/方法，那就是一定有返回值或者是为void。但是构造方法是没有返回值的，也不为void

3、构造器没有返回值，即没有return值

4、构造器是完成对象的初始化，并不是创建对象

```
这句话的理解：
1、构造器/构造方法是在创建对象的时候传递参数，即初始化属性
2、构造器并不能创建对象
```

5、在创建对象的时候，系统自动调用该类的构造方法

```java
//这句话的理解是：
//在new对象的时候，传递了参数，那么jvm虚拟机会自动调用类中的构造方法，并不需要程序员手动去调用，如果程序员手动去调用就会报错

// 示例：
public class Test {
    public static void main(String[] args) {
        // 创建对象，在创建的时候就是初始化属性
        Person p1 = new Person("smith",25);
        // 程序员手动去进行调用，则程序直接报错，因为系统的jvm虚拟机会自动去调用
        p1.Person();
    }
}

class Person {
    // 全局变量/属性
    String name;
    int age;

    // 构造方法
    public Person(String pName,int pAge) {
        System.out.println("调用了构造方法，对象已经存在~");
        name = pName;
        age = pAge;
    }
}
```

6、如果程序员没有定义构造器，系统会自动给类生成一个默认“无参构造器”（也叫做默认构造器），比如：Dog( ) { }，使用javap 反编译试试看

```java
// 编译：从.java文件编译为.class字节码文件叫做编译
// 反编译：从.class字节码文件编译为.java文件叫做反编译

public class Test {
    public static void main(String[] args) {
        // 这里解释为什么创建对象的时候不传递参数，因为在Dog类中的默认无参构造是没有任何参数的
        // 这里就可以进一步了解到前面的“为什么创建对象没有参数了？”
        Dog dog = new Dog();
    }
}

class Dog {
    // 因为这里我们没有定义构造器，所以系统会自动生成一个默认的无参构造器
    // 这个默认的无参构造的意思是：没有参数，没有代码块
    // 就是下面这种形式：
    /*
        Dog() { }
     */
}
```

7、一旦定义了自己的构造器，默认的“无参构造器”就会被覆盖，就不能再使用默认的无参构造器了，除非显示的定义一下，即：Dog( ) { }

```java
public class Test {
    public static void main(String[] args) {
        // 因为在类中显示的定义了默认的无参构造器，所以这里不会再报错
        Dog dog = new Dog();
    }
}

class Dog {
    public Dog(String name) {
        // 这里虽然什么也没有写
        // 但是这里你定义了自己的构造方法
        // 所以原来默认的无参构造方法被这个覆盖了
        // 当你再使用javap去反编译的时候机会报错
        // 而且在main主方法中不传递参数就创建对象也会报错
    }
    
    // 但是我依旧想要在main主方法中使用默认的“无参构造器”
    // 那么你就是需要显示的定义一下
    Dog() {}
    // 这样在main主方法中也不会报错
    // 只是无参构造器被显示定义了
}
```



# 五、课堂练习？

需求：定义一个Person类，并且在这个类中添加两个构造器

1、第一个构造器是“无参构造器”，利用构造器将所有的人的age都设置为18

2、第二个是“有参构造器”，参数是pName和pAge，并且在创建Person对象的时候初始化name和age这两个属性值

3、最后使用输出语句输出结果查看是否成功【这个输出语句可以设置在类中也可以设置在main主方法中】

```java
public class Test {
    public static void main(String[] args) {
        Person person = new Person();
        Person person1 = new Person("jack",24);
    }
}

class Person {
    // 全局属性/变量
    int age;
    String name;

    // 第1个构造器
    public Person() {
        age = 18;
        System.out.println("第2个构造器中的年龄是：" + age);
    }

    // 第2个构造器
    public Person(String pName,int pAge) {
        name = pName;
        age = pAge;
        System.out.println("这个人的名字是：" + name + ",年龄是：" + age);
    }
}
```



