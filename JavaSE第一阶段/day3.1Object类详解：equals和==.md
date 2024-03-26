# 一、Object类详解：==？【可以判断基本数据类型，又可以判断引用数据类型】

#### <span style="color:red">==是用来判断对象是否相等【这里的`是否相等`包含了值，或者是内存地址】</span>

解析：== 是一个运算符，可以用来判断对象`是否相等`，是什么类型就走什么下面两种方式

#### <span style="color:red">1、==既可以判断基本数据类型，又可以判断引用数据类型</span>

#### <span style="color:red">2、判断基本数据类型：判断的是值是否相等</span>

```java
int num1 = 10;
double num2 = 10.0;
// 即使类型不一样，但是值都是10，所以相等的
System.out.println(num1 == num2); // 输出：true
```

#### <span style="color:red">3、如果判断的是引用数据类型：判断的是地址是否相等【即判定是不是同一个对象的引用】</span>

```java
package com.Extend;

public class StaticMethods {
    public static void main(String[] args) {
        Father father = new Son();
        Father son = father;
        // 父类的引用是Son的内存地址，然后又将父类的引用地址给了son
        // 使用 == 来判断，则判断出father和son指向的地址都是同一个
        System.out.println(father == son);
    }
}
class Father {}
class Son extends Father{}
```



# 二、Object类讲解：equals？【只可以判断引用数据类型】

## <span style="color:red">equals默认就是比较对象的地址是否相同【这里只包含了内存地址】</span>

解析：equals是Object中的方法，只能判断引用数据类型

```java
Boolean res = "hell".equals("bye~");
System.out.println(res);
```

#### <span style="color:red">如何查看源码：</span>

1、ctrl + 鼠标点击想要查看的方法即可跳转到对应的jdk源码

2、将光标定位在想看的方法上，然后使用ctrl + B 即可查看

3、将鼠标定位到方法上，右键，点击 go to，再点击Declaration or Usages

## <span style='color:red'>一、equals默认判断的是地址是否相等，在子类中往往重写该方法，用于判断内容是否相等</span>

1、解析

```
这句话怎么理解？
例如：equals是Object的方法，String又是Object的子类，所以在判断字符串的时候，String类就会重写Object的equals方法
1、equals只可以用来判断内存地址引用是否相等，无法判断具体的内容
2、但是在使用String的时候，又想要判断具体的内容，所以Sting子类就重写了Object中的equals方法
```

2、equals在Object中的源码

```java
public boolean equals(Object obj) {
    return (this == obj);
}
// 这里为什么会这样写？
// 因为equals是直接判断内存地址的，使用==来判断，如果传入的obj和this当前对象的内存地址是相同的，则直接返回true，如果不相同，则直接返回false
```

3、在子类Integer中重写了Object中的equasl

```java
public boolean equals(Object obj) {
    if(obj instanceof Integer) {
        return value == ((Integer)obj).intValue();
    }
    return false;
}
// 为什么要在Integer中重写Object中的equals？
// 解析：因为Object中的equals不满足Integer中的使用，所以需要在子类中进行重写
```



# 三、==和equals比较？

## 一、==

解析：有2种判断方式，分别是判断对象的值和对象的内存地址

1、判断基本数据类型：直接对值进行判断【即使数据类型不一样，值一样都是true】

2、判断引用数据类型：直接比较对象的内存地址，如果指向的内存地址是同一个的话，则返回true，否则返回false

## 二、equals

解析：equals只用来判断引用数据类型，并且在子类中重写了Object中的equals【这里的重写是指：Object中的equals并不满足像String、Integer等子类中的数据判断，所以String和Integer会重写equals，用以满足判断】





# 四、equals例题？【重写equals方法】

需求：判断两个Person对象的内容是否相等【内容是指：传递进来的属性值】，如果两个Person对象的各个属性值都一样的，则返回true，否则返回false

```java
package com.Extend;

public class StaticMethods {
    public static void main(String[] args) {
        Person person1 = new Person("Jack",24,'男');
        Person person2 = new Person("Jack",24,'男');
        System.out.println(person1.equals(person2)); // true
    }
}
class Person { // 默认继承了Object的equals
    private String name;
    private int age;
    private char gender;
    public Person(String name, int age,char gender) {
        this.name = name;
        this.age = age;
        this.gender = gender;
        // set验证机制，不允许通过构造器绕过数据验证
        setName(name);
        setAge(age);
        setGender(gender);
    }
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
    public char getGender() {
        return gender;
    }
    public void setGender(char gender) {
        this.gender = gender;
    }

    // 重写Object中的equals：equals是boolean类型
    public boolean equals(Object obj) {
        // 判断：比较两个对象是不是同一对象【同一对象的意思是：是否指向同一个内存地址】，在直接返回true
        if(this == obj) {
            return true;
        }
        // 类型的判断
        if(obj instanceof Person) { // 前提是传递的都是person类型，我们才进行比较
            // 向下转型：将Object类型转换为Person类型
            // 为什么要向下转型？解答：因为要拿到子类Person中的属性
            // 只有向下转型了之后才可以拿到子类Person中的属性
            Person p = (Person)obj;
            return this.name.equals(p.name) && this.age == p.age && this.gender == p.gender;
        }
        // 传递的不是Person类型，则直接返回false
        return false;
    }
}
```

