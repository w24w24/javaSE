# 一、面向对象——继承★★★★★

## 一、为什么需要继承？

需求：写三个类，一个类叫做pupil类、一个叫做graduate类、一个叫做testRun类

（1）pupil类中包含了3个属性：名字、年龄、成绩

（2）graduate类中也包含了3个属性：名字、年龄、成绩

（3）在testRun类中运行测试

#### <span style="color:red">使用这个例子的目的：是为了引出为什么需要使用继承</span>

1、这是pupil类

```java
package com.Test;

public class pupil {
    public String name;
    public int age;
    private double score;

    public void setScore(double score) {
        this.score = score;
    }
    public void testing() { // 这里是pupil考试科目
        System.out.println("大学生" + name + "正在考小学数学~");
    }
    public void showInfo() { // 这里是小学生信息
        System.out.println("学生名" + name + "年龄" + age + "成绩" + score);
    }
}
```

2、这是graduate类

```java
package com.Test;

public class graduate {
    public String name;
    public int age;
    private double score;

    public void setScore(double score) {
        this.score = score;
    }
    public void testing() { // 这里是graduate考试科目
        System.out.println("大学生" + name + "正在考大学数学~");
    }
    public void showInfo() { // 这里是大学生信息
        System.out.println("学生名" + name + "年龄" + age + "成绩" + score);
    }
}
```

3、这是testRun类

```java
import com.Test.pupil;
public class testRun {
    public static void main(String[] args) {
        pupil pupil =  new pupil();
        pupil.name = "jack";
        pupil.age = 12;
        pupil.testing();
        pupil.setScore(60);
        pupil.showInfo();

        System.out.println("=========");

        com.Test.graduate graduate =  new com.Test.graduate();
        pupil.name = "tom";
        pupil.age = 24;
        pupil.testing();
        pupil.setScore(100);
        pupil.showInfo();
    }
}
```

## 二、出现问题？

解析：我们发现在pupil和graduate中有很多重复的代码，一旦涉及到更改，就会有很大的工作量。这就导致了`代码的复用性`很差。那么如何解决呢？

#### <span style="color:red">使用继承，继承可以很好的避开重复代码的书写</span>



# 二、继承原理？

## 一、基本介绍？

解析：继承可以解决代码的复用性问题，让我们的编程更加接近人类的思维，当多个类存在相同的属性和方法的时候，可以从这些类中抽取出`父类`，在父类中定义这些相同的属性和方法，所有的子类不需要再重新定义这些属性和方法，只需要通过extends来声明继承父类即可

示意图：

