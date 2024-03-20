# 一、为什么需要多态——多态的出现？

## 一、情景需求

需求：请编写一个程序，Master类中有一个feed(喂食)方法，可以完成主人给动物喂食，以当前`封装、继承`的知识，你可能会这样做：

（1）建立一个Food食物类，里面包含了食物名字：Fish、Bone、Rice....

（2）建立一个Animal动物类，里面包含了动物名字：Cat、Dog、Pig....

（3）建立一个Master喂食者类，里面包含了喂食者的名字：name.....

```java
package com.Extend;

// 主程序
public class Polymorphic {
    public static void main(String[] args) {
        Master master = new Master("jack");
        // 狗的喂食
        Dog dog = new Dog("微微");
        Bone bone = new Bone("大棒骨");
        String dogFood = master.feed(dog,bone);
        System.out.println(dogFood);

        System.out.println("===========");

        // 猫的喂食
        Cat cat = new Cat("洛必达");
        Fish fish = new Fish("小黄鱼");
        String catFood = master.feed(cat,fish);
        System.out.println(catFood);
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

    // dog的feed方法
    public String feed(Dog dog,Bone bone) {
        return "主人" + name + "给" + dog.getName() + "喂了" + bone.getName();
    }
    // cat的feed方法
    public String feed(Cat cat,Fish fish) {
        return "主人" + name + "给" + cat.getName() + "喂了" + fish.getName();
    }
    // .....假如动物很多，这种feed方法就会很多，不利于代码的维护和管理
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



# 二、多态——体现在哪几方面？【2个方面：方法、对象】

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

#### <span style="color:red">现在使用多态来解决Master给Animal喂食的问题</span>

```java
package com.Extend;

// 主程序
public class Polymorphic {
    public static void main(String[] args) {
        Master master = new Master("jack");
        // 狗的喂食
        Dog dog = new Dog("微微");
        Bone bone = new Bone("大棒骨");
        master.feed(dog,bone);

        System.out.println("===========");

        // 猫的喂食
        Cat cat = new Cat("洛必达");
        Fish fish = new Fish("小黄鱼");
        master.feed(cat,fish);
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

    // 使用多态进行改造，摈弃原先每增加一个动物或者食物，就写一个feed方法的窘境
    public void feed(Animal animal, Food food) {
        // 这里使用了多态，因为多态中，父类可以接收和引用子类
        // Animal是Dog和Cat的父类，Food是Bone和Fish的父类
        // 所以，Animal和Food是可以接收和引用子类的
        // 使用了多态之后，即使后面增加再多的动物和食物，都不用更改feed的方法
        System.out.println("主人" + name + "给" + animal.getName() + "喂了" + food.getName());
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



# 三、多态——向上转型？【`父类引用`指向`子类对象`】

#### 一、多态的前提是：<span style="color:red">2个对象（类）存在继承关系</span>

#### 二、多态的向上转型？

1、向上转型的本质：<span style="color:red">`父类引用`指向`子类对象`</span>

2、语法：父类类型 引用名 = new 子类类型( )

```java
Animal animal = new Dog();
```

#### 三、向上转型的特点？

1、编译类型看左边，运行类型看右边

```java
// Animal 就是编译类型，因为它在 = 号的左边
// Dog() 就是运行类型，因为它在 = 号的右边
Animal animal = new Dog();
```

2、使用多态的向上转型，可以调用父类中的所有成员，但是需要遵守访问规则，即被private修饰的方法或者是属性，不可以在其它类中被访问

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 使用多态的向上转型：父类引用子类对象
        Father father = new Son();
        // 使用了多态的向上转型，可以使用父类中的方法
        father.run(); // 可使用
        father.sleep(); // 可使用
        father.eat(); // 不可使用，因为没有遵守访问范围，即使用了private修饰
    }
}
class Father {
    public void run() {
        System.out.println("我会跑~");
    }
    public void sleep() {
        System.out.println("我会睡觉");
    }
    private void eat() {
        System.out.println("我会吃饭");
    }
}
class Son extends Father {
    public void climb() {
        System.out.println("我会爬");
    }
}
```

3、不能调用子类中的特有成员，这里的特有成员是指：这个方法是子类专属的，父类没有。即使子类中不被private修饰，也不可以被调用【不能调用子类中的特殊成员是因为`在编译阶段是由javac去编译的，它只编译了Father，因为Father是编译类型，在Father中是没有子类中的特殊成员的。之后执行的时候又是由于java.exe去执行的，导致编译和运行分开了，所以不能调用子类中的特有成员`】

（1）当这个方法是子类中专属的方法的时候，即父类中没有这个方法，那么是不允许去调用的【如果想要调用子类专属则必须使用向下转型】

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 使用多态的向上转型：父类引用子类对象
        Father father = new Son();
        // 去访问子类中的特有成员
        father.climb(); // 不可以，因为climb是属于Son子类的特有成员
    }
}
class Father {
    public void run() {
        System.out.println("我会跑~");
    }
    public void sleep() {
        System.out.println("我会睡觉");
    }
    private void eat() {
        System.out.println("我会吃饭");
    }
}
class Son extends Father {
    public void climb() {
        System.out.println("我会爬");
    }
}
```

（2）当这个方法不是子类中专属的方法的时候，即父类中也有这个方法，构成了重写，是可以调用的。查找执行这个方法执行，从本类开始，如果有则执行，没有则往父类查找

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 使用多态的向上转型：父类引用子类对象
        Father father = new Son();
        // 当这个方法不是子类中专属的时候，就可以正常的调用
        father.show(); // 可以调用，因为show不是Son子类中专属的方法
    }
}
class Father {
    public void run() {
        System.out.println("我会跑~");
    }
    public void sleep() {
        System.out.println("我会睡觉");
    }
    private void eat() {
        System.out.println("我会吃饭");
    }
    public void show(){
        System.out.println("我是Father中show");
    }
}
class Son extends Father {
    public void climb() {
        System.out.println("我会爬");
    }
    public void show(){
        System.out.println("我是Son中show");
    }
}
```

4、最终的运行效果看子类（运行类型）的具体实现。这句话的意思是：当子类中的方法不是专属方法的时候，则执行子类中的方法，否则执行父类中的方法

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 使用多态的向上转型：父类引用子类对象
        Father father = new Son();
        // 子类中的方法不是专属方法，则执行子类中的方法
        father.show(); // 输出：我是Son中show【这就是最终效果看子类的具体实现】
    }
}
class Father {
    public void run() {
        System.out.println("我会跑~");
    }
    public void sleep() {
        System.out.println("我会睡觉");
    }
    private void eat() {
        System.out.println("我会吃饭");
    }
    public void show(){
        System.out.println("我是Father中show");
    }
}
class Son extends Father {
    public void climb() {
        System.out.println("我会爬");
    }
    public void show(){
        System.out.println("我是Son中show");
    }
}
```



