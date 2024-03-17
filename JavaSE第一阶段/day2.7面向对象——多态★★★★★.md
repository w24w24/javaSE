# 一、为什么需要多态？

## 一、情景需求

需求：请编写一个程序，Master类中有一个feed(喂食)方法，可以完成主人给动物喂食，以当前`封装、继承`的知识，你可能会这样做：

（1）建立一个Food食物类，里面包含了食物名字：Fish、Bone、Rice....

（2）建立一个Animal动物类，里面包含了动物名字：Cat、Dog、Pig....

（3）建立一个Master喂食者类，里面包含了喂食者的名字：name.....

```java
package com.Extend;

// 主程序
public class RunTest {
    public static void main(String[] args) {
        Master master = new Master("jack");
        Cat cat = new Cat("洛必达");
        Fish fish = new Fish("小黄鱼");

        String res = master.feed(cat,fish);
        System.out.println(res);
    }
}

// Master类：喂食者
class Master {
    // 私有属性：name
    private String name;

    // 有参构造器
    public Master(String name) {
        this.name = name;
    }

    // get、set方法
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    // feed方法：喂食
    public String feed(Animal animal,Food food) {
        return "主人" + name + "给" + animal.getName() + "喂了" + food.getName();
    }
}

// Animal类：动物类
class Animal {
    // 私有属性：name
    private String name;

    // 有参构造器
    public Animal(String name) {
        this.name = name;
    }

    // get、set方法
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}

// Food类：食物类
class Food {
    // 私有属性：name
    private String name;

    // 有参构造器
    public Food(String name) {
        this.name = name;
    }

    // get、set方法
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}

// Dog类：继承了Animal类，是Animal的具体化
class Dog extends Animal{
    public Dog(String name) {
        super(name);
    }
}

// Cat类：继承了Animal类，是Animal的具体化
class Cat extends Animal {
    // 有参构造器
    public Cat(String name) {
        super(name);
    }
}

// Fish类：继承了Food类，是Food的具体化
class Fish extends Food {
    public Fish(String name) {
        super(name);
    }
}

// Bone类：继承了Food类，是Food的具体化
class Bone extends Food {
    public Bone(String name) {
        super(name);
    }
}
```

## 二、出现的问题

解析：使用上述方式去做这个功能需求，虽然可以完成，但是会出现以下问题：

（1）我们只例举了2个具体动物，假如动物有1000种呢？那么新建的类就会特别多，代码冗余度太高，不利于维护和管理

（2）还有就是每一种动物爱吃的食物不一样，1000种动物可能喜欢吃12000种食物，那么类和方法也会特别的多数，这个时候代码冗余度非常高，也不利于维护和管理

#### <span style="color:red">总结：代码冗余度太高，不利于维护和管理。那要怎么解决呢？【使用多态】</span>



# 二、多态？

介绍：多态【多种状态】，在java种，`方法`或`对象`具有多种状态，多态是面向对象的第三大特征之一，多态是建立在封装和继承的基础上的

## 一、多态的体现【方法的多态、对象的多态】

#### <span style="color:red">1、方法的多态【方法的重写、方法的重载中体现】</span>

解析：java中的方法有普通方法和构造方法。方法的重写和重载就体现多态

```
1、方法重写：发生在子类与父类中，方法名字必须相同，形参列表必须相同
2、方法重载：发生在本类中，方法名字必须相同，形参列表可以不同
```

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        A a = new A();
        B b = new B();
        // 根据对象不一样，调用的方法也不一样，虽然方法名字相同
        a.test();
        b.test();
        // 根据参数不一样，调用的方法也不一样，虽然方法名字相同
        a.sum(10,20);
        a.sum(10,20,30);
    }
}
class A {
    public void test() {
        System.out.println("我是A...");
    }

    // 方法重载
    public void sum(int num1,int num2){
        System.out.println("sum = " + (int)(num1 + num2));
    }
    public void sum(int num1,int num2,int num3) {
        System.out.println("sum = " + (int)(num1 + num2 + num3));
    }
}
class B extends A {
    // 方法的重写
    public void test() {
        System.out.println("我是B...");
    }
}
```

## <span style="color:red">2、对象的多态`【这是多态的核心】`★★★★★</span>

#### （1）编译类型看定义时 = 号 的左边，运行类型看 = 号 的右边

```java
// animal的编译类型是 = 号的左边。即Animal
// 运行类型是是 = 号的右边，即new Dog()
Animal animal = new Dog();
```

#### （2）一个对象的编译类型和运行类型可以不一致

```java
// 这是一般的写法：编译类型和运行类型都是一致的
Animal animal = new Animal();

// 但是多态中，编译类型和运行类型可以不一致
// 编译类型是：Animal，运行类型是：new Doig()
Animal animal = new Dog();
```

#### （3）编译类型在定义对象的时候就确定了，一旦确定，就不能改了

```java
// Animal就是编译类型，定义对象的时候，就确定了
Animal animal = new Dog();

// 想要更改编译类型Animal，是不行的
Dog animal = new Dog();
```

#### （4）运行类型是可以变化的

```java
// new Dog()就是运行类型，后续是可以改变的
Animal animal = new Dog();

// 想要更改运行类型new Dog()，是可以的
animal = new Cat();
// 虽然animal的运行类型变为了Cat，但是编译类型仍然是Animal
```

#### （5）代码示例：编译类型不可以改变，但是运行类型可以改变

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 编译类型是Animal，运行类型是Dog
        Animal animal = new Dog();
        animal.say(); // 输出：小狗叫唤...

        System.out.println("============");

        // 改变编译类型Animal的指向
        animal = new Cat();
        animal.say(); // 输出：小猫叫唤...
    }
}

class Animal {
    public void say() {
        System.out.println("动物叫唤....");
    }
}
class Cat extends Animal {
    public void say() {
        System.out.println("小猫叫唤...");
    }
}
class Dog extends Animal {
    public void say() {
        System.out.println("小狗叫唤....");
    }
}
```