![image-20240306201140867](https://github.com/w24w24/javaSE/blob/master/Images/%E7%BB%A7%E6%89%BF%E5%AD%90%E7%B1%BB%E4%B8%8E%E7%88%B6%E7%B1%BB%E5%85%B3%E7%B3%BB%E5%9B%BE%E3%80%81.png)



## 二、继承的基本语法？

```
class 子类 extends 父类 {
	...
}
```

1、子类会自动拥有父类定义的属性和方法【要看修饰符】

2、父类又叫做超类、基类

3、子类又叫做派生类



## 三、使用继承来解决Pupil和Graduate中代码冗余度太高问题？

1、父类：Extends，用来抽取Pupil和Graduate中重复的代码和属性

```java
package com.Extend;

public class Extends {
    // 共有的属性
    public String name;
    public int age;
    private double score;

    // 共有的方法
    public void setScore(double score) {
        this.score = score;
    }
    public void showInfo() { // 这里是小学生信息
        System.out.println("学生名" + name + "年龄" + age + "成绩" + score);
    }
}
```

2、子类：Pupil，用来继承和书写自己特有的属性和方法，以及继承Extends中的属性和方法

```java
package com.Extend;

public class Pupil extends Extends{
    // 特有的方法
    public void testing() {
        System.out.println("小学生" + name + "正在考小学数学~");
    }
}
```

3、子类：Graduate，用来继承和书写自己特有的属性和方法，以及继承Extends中的属性和方法

```java
package com.Extend;

public class Graduate extends Extends {
    // 特有的方法
    public void testing() {
        System.out.println("大学生" + name + "正在考小学数学~");
    }
}
```

4、TestRun测试运行类：在这里面测试和允许代码

```java
package com.Extend;

public class TestRun {
    public static void main(String[] args) {
        // Pupil对象
        Pupil pupil = new Pupil();
        pupil.name = "tom";
        pupil.setScore(60);
        pupil.age = 15;
        pupil.testing();
        pupil.showInfo();

        System.out.println("================");

        // Graduate对象
        Graduate graduate = new Graduate();
        graduate.name = "jack";
        graduate.setScore(90);
        graduate.age = 24;
        graduate.testing();
        graduate.showInfo();
    }
}
```



# 三、继承的细节和注意事项？【10点】

## <span style="color:red">一、子类继承了父类中的所有属性和方法【使用private修饰的属性和方法，要在父类中提供公共方法，保证子类可以访问】</span>

1、非私有的属性和方法可以在子类中直接进行访问

```
这句话的意思是：父类中的属性和方法，只要不被private修饰，都是可以在子类中进行访问的
```

2、但是私有属性和方法不能在子类中直接访问，必须要通过父类提供的公共的方法去访问

```
这句话的意思是：父类中的属性和方法，只要是被private修饰的，必须在父类中提供公共的方法，这样被private修饰的属性和方法才可以被子类访问
```

（1）Father中的属性和方法：分别有4种修饰符修饰的属性和方法

```java
package com.Extend;

public class Father {
    // 公共的属性
    public String name = "jack";
    int age = 24;
    protected double score = 150;
    private int salary = 7000;

    // 公共的方法
    public void testName() {
        System.out.println("我是Father中的测试名字");
    }
    void testAge() {
        System.out.println("我是Father中的测试年龄");
    }
    protected void testScore() {
        System.out.println("我是Father中的测试分数");
    }
    private void testSalary() {
        System.out.println("我是Father中的测试薪资");
    }

    // 由于salary是使用private修饰的，所以子类是无法访问的
    // 所以在这里提供公共的方法，让子类可以访问到这个方法
    public int getSalary() {
        return salary;
    }
    // 由于testSalary也是使用private修饰的，所以子类也是无访问的
    // 在这里也是需要提供公共的方法供子类访问
    public void callTestSalary() {
        testSalary();
    }

    // 访问属性
    public void accessProperties() {
        System.out.println(name);
        System.out.println(age);
        System.out.println(score);
        System.out.println(getSalary());
    }

    // 访问方法
    public void accessMethod() {
        // 可以访问Father中的不被private修饰属性
        // 由于salary是使用private修饰的，所以需要父类提供一个公共的方法才可以进行访问
        testAge();
        callTestSalary();
        testScore();
        testName();
    }
}
```

（2）Son1继承了Father中的所有属性和方法：

```java
package com.Extend;

public class Son1 extends Father {
    public void testSon1() {
        Father father = new Father();
        // 访问属性
        father.accessProperties();
        // 访问方法
        father.accessMethod();
    }
}
```

（3）Son2继承了Father中的所有属性和方法：

```java
package com.Extend;

public class Son2 extends Father {
    public void testSon2() {
        Father father = new Father();
        // 访问属性
        father.accessProperties();
        // 访问方法
        father.accessMethod();
    }
}
```

（4）TestRun中运行测试带代码

```java
package com.Extend;

public class TestRun {
    public static void main(String[] args) {
        Son1 son1 = new Son1();
        son1.testSon1();

        System.out.println("=============");

        Son2 son2 = new Son2();
        son2.testSon2();
    }
}
```



## <span style="color:red">二、子类必须调用父类的无参构造器，完成父类的初始化</span>

解析：我们都知道“无参构造器”，是java程序类自带的，即在实例化对象的时候Jvm虚拟机就会自动调用无参构造器。这种情况也是会出现在继承中的

示例：我们写了一父类，又写了一个子类，并且在子类中继承了父类。在实例化子类的时候，就会调用父类中的无参构造器，具体情况如下

1、这是父类Father

```java
package com.Extend;

public class Father {
    // 无参构造
    public Father() {
        System.out.println("我是Father的无参构造~");
    }
}
```

2、这是子类Son1

```java
package com.Extend;

public class Son1 extends Father {
    // 无参构造
    public Son1() {
        System.out.println("我是Son1的无参构造~");
    }
}
```

3、这是测试类TestRun

```java
package com.Extend;

public class Son1 extends Father {
    // 无参构造
    public Son1() {
        System.out.println("我是Son1的无参构造~");
    }
}
```

#### <span style="color:red">提问：为什么会出现这种情况呢？</span>

解析：这是因为java的机制造成的。为什么这么说？因为我们使用了继承extends。为什么使用了继承extends就会造成这种情况？因为在使用了继承extends之后，子类中就会拥有隐藏的super( )方法，这个方法是导致“在实例化子类对象的时候，会调用父类中无参构造器的根本因素”

在子类Son1中有这种情况：

```java
package com.Extend;

public class Son1 extends Father {
    // 无参构造
    public Son1() {
        // 即使你不写，这个super()方法也是隐式存在的
        // 那么这个super()方法存在的意义是什么？
        // 意义是：有时候我们需要借助这个方法产生的效果为”父类“中的属性赋值
        super(); // 默认调用父类的无参构造
        System.out.println("我是Son1的无参构造~");
    }
}
```

解析：上述中的super方法是隐式存在的，即使你不写，它也是存在的，这也是为什么在实例化子类的时候会调用父类中的无参构造器

<span style="color:red">super会在后面讲解，所以先暂时了解这么多</span>



## <span style="color:red">三、当创建子类对象的时候，不管使用子类的哪一个构造器，默认情况下总是会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中使用super去指定使用父类的哪个构造器完成对父类的初始化工，否则，编译器不会通过编译【一句话一句话的拆开理解】</span>

1、当创建子类对象的时候，不管使用子类的哪一个构造器，默认情况下总是会去调用父类的无参构造器

解析：这句话的意思是：当子类继承了父类，无论子类使用“无参构造器”还是“有参构造器”，在实例化的时候，都会去调用父类的无参构造器，注意是父类的无参构造

（1）这是Father中的无参构造器

```java
package com.Extend;

public class Father {
    // 这是Father中的无参构造器
    public Father() {
        System.out.println("我是Father的无参构造");
    }
}
```

（2）这是在Son1类中继承Father类

```java
package com.Extend;

public class Son1 extends Father {
    // 有参构造器
    public Son1(String name) {
        System.out.println("我是Son1的有参构造");
    }
    // 无参构造器
    public Son1() {
        System.out.println("我是Son1的无参构造器");
    }
}
```

（3）这是在TestRun类中运行测试

```java
package com.Extend;

public class TestRun {
    public static void main(String[] args) {
        // 实例化无参构造器
        Son1 son1 = new Son1();

        System.out.println("==================");

        // 实例化有参构造器
        Son1 son2 = new Son1("jack");

    }
}
```

解析：运行之后，我们发现，无论子类子类使用有参构造还是无参构造，都会去调用父类中的“无参构造”

#### <span style="color:red">提问：假如我在父类中使用有参构造器覆盖无参构造器呢？子类中也能正常运行吗？</span>

解答：假如在父类中使用有参构造器覆盖无参构造器，那么子类中就会报错。这是为什么？这是因为子类中无论使用什么构造器都会去调用父类中的无参构造器，但是无参构造器被你使用有参构造器覆盖了，就导致子类找不到父类中的无参构造器，那么编译器就会直接报错

#### <span style="color:red">如何解决父类中使用有参构造器覆盖无参构造器之后，导致子类中的构造器找不到父类中的无参构造器，编译器报错问题？</span>

解答：使用super方法

（1）这是Father中的有参构造器

```java
package com.Extend;

public class Father {
    // 这是Father中的有参构造器
    public Father(String name) {
        System.out.println("我是Father的有参构造");
    }
}
```

（2）这是Son1类中继承Father类

```java
package com.Extend;

public class Son1 extends Father {
    // 有参构造器
    public Son1(String name) {
        // 因Father中使用了有参构造器，所以Father中的无参构造器被覆盖了
        // 既然被覆盖了，那么这里的有参构造器就无法访问Father中的无参构造器
        // 想要访问父类中的构造器，就需要使用super方法
        super("jack");
        System.out.println("我是Son1的有参构造");
    }
    // 无参构造器
    public Son1() {
        // 这里也是同理
        super("tom",24);
        System.out.println("我是Son1的无参构造器");
    }
}
```

（3）TestRun类中测试

```java
package com.Extend;

public class TestRun {
    public static void main(String[] args) {
        // 实例化无参构造器
        Son1 son1 = new Son1();

        System.out.println("==================");

        // 实例化有参构造器
        Son1 son2 = new Son1("jack");
    }
}
```

#### <span style="color:red">super的作用就是：当父类中的无参构造器被有参构造器覆盖之后，在子类中使用super来指明你想使用父类中的哪一个构造器。这个指明是通过super( )方法中的参数传递来指明的</span>



## 四、如果希望指定去调用父类的某个构造器，则显式的调用一下，这个显式调用是使用super方法去调用



## 五、super在使用的时候，必须放在构造器的第一行。<span style="color:red">super只能在构造器中使用</span>



## 六、super和this都只能放置在构造器的第一行，因此这两个方法不能存在于同一个构造器

（1）这是Father类

```java
package com.Extend;

public class Father {
    // 这是Father中的2个有参构造器
    public Father(String name) {
        System.out.println("我是Father的有参构造1");
    }
    public Father(String name,int age) {
        System.out.println("我是Father的有参构造2");
    }
}
```

（2）这是Son1类

```java
package com.Extend;

public class Son1 extends Father {
    public Son1() {
        super("jack",24);
        this("tom"); // 直接报错
    }
    // 这里是可以被this调用的方法
    public Son1(String name) {
        super("jack");
        System.out.println("我是可以被this调用的方法" + name);
    }
}
```

（3）这是不允许的：因为this和super必须放置在构造器的首行，下面的形式放置在了同一个构造器，产生了冲突

```java
package com.Extend;

public class Son1 extends Father {
    // 无参构造器
    public Son1() {
        // 使用super来指向Father中的有参构造
        // super就是用来跨类指向的
        super("jack");
        this(24); // this.(24)的意思是：去调用本类的 Son1(int age)有参构造器
    }
    public Son1(int age) {
        super("jack",24);
        System.out.println("我的年龄是：" + age);
    }
}
```

解析：为什么会直接报错，因为实例化类的时候，都会去调用构造器，而且super必须放置在第一行，this也必须放置在第一行，二者都必须放置在第一行，所以就产生冲突了。所以就有一个结论：this和super不允许同时出现在统一个构造器中



## <span style="color:red">附加知识：进一步了解this和super</span>

1、this：用于在“本类构造器”中，指向或者是调用【当前类】的属性/方法。this可以有多个

```java
package com.Extend;

public class Son1 {
    public static void main(String[] args) {
        // 实例化对象
        Example example = new Example();
        // 访问并打印属性
        System.out.println(example.name);
        System.out.println(example.age);
        System.out.println(example.score);
    }
}

class Example {
    // 属性
    public String name;
    public int age;
    public double score;

    // 方法
    public void test(String name) {
        System.out.println("我的名字是：" + name);
    }

    // 构造器中使用this指向或者是访问本类的属性/方法
    public Example() {
        // 访问属性，并且赋值
        this.name = "jack";
        this.score = 98;
        this.age = 24;
        // 访问方法
        this.test("jack");
    }
}
```

2、super是用来跨类访问或者指向父类构造器的。一个构造器中只允许有1个super

```java
package com.Extend;

public class Son1 extends Father {
    // 无参构造器
    public Son1() {
        // 使用super来指向Father中的有参构造
        // super就是用来跨类指向的
        super("jack");
    }
}
```



## 七、java所有类都是Object类的子类，即Object是所有类的基类/超类

1、演示：在继承之后使用ctrl + H查看继承关系

![image-20240311190954519](https://github.com/w24w24/javaSE/blob/master/Images/Object%E4%B8%8E%E5%85%B6%E5%AE%83%E7%B1%BB%E7%9A%84%E5%85%B3%E7%B3%BB.png)

## 八、父类构造器的调用不限于直接父类，将会一直往上追溯到Object类（顶级父类）【也就是说，程序的执行会从顶级父类开始执行】

<span style="color:red">提问：为什么会一直往上追溯，这是因为涉及到了继承，一旦涉及到继承，构造器中就会有默认super的存在，super就会逐步的往上查找</span>



## 九、子类只能继承一个父类（指直接继承），即java是单继承机制

1、这是Father类

```java
package com.Extend;

public class Father {
    public Father() {
        System.out.println("我是Father类，我继承了Object");
    }
}
```

2、这是Father2类

```java
package com.Extend;

public class Father2 {
    public Father() {
        System.out.println("我是Father类，我继承了Object");
    }
}
```



3、这是Son1类

```java
package com.Extend;

public class Son1 extends Father {
    public Son1() {
        System.out.println("我是Son1类，我继承了Father类");
    }
}
```

#### <span style="color:red">一旦Son1继承了Father，就不能再直接使用extends去继承Father2类了</span>

<span style="color:red">提问：如果想要在Son1中使用Father2中的属性/方法，该怎么去使用呢？</span>

解析：将Father当作一个中转站，去继承Father2，这样就Son1就可以使用Father2中的属性/方法了



## 十、不能滥用继承，子类和父类之间必须满足is-a的逻辑关系【is-a：即XXX是XXX的关系】

```java
// Person is a Music？
Person Music
// Perosn和Music之间可以进行继承吗？
Person extends Music; // 这样是不合理的


// Animal
Cat extends Animal; // 这样是合理的
```





# <span style="color:red">四、继承的本质分析？★★★★★</span>

案例：我们来看一个案例分析当子类继承了父类之后，在创建子类对象的时候，内存中到底发生了什么？【提示：当子类对象创建好之后，建立“查找的关系”】

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        // 在new这一刻到底发生了什么？
        Son son = new Son();

        // 访问
        System.out.println(son.name); // 输出：大头儿子
        System.out.println(son.age); // 输出：45
    }
}

