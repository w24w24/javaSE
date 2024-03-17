# 一、方法重写介绍？

基本介绍：方法重写/方法覆盖，就是子类有一个方法，和父类<span style="color:red">`这里的父类不一定是直接父类，也有可能是父类的父类，都可以`</span>的某个方法的名称、返回类型、参数一样，那么我们就说子类的这个方法覆盖了父类的方法，下面使用Animal和Dog来演示

1、Animal类，在这里面有一个cry方法

```java
package com.Extend;

public class Animal {
    // 这是Animal类中的方法
    public void cry() {
        System.out.println("动物叫唤...");
    }
}
```

2、Dog类，在这里面重写了Animal类中的cry方法

```java
package com.Extend;

public class Dog extends Animal {
    // Dog类继承了Animal类
    // 在这里重写了Animal中的cry方法
    public void cry() {
        System.out.println("小狗叫唤...");
    }
}
```

3、RunTest类，在这里运行

```java
package com.Extend;

public class RunTest {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.cry();
    }
}
```

#### <span style="color:red">注：在RunTest中运行的时候，会先从子类中开始查找，如果子类中没有，就会去父类中查找，如果父类中也没有，那就接着往上查找，如果都没有，那就报错</span>



# 二、方法重写的注意事项和细节？

介绍：方法重写也叫做方法覆盖，需要满足下面的条件

#### 1、子类方法的形参列表、方法名称，要和父类中的形参列表、方法名称完全一致

```java
// 这是Animal类
package com.Extend;
public class Animal {
    // 形参列表为空、方法名称为cry
    public void cry() {
        System.out.println("动物叫唤...");
    }
}

// 这是Dog类
package com.Extend;
public class Dog extends Animal {
    // 形参列表也为空、方法名称也为cry
    public void cry() {
        System.out.println("小狗叫唤...");
    }
}
```

#### 2、子类方法的返回类型和父类方法的返回类型必须一致，或者子类方法的返回类型必须是父类方法返回类型的子类【例如：父类的返回类型是Object，子类要么为Object，要么为String。要么一致，要么是父类的子类】

```java
// 这是Animal类
package com.Extend;
public class Animal {
    // 返回类型是Object
    public Object cry() {
        System.out.println("动物叫唤...");
    }
}

// 这是Dog类
package com.Extend;
public class Dog extends Animal {
    // 返回类型可以是Object，也可以是String
    public Object cry() {
        System.out.println("小狗叫唤...");
    }
}
```

#### 3、子类方法不能缩小父类方法的访问权限，但是可以扩大。【假如父类的访问权限修饰符为public，那么子类就只能是public，因为使用其它的修饰符号都会缩小父类方法的访问权限】

#### <span style="color:red">修饰符权限顺序：public > protected > 默认修饰符号 > private</span>

```java
// 这是Animal类
package com.Extend;
public class Animal {
    // 修饰符为protected
    protected Object cry() {
        System.out.println("动物叫唤...");
    }
}

// 这是Dog类
package com.Extend;
public class Dog extends Animal {
    // 因为父类修饰符号是protected，子类不不能缩小父类的访问权限，但是可以扩大，所以这里可以使用public或者是protected
     public Object cry() {
        System.out.println("小狗叫唤...");
    }
}
```



# 三、方法重载和方法重写的对比？

## 一、表格对比

| 名称             | 发生范围 | 方法名   | 形参列表                         | 返回类型                                                 | 修饰符                                           |
| ---------------- | -------- | -------- | -------------------------------- | -------------------------------------------------------- | ------------------------------------------------ |
| 重载（overload） | 本类     | 必须一样 | 类型、个数、顺序，至少有一个不同 | 只需要方法名相同，返回类型不要求                         | 无要求                                           |
| 重写（override） | 父子类   | 必须一样 | 相同                             | 子类重写的方法，返回类型要么和父类一致，要么是父类地子类 | 子类方法不能缩小父类方法地访问范围，但是可以扩大 |



## 二、例题【自己完成的】

需求：

（1）编写一个Person类，包括属性/private(name,age)、构造器、方法say(返回自我介绍地字符串)

（2）编写一个Student类，继承Person类，增加id、score属性/private，以及构造器，定义say方法(返回自我介绍地信息)

（3）在main主方法中，分别创建Person和Student对象，调用say方法输出自我介绍

```java
package com.Extend;

public class Exercise {
    public static void main(String[] args) {
        Person person = new Person("jack",24);
        String PersonRes = person.say();
        System.out.println(PersonRes);

        System.out.println("========================");

        Student student = new Student("tom",35,15,89.0);
        String studentRes = student.say();
        System.out.println(studentRes);
    }
}

/**
 * Person类：个人信息
 */
class Person {
    // 属性
    private String name;
    private int age;

    // 构造器
    public Person() {}
    public Person(String name,int age) {
        this.name = name;
        this.age = age;
    }

    // 封装信息：需要返回的个人信息
    public String returnInformation() {
        return "名字：" + this.name + "\n年龄:" + this.age;
    }
    // 成员方法：调用需要返回的个人信息
    public String say() {
        return returnInformation();
    }

    // get和set方法
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

/**
 * Student类：继承Person类，具体化个人信息
 */
class Student extends Person {
    // 属性：增加id、score
    private int id;
    private double score;

    // 构造器：给属性赋值
    public Student() {}
    public Student(String name, int age,int id,double score) {
        super(name, age);
        this.id = id;
        this.score = score;
    }

    // 封装：返回学生具体信息
    public String returnStudentInformation() {
        return "id：" + this.id + "\n" +  super.say() + "\n分数:" + this.score;
    }

    // say方法：调用学生的具体信息
    public String say() {
        return returnStudentInformation();
    }

    // get和set方法
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public double getScore() {
        return score;
    }

    public void setScore(double score) {
        this.score = score;
    }
}
```

