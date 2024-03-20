# 一、Java的动态绑定机制？★★★★★很重要★★★★★

## 一、java的重要特性：动态绑定机制【和多态相关】

概念：运行时绑定也叫做动态绑定，是一种调用对象方法的机制。java调用对象方法的时候，采用`动态绑定机制`

#### <span style="color:red">动态绑定机制就是：在多态的向上转型中，父类引用去调用子类方法，会先从运行类型中去查找，找得到，则直接执行，找不到，则又利用继承机制去找。如果在调用方法中又遇到调用方法，则又回到运行类型中开始查找</span>

（1）<span style="color:red">当调用对象的方法的时候，该方法会和该对象的内存地址（即运行类型）绑定</span>

```java
// 一、可以直接在运行类型中找到方法
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型
        Father father = new Son();
        System.out.println(father.sum()); // 输出：40
        System.out.println(father.sum1()); // 输出：30
    }
}
// 父类
class Father {
    public int i = 10;
    // sum
    public int sum() {
        return getI() + 10;
    }
    // sum1
    public int sum1() {
        return i + 10;
    }
    // getI
    public int getI() {
        return i;
    }
}

// 子类
class Son extends Father {
    public int i = 20;
    // sum
    public int sum() {
        return i + 20;
    }
    // sum1
    public int sum1() {
        return i + 10;
    }
    // getI
    public int getI() {
        return i;
    }
}
=======================================================
// 二、不能直接在运行类型中找到方法
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型
        Father father = new Son();
        // 1、father.sum()，运行类型是Son，所以先从Son类中开始找
        // 2、发现没有sum方法
        // 3、继承机制发挥作用，到father类中找sum方法
        // 4、有sum方法，则执行
        // 5、sum方法中又是getI方法，根据运行机制，又从Son类中找
        // 6、找到getI方法，则运行返回值(20) + 10 = 30
        System.out.println(father.sum()); // 输出：30
        System.out.println(father.sum1()); // 输出：30
    }
}
// 父类
class Father {
    public int i = 10;
    // sum
    public int sum() {
        return getI() + 10;
    }
    // sum1
    public int sum1() {
        return i + 10;
    }
    // getI
    public int getI() {
        return i;
    }
}

// 子类
class Son extends Father {
    public int i = 20;
    // sum1
    public int sum1() {
        return i + 10;
    }
    // getI
    public int getI() {
        return i;
    }
}
```

（2）<span style="color:red">当调用对象属性的时候，没有动态绑定机制，那里声明，就在哪里使用</span>

```java
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型
        Father father = new Son();
        System.out.println(father.sum()); // 输出：30
        System.out.println(father.sum1()); // 输出：30
    }
}
// 父类
class Father {
    public int i = 10;
    // sum
    // 1、在调用这个方法的时候，遇到了getI(),则又会与动态机制绑定，回到运行类型Son类中查找getI()
    // 2、因为在运行类型Son类中有getI，所以就会执行这里，由于属性不存在动态绑定机制，所以i的值就是Son类中的10，除非Son中没有i，则有启用继承机制去使用Father中的i
    public int sum() {
        return getI() + 10;
    }
    // sum1
    public int sum1() {
        return i + 10;
    }
    // getI
    public int getI() {
        return i;
    }
}

// 子类
class Son extends Father {
    public int i = 20;
    // sum1
    public int sum1() {
        return i + 10;
    }
    // getI
    public int getI() {
        return i;
    }
}
```



# 二、多态数组例题？【这个例题集合`封装` `继承` `多态` ，后面如果有任何疑问，都可以重写这一道题目来理解封装、继承、多态】

多态数组：数组的定义类型为父类类型，里面保存的实际元素类型是子类类型

需求：现在有一个继承结构如下，需要你使用多态数组的形式，将传入人物信息的say方法输出出来？

（1）有1个Person类作为父类，有Student、Teacher2个类作为子类继承了Person

（2）Person类中有一个被public修饰的say方法，用来输出人的信息：我是XX，年龄是XX岁

（3）Person中有private修饰的属性name、age

（4）Student类中有private修饰的属性score，Teacher类中有private修饰的属性salary

（5）Student子类中有专属方法study，Teacher子类中有专属方法teach，请访问它

```java
package com.Extend;

public class RunTest {
    public static void main(String[] args) {
        // Person类定义为多态数组
        Person[] person = new Person[5];
        // 将子类作为数组的元素
        person[0] = new Person("自定义名字",21);
        // 向上转型，子类被父类引用
        person[1] = new Student("Jack",24,89);
        person[2] = new Student("Tom",25,92);
        person[3] = new Teacher("Mr.wang",34,1500);
        person[4] = new Teacher("Mr.yang",28,14500);
        // 遍历输出say方法，注：这里只能输出Person的中方法。子类的专属方法是访问不到的
        // 为什么访问不到？解答：这是向上转型中的规定，子类中的专属方法，父类引用无法访问
        // 父类引用想要访问子类中的专属方法，必须先向下转型，即父类引用强制转为子类引用
        for (int i = 0; i < person.length; i++) {
            System.out.println(person[i].say());
            // 使用instanceof来判断类型
            // 如果运行类型为Student，则向下转型，然后调用Student中的study方法
            // 如果运行类型为Teacher，则向下转型，然后调用Teacher中的teach方法
            if(person[i] instanceof Student) {
                // 向下转型
                Student student = (Student)person[i];
                student.study();
                System.out.println('·');
            }else if(person[i] instanceof Teacher) {
                // 向下转型
                Teacher teacher = (Teacher)person[i];
                teacher.teach();
                System.out.println('·');
            } else if(person[i] != null) { // 当运行类型为Person的时候，什么都不做
                System.out.println(" ");
            }else {
                System.out.println("类型有误，请检查...");
            }
        }
    }
}

// Person
class Person {
    // 未初始化的属性
    private String name;
    private int age;
    // 构造方法初始化属性
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    // 提供get方法和set方法，让外部可以访问、设置私有属性
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

    // say方法，输出人物信息
    public String say() {
        return "我是" + getName() + "，年龄是" + getAge();
    }
}

// Student
class Student extends Person{
    // 未初始化的属性
    private double score;
    // 构造方法初始化属性
    public Student(String name, int age, double score) {
        super(name, age);
        this.score = score;
    }
    // 提供get方法和set方法，让外部可以访问、设置私有属性
    public double getScore() {
        return score;
    }
    public void setScore(double score) {
        this.score = score;
    }

    // 子类中的专属方法：study
    public void study() {
        System.out.println("我是" + getName() + "同学，" + "我正在上课~");
    }
}

// Teacher
class Teacher extends Person{
    // 未初始化的属性
    private double salary;
    // 构造方法初始化属性
    public Teacher(String name, int age, double salary) {
        super(name, age);
        this.salary = salary;
    }
    // 提供get方法和set方法，让外部可以访问、设置私有属性
    public double getSalary() {
        return salary;
    }
    public void setSalary(double salary) {
        this.salary = salary;
    }

    // 子类中的专属方法:teach
    public void teach() {
        System.out.println("我是" + getName() + "老师，" + "我正在授课~");
    }
}
```