class Grandpa {
    String name = "大头爷爷";
    String hobby = "旅行";
}
class Father extends Grandpa {
    String name = "大头爸爸";
    int age = 45;
}
class Son extends Father {
    String name = "大头儿子";
}
```

内存图示例：

![image-20240311211449080](https://github.com/w24w24/javaSE/blob/master/Images/%E7%BB%A7%E6%89%BF%E7%9A%84%E5%86%85%E5%AD%98%E6%9C%BA%E5%88%B6%E7%A4%BA%E6%84%8F%E5%9B%BE.png)

#### <span style="color:red">解析：</span>

我们创建完了Grandpa类、Father类、Son类，然后在main主方法中实例化Son对象，所有的东西都几种在new的时候。

第一步：

当我们创建Son对象的时候，首先会在内存的方法区中加载类信息【类信息是指类的属性】，第一个加载的就是Son的类信息，因为涉及了继承，所以在Son中会有super方法，这个方法会自动地往上进行“查找”【查找地意思是：再往上看是否还有类的属性可以被加载到方法区中】，于是又找到了Father，于是又加载了Father。又因为Father继承了Grandpa类，所以在Father中也含有super方法，所以又会向上寻找，于是又找到了Grandpa，于是又将Grandpa中的信息加载到方法区中。因为所有的类都是Object的子类，即所有的类都继承了Object，所以在Grandpa中还有一个super方法，于是又找到了Object这个顶级对象，但是里面什么也没有输出，所以Object就没有任何的属性加载到方法区中

第二步：

类信息加载完毕之后，就开始初始化属性值。先在堆中开辟3个空间来存储属性值【3个空间是因为有3个类，因此有3个类的属性需要加载】，当3个类的信息都加载完毕之后，就将这个地址给到son

#### <span style="color:red">访问：</span>

在访问的时候，java的Jvm虚拟机会从自己开始查找需要访问的属性值，如果有，并且可以正常访问【这里正常访问的意思是没有被private修饰等情况】，就直接访问到，如果没有，则向上查找，如果有，并且可以访问到，那就访问，这样一直循环直到查找到Object，如果查找了之后都没有，则报错

#### 1、当属性被private修饰的时候，无法访问时，提供一个公共的get方法

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        // 在new这一刻到底发生了什么？
        Son son = new Son();

        // 访问
        System.out.println(son.name); // 输出：大头儿子
        System.out.println(son.getAge()); // 输出：45
    }
}

class Grandpa {
    String name = "大头爷爷";
    String hobby = "旅行";
}
class Father extends Grandpa {
    String name = "大头爸爸";
    private int age = 45;

    // 当属性被private修饰的时候，这个属性的访问范围只在本类中
    // 为了保证这个类可以被正常访问，需要提供一个公共的get方法
    public int getAge() {
        return age;
    }
}
class Son extends Father {
    String name = "大头儿子";
}
```