# 四、多态——向下转型？【向下转型之前必须先向上转型】

1、语法：<span style="color:red">子类类型 引用名 = (子类类型) 父类引用</span>

```java
// 上面的父类引用是什么意思？
// 解析：上面的父类引用是“子类向上转型之后，被父类引用的名称”

// 1、这是main主方法，在这里面进行向上转型
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型：father就是父类引用
        Father father = new Son();
        
        // 向下转型：必须现有向上转型
        Son son = (Son) father;
    }
}
// 2、Father类
class Father {}
// 3、Son类
class Son {}
```

2、向下转型只能强转“父类的引用”，不能强转“父类的对象“

```java
// 这是强转“父类的引用”，是允许的
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型：father就是父类引用
        Father father = new Son();
        // 向下转型：必须现有向上转型
        Son son = (Son) father;
    }
}
class Father {}
class Son {}

// 这是强转“父类的对象”，是不允许的
public class Polymorphic {
    public static void main(String[] args) {
        // 实例化Father对象
        Father father = new Father();
        // 向下转型：直接强转父类的对象
        Son son = (Son) father;
    }
}
class Father {}
class Son {}
```

3、要求“父类的引用”必须指向的必须是向上转型中的“目标类型对象”

```java
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型：father指向的“目标类型对象是Son”
        Father father = new Son();
        
        // 向下转型：father指向的“目标类型对象是GrandSon”，和向上转型中的目标类型对象不一致
        GrandSon grandSon = (GrandSon) father;
        // 为什么要和向上转型中的目标对象一致？
        // 解析：因为father指向的对象是Son，在内存中存在了Son对象，但是GrandSon是不存在内存中的，所以去强转一个不存在的对象引用的时候，编译器就会报错
    }
}
// 2、Father类
class Father {}
// 3、Son类
class Son {}
// 4、GrandSon类
class GrandSon {}
```

4、当向下转型之后，就可以调用子类类型中的所有成员了，但是要遵循访问权限

```java
public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型
        Father father = new Son();
        // 没有向下转型，是无法调用子类中的方法的
        father.run(); // 报错
        
        // 向下转型
        Son son = (Son) father;
       // 因为我们已经使用了向下转型，所以可以调用子类中的方法了
        son.run(); // 输出：我是子类专属方法run
    }
}
class Father {
    public void cry() {
        System.out.println("我是父类的cry方法")
    }
}
class Son {
    public void run() {
        System.out.println("我是子类专属方法run")
    }
}
```



# 五、多态——属性重写问题？

1、属性没有重写之说，属性的值看编译类型

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型
        // 编译类型是：Father
        // 运行类型是：Son
        Father father = new Son();
        int res = father.count;
        System.out.println(res); // 输出：10
        // 为什么输出10？
        // 解析：因为在new Son()的时候，首先会将Son类中count值加载到常量池中，因为Son类继承了Father，所以Father的值也会被加载到常量池中。因为是属性值，不像是引用类型，使用的是地址引用，所以father.count指向的就是编译类型的count值
    }
}
class Father {
    public int count = 10;
}
class Son extends Father{
    public int count = 20;
}
```

2、instanceof 比较操作符，用于判断“对象的运行类型”是否为`某一个类的`XX类型，或者是否为XX类型的子类型

```java
package com.Extend;

public class Polymorphic {
    public static void main(String[] args) {
        // 向上转型
        Father father = new Son();
        Son son = new Son();
        // 判断Son是否是自己的类型或者是Father的子类型
        // 注意：instanceof的左边必须是class类，不允许是引用变量
        System.out.println(father instanceof Father); // true
        System.out.println(son instanceof Son); // true
    }
}
class Father {}
class Son extends Father{}
```

#### <span style="color:red">注意：使用instanceof的时候，语法是：</span>

```java
// instanceof的左边可以是对象引用，但是不能是class类。object就是对应引用，不是class类
// instanceof的右边边必须是类，不能是对象引用。class就是类
instanceof 运算符的语法是: object instanceof Class
    
// 1、错误用法
public class Polymorphic {
    public static void main(String[] args) {
        Object obj = null;
        Test test = new Test();
        // test是object对象引用，但是obj不是类，不符合instanceof语法
        System.out.println(test instanceof obj);
    }
}
class Test {}

// 正确用法
public class Polymorphic {
    public static void main(String[] args) {
        Object obj = null;
        Test test = new Test();
        // test是object对象引用，Object是顶级类，符合instanceof语法
        System.out.println(test instanceof Object);
    }
}
class Test {}
```