#### 2、继承中在查找访问属性的时候，不能跨类访问【比如：在son中访问age，在Father中的age被private修饰了，也没有提供public的get方法，但是Grandpa中又有public修饰的age属性，son不能跳过Father中的age去访问Grandpa中的age】

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        // 在new这一刻到底发生了什么？
        Son son = new Son();

        // 访问
        System.out.println(son.name); // 输出：大头儿子
        System.out.println(son.age); // 报错
    }
}

class Grandpa {
    String name = "大头爷爷";
    String hobby = "旅行";
    // son不能跳过Father中的age来访问这里的age
    public int age = 80;
}
class Father extends Grandpa {
    String name = "大头爸爸";
    private int age = 45;
}
class Son extends Father {
    String name = "大头儿子";
}

// 简而言之就是：在查找访问的时候，不能被堵到，一旦被堵到，直接报错
```



# 五、this和super的区别？【都必须在构造器内部使用】可能有错误，因为是自己想的，具体请看super那一章

#### 一、this

解析：this只能在本类的构造器中使用，作用范围也只能是本类，可以使用this来访问本类中的属性、方法、构造器

<span style="color:red">1、this只允许访问本类中的属性、方法、构造器。但是在访问构造器的时候，必须放置在第一行</span>

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {

    }
}
class Example {
    // 这是属性
    public String name;
    public int age;
    // 这是方法
    public void test() {
        System.out.println("我是方法");
    }
    // 这是有参构造器
    public Example(String name) {
        System.out.println(name);
    }

    // 在构造器中使用this来访问本类中的属性、方法、其它构造器
    public Example() {
        this("tom"); // 这个this必须放置在第一行，因为是要访问构造器
        this.name = "jack";
        this.age = 24;
    }
}
```

2、this的语法是：this.和this( )

```java
this.
this()
```

3、this大部分情况下是可以省略的，但是有时候是不可以省略的

```java
// 这是不可以省略的情况：当使用来区分局部变量和实例变量的时候是不可以省略的
Public void setName(String name){
	this.name = name;
}
```

## <span style="color:red">一般在构造方法中就访问构造方法，不去访问属性、实例方法</span>

#### 二、super

解析：super使用在子类中，用来跨类访问父类中的构造器

<span style="color:red">1、super用来跨类访问父类中的属性、方法、构造器。在访问构造器的时候，必须放置在第一行</span>

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        Son son = new Son();
        // 访问父类中的方法
        son.test();
        // 访问父类中的属性
        System.out.println(son.name);
        System.out.println(son.age);
    }
}
// 父类
class Father {
    // 属性
    public String name;
    public int age;
    // 方法
    public void test() {
        System.out.println("我是方法~");
    }
    // 有参构造器
    public Father(String name) {
        System.out.println("我是名字是：" + name);
    }
}
// 子类
// 继承父类
class Son extends Father {
    public Son() {
        // 使用super去访问父类中的构造器，在访问构造器的时候必须放置在第一行
        super("jack");
        // 虽然也可以在这里访问属性，但是我们不在这里进行访问
        // 一般构造方法就去访问构造方法，不访问其它的
    }
}
```

2、super的语法是：super.和super( )

```java
super.
super()
```



#### 总结：

1、this指向当前对象的自己，super指向当前对象的父类。【不需要死脑筋理解】所以this的东西比super多，super是this的一部分

2、this( )和super( )都只能出现在构造方法的第一行，所以this( )和super( )方法不能共存。当一个类的构造方法没有this( )，也没有super( )时，Jvm虚拟机默认有super( )方法

#### <span style="color:red">3、this( )在构造方法中调用本类中的其它构造方法；super( )是在当前对象的构造方法中去调用父类的构造方法</span>



# 六、打印电脑参数

需求：编写Computer类，包含cpu、内存、硬盘等属性，getDetails用于返回Computer的详细信息

（1）编写子类PC，继承Computer，添加特有属性【品牌brand】

（2）编写NotePad子类，继承Computer类，添加特有属性color

（3）编写Test类，在main方法中创建PC和NotePad对象，分别给对象中的特有属性赋值，以及从Computer类继承的属性赋值，并使用方法的打印输出信息

```java
package com.Extend;

public class Test {
    public static void main(String[] args) {
        PC pc = new PC("AMD",24,1024,"华硕");
        System.out.println(pc.printComputerInformation_PC());
        System.out.println("=========================");
        NotePad notePad = new NotePad("intel",16,10240,"联想");
        System.out.println(notePad.printComputerInformation_NotePad());
    }
}
class Computer {
    // 为了数据的安全，所以在类中的属性要使用private来修饰
    private String cpu;
    private int memory;
    private int hardDisk;

    // 构造器给属性赋值
    public Computer(String cpu,int memory,int hardDisk) {
        this.cpu = cpu;
        this.memory = memory;
        this.hardDisk = hardDisk;
    }

    // getDetails返回Computer的详细信息
    public String getDetails() {
        return "电脑cpu：" + cpu + "\n电脑memory：" + memory + "\n电脑hardDisk：" + hardDisk;
    }

    // 这是getter、setter方法
    public String getCpu() {
        return cpu;
    }

    public void setCpu(String cpu) {
        this.cpu = cpu;
    }

    public int getMemory() {
        return memory;
    }

    public void setMemory(int memory) {
        this.memory = memory;
    }

    public int getHardDisk() {
        return hardDisk;
    }

    public void setHardDisk(int hardDisk) {
        this.hardDisk = hardDisk;
    }
}


class PC extends Computer {
    private String brand;
    // 构造器给属性赋值
    public PC(String cpu, int memory, int hardDisk, String brand) {
        super(cpu, memory, hardDisk); // 这里调用了父类中的有参构造器
        this.brand = brand;
    }

    // 输出电脑的信息
    public String printComputerInformation_PC() {
        return getDetails() + "\n电脑品牌：" + brand;
    }

    // getter、setter方法
    public String getBrand() {
        return brand;
    }
    public void setBrand(String brand) {
        this.brand = brand;
    }
}


class NotePad extends Computer {
    private String color;
    // 构造器给属性赋值
    public NotePad(String cpu,int memory,int hardDisk,String color) {
        super(cpu,memory,hardDisk);
        this.color = color;
    }

    // 输出电脑的信息
    public String printComputerInformation_NotePad() {
        return getDetails() + "\n电脑颜色：" + color;
    }

    // getter、setter方法

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}
```





