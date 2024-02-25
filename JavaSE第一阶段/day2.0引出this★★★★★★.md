# 一、引出this？

1、先看示例代码：

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Example example = new Example("jack",25);
        example.info(); // 输出：name是：jack   age是：25
    }
}

class Example {
    // 全局变量/属性
    String name;
    int age;

    // 构造器
    public Example(String pName,int pAge) {
        name = pName;
        age = pAge;
    }

    public void info() {
        System.out.println("name是：" + name + "\nage是：" + age);
    }
}
```

#### <span style="color:red">问题：在构造器中，我们传递的形式参数是pName、pAge，这样看起来好难看。这个时候我们想要让pName、pAge和类中的全局变量/属性name、age名字一致，如下：</span>

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Example example = new Example("jack",25);
        example.info(); // 输出：name是：null   age是：0
    }
}

class Example {
    // 全局变量/属性
    String name;
    int age;

    // 构造器
    public Example(String name,int age) {
        name = name;
        age = age;
    }

    public void info() {
        System.out.println("name是：" + name + "\nage是：" + age);
    }
}
```

#### <span style="color:red">又出现一个问题：那就是在调用info( )方法的时候，无法输出我们传递的实参了，这是为什么呢？</span>

解析：这是因为我们在main主方法中创建对象的时候，虽然传递了实参给到类中的构造方法，但是因为类中构造器的形式参数是name、age，而还是 name = name、age = age【`自己等于自己，没有影响到全局变量/属性，与全局变量/属性没有任何关系`】，这就导致了实参是没有给到全局变量/属性的，而且调用info( )方法的时候，使用的是全局的变量/属性，因为没有被更改，所以还是默认值，所以输出了null、0

## `总结：上述的问题可以使用这句话来概括：`<span style="color:red">构造方法的输入参数名字不是很友好，如果将pName、pAge改为name、age就好了。但是改变了之后我们会发现按照变量的作用域原则，name的值是null，age的值是0。怎么解决？——使用this</span>



# 二、this关键字？

java虚拟机会给每个对象都分配this，代表当前的对象。坦白的讲，要明白this不是一件容易的事情

比方：每个人都有眼睛、鼻子、嘴巴。小明指着自己的鼻子说：“这是我的鼻子”；小杨也指着自己的鼻子说：“这是我的鼻子”。这里两个人都指着自己的鼻子说，它们指的都是自己，this的指向也是这样，谁使用了就指向谁【这里的使用是指在创建对象的时候】

1、使用this解决输出null、0问题：

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Example example = new Example("jack",25);
        example.info(); // 输出：name是：jack   age是：25
    }
}

class Example {
    // 全局变量/属性
    String name;
    int age;

    // 构造器
    public Example(String name,int age) {
        // this.name就是当前对象的属性
        this.name = name;
        // this.age也是当前对象的属性
        this.age = age;
    }

    public void info() {
        System.out.println("name是：" + name + "\nage是：" + age);
    }
}
```

当前对象：当前对象就是在你创建好这个对象之后，谁在调用这个构造器，那么这个this就是哪一个对象

#### <span style="color:red">这里为什么使用了this就可以解决输出null、0问题呢？</span>

解析：因为我们在创建对象的时候，就调用了构造器，既然这个对象调用了构造器，那么this就指向这个对象



# 三、还是理解不了this？

1、再使用一个简单的代码例子来理解，如下：【无参构造设置属性】

```java
public class Test {
    public static void main(String[] args) {
         Dog dog = new Dog();
         // 当使用的是默认的无参构造器的时候，我们可以直接在类中给全局变量/属性赋

         // 或者是调用对象属性后赋值
        dog.name = "tom";
        dog.age = 21;
        System.out.println(dog.name); // 输出：tom
        System.out.println(dog.age); // 输出：21
    }
}

class Dog {
    // 全局变量/属性
    String name = "jack";
    int age = 24;
}
```

2、有参构造设置属性

```java
public class Test {
    public static void main(String[] args) {
        // 因为将构造器书写出来了，所以可以直接在创建对象时候传递参数
         Dog dog = new Dog("jack",24);
        System.out.println("dog.hashCode的地址是：" + dog.hashCode());
    }
}

class Dog {
    // 全局变量/属性
    String name;
    int age;

    public Dog(String name,int age) {
        // 这里的this指向的就是Dog对象自己
        // this.name相当于dog.name
        // this.age相当于dog.age
        this.name = name;
        this.age = age;
        System.out.println("this.hashCode的地址是：" + this.hashCode());
    }

    public void printInformation() {
        System.out.println(name + "\n" + age);
    }
}

// 那我怎么确定this.name和dog.name是同一个呢？
// 可以通过它们的内存地址来确定
// 但是很不幸，java是无法打印出地址的，这是因为java是运行在虚拟机上的
// 但是可以使用this.hashCode()这个方法来模拟内存地址
// 假如this.hashCode()和dog.hashCode()的模拟地址是一样的，说明this指向的就是dog这个对象
```

使用this.hashCode( )打印出来的模拟地址和dog.hashCode( )的模拟地址是一致的，所以证明了this的指向就是dog对象

#### <span style="color:red">简单说：哪一个对象调用了，那么这个this就指向谁</span>





# 四、this使用细节？

1、this关键字可以使用来访问本类的属性、方法、构造器

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象，因为是构造器，所以在创建对象的时候构造器就存在了，所以不需要手动去调用
        Example example = new Example();
    }
}

class Example {
    // 全局变量/属性
    String name = "jack";
    int age = 25;

    // 构造器
    public Example() {
        // 使用this来访问全局变量/属性name、age
        String name = this.name;
        int age = this.age;
        System.out.println("Example中的name是：" + name);
        System.out.println("Example中的age：" + age);

    }
}
```

2、this还可以用于区分当前类的属性和局部变量

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象的时候就会自动调用构造器，所以无需手动进行调用
        Example example = new Example();
    }
}

class Example {
    // 全局变量/属性
    String name = "jack";
    int age = 24;

    // 构造器
    public Example() {
        // 局部变量/局部属性
        String name = "tom";
        int age = 35;

        // 因为全局变量/属性和局部变量/属性名字都是name、age
        // 那么如何区分调用的是谁呢？【使用this】
        String usedName1 = this.name; // 因为使用了this，所以this指向了全局变量/属性
        int usedAge1 = this.age; // 同理
        System.out.println(usedName1); // 输出：jack
        System.out.println(usedAge1);  // 输出：24

        String usedName2 = ""; // 因为没有使用this，所以根据就近原则使用的是局部变量/属性
        usedName2 = name; // 同理
        int usedAge2 = 0;
        usedAge2 = age;
        System.out.println(usedName2); // 输出：tom
        System.out.println(usedAge2); // 输出：35
    }
}
```

3、访问成员方法的方式有2种：一种是直接访问，一种是通过this调用访问

<span style="color:red">使用this调用的语法：this.方法名字(参数列表)</span>

```java
public class Test {
    public static void main(String[] args) {

    }
}

// 需求：请在成员方法2中调用成员方法1【传统方式调用、this调用】
class Example {
    // 成员方法1
    public void fun1() {
        System.out.println("我是成员方法1");
    }
    // 成员方法2
    public void fun2() {
        System.out.println("我是成员方法2");
        // 传统的调用方式
        fun1();
        // this调用：this.方法名字(参数列表)
        this.fun1();
    }
}
```

4、使用this访问构造器语法：this(参数列表)

<span style="color:red">注意：使用this去访问构造器，只可以在构造器作用域内使用【即只可以在一个构造器中访问另外一个构造器，而且必须放在语句的第一个位置】</span>

```java
public class Test {
    public static void main(String[] args) {
        // 这样创建对象，jvm虚拟机是调用了构造器1
        Example example = new Example();
        // 这样创建对象，jvm虚拟机是调用了构造器2
        Example example1 = new Example("jack");
    }
}

// 需求：在构造器2中调用构造器1
class Example {
    // 构造器1
    public Example() {
        System.out.println("构造器1");
    }
    // 构造器2
    public Example(String name) {
        // 使用this进行调用，this语句必须放在第一个位置
        this();
        System.out.println("构造器2");
    }
}
```

5、this语句不允许在类的外部使用，只能在类定义的方法中使用【这个很好理解了，就是说，this不允许放置到类外边】



# 五、this练习题？

需求：定义Person类，里面有name、age属性，并提供了compareTo比较方法，用于判断是否和另外一个人相等，提供测试类TestPerson用于测试，名字和年龄完全一致，就返回true，否则返回false

个人完成代码如下：

```java
public class Test {
    public static void main(String[] args) {
        TestPerson testPerson = new TestPerson();
        boolean res = testPerson.returnStatue("jack",20);
        System.out.println(res);
    }
}

class Person {
    String name = "jack";
    int age = 24;

    public boolean compareTo(String name,int age) {
        boolean judge = false;
        if(this.name.equals(name) && this.age == age) {
            System.out.println("Person类和TestPerson类数据相同");
            judge = true;
        }else {
            System.out.println("Person类和TestPerson类数据不相同");
        }
        return judge;
    }
}

class TestPerson {
    public boolean returnStatue(String name,int age) {
        Person person = new Person();
        return person.compareTo(name,age);
    }
}
```



# 六、本章练习题？

1、需求：编写类A01，定义方法max，实现求某个double数组中的最大值，并且将这个值返回【自己书写的】

```java
// 需求：编写类A01，定义方法max，实现求某个double数组中的最大值，并且将这个值返回
class A01 {
    public double max(double[] arrays) {
        double max = arrays[0];
        for (int i = 1; i < arrays.length; i++) {
            if(arrays[i] > max) {
                max = arrays[i];
            }
        }
        return max;
    }
}

// public main类
public class Test {
    public static void main(String[] args) {
        A01 a01 = new A01();
        double[] arrays = {1.1,2.1,3.1,4.1,100.9,5.8,9.0,10.5};
        double res = a01.max(arrays);
        System.out.println(res); // 测试成功
    }
}
```

2、需求：编写类A02,定义方法find，实现"某字符串数组"中的元素查找。如果找到，则返回相应的索引；如果找不到，则返回-1

```java
// 需求：编写类A02,定义方法find，实现"某字符串数组"中的元素查找
// 1、如果找到，则返回相应的索引
// 2、如果找不到，则返回-1
public class Test {
    public static void main(String[] args) {
        A02 a02 = new A02();
        // 数据池
        String[] userInputString = {"丝袜","拖鞋","帽子","衬衫"};
        // 想要查找的字符串
        String searchString = "衬衫";
        int res = a02.find(userInputString,searchString);
        if(res == 0) {
            System.out.println("成功码值：" + res);
        }else {
            System.out.println("失败码值：" + res);
        }
    }
}

class A02 {
    public int find(String[] userInputString,String userWantToSearchString) {
        int judgeNumber = 1;
        // 开始查找
        for (int i = 0; i < userInputString.length; i++) { // i是控制次数
            if(userInputString[i].equals(userWantToSearchString)) {
                judgeNumber = 0;
                // 成功
                System.out.println("成功~已找到：" + userInputString[i]);
                System.out.println("索引值是：" + i);
                break;
            }else {
                judgeNumber = -1;
            }
        }
        // 失败
        if(judgeNumber == -1) {
            System.out.println("失败~未找到：" + userWantToSearchString);
        }
        return judgeNumber;
    }
}
```

3、需求：编写一book类，定义方法updatePrice，实现更改某本书的价格，具体如下：

（1）如果价格>150，则更改为150

（2）如果价格>100，更改为100，否则不变

<span style="color:red">一、常规写法</span>

```java
// 需求：编写一book类，定义方法updatePrice，实现更改某本书的价格，具体如下：
// 1、如果价格>150，则更改为150
// 2、如果价格>100，更改为100，否则不变
public class Test {
    public static void main(String[] args) {
        Book book = new Book();
        book.updatePrice("三国演义",50);
    }
}

class Book {
    String name = "";
    int price = 0;
    // 常规方式
    public void updatePrice(String name,int price) {
        if(price > 150) {
            this.name = name;
            this.price = 150;
            System.out.println(this.name + "的价格是：" + this.price);
        }else if(price > 100 && price < 150) {
            this.name = name;
            this.price = 100;
            System.out.println(this.name + "的价格是：" + this.price);
        }else {
            this.name = name;
            this.price = price;
            System.out.println(this.name + "的价格是：" + this.price);
        }
    }
}
```

<span style="color:red">二、构造器写法</span>

```java
// 需求：编写一book类，定义方法updatePrice，实现更改某本书的价格，具体如下：
// 1、如果价格>150，则更改为150
// 2、如果价格>100，更改为100，否则不变
public class Test {
    public static void main(String[] args) {
        Book book = new Book("三国演义",10);
    }
}

class Book {
    String name;
    int price;
    // 构造器写法
    public Book(String name,int price) {
        this.name = name;
        this.price = price;
        updatePrice();
    }
    // 这是updatePrice方法
    public void updatePrice() {
        if(this.price > 150) {
            this.price = 150;
            System.out.println(this.name + "的价格是：" + this.price);
        }else if(this.price < 150 && this.price > 100) {
            this.price = 100;
            System.out.println(this.name + "的价格是：" + this.price);
        }else {
            System.out.println(this.name + "的价格是：" + this.price);
        }
    }
}
```

4、需求：编写类A03，实现数组的复制功能copyArr，具体如下：输入旧数组，返回一个新数组，元素和旧数组一样

```java
import java.util.Arrays;
// 需求：编写类A03，实现数组的复制功能copyArr，具体如下：
// 输入旧数组，返回一个新数组，元素和旧数组一样
public class Test {
    public static void main(String[] args) {
        A03 a03 = new A03();
        String[] example = {"jack","code","tom","test"};
        String[] res = a03.copyArr(example);
        System.out.println("新数组：" + Arrays.toString(res));
        System.out.println("旧数组：" + Arrays.toString(example));
    }
}

class A03 {
    String[] newArrays;
    public String[] copyArr(String[] arrays) {
        // 给数组开空间
        newArrays = new String[arrays.length];
        // 给数组赋值
        for (int i = 0; i < arrays.length; i++) {
            newArrays[i] = arrays[i];
        }
        // 改变数组元素，测试和旧数组是否是独立的内存空间
        for (int i = 0; i < newArrays.length; i++) {
            newArrays[0] = "谭磊";
        }
        return newArrays;
    }
}
```

5、需求：定义一个圆类Circle，定义属性：半径

（1）提供计算”圆周长“功能的方法

（2）提供计算”圆面积“功能的方法

```java
// 需求：定义一个圆类Circle，定义属性：半径
// 1、提供计算”圆周长“功能的方法
// 2、提供计算”圆面积“功能的方法
public class Test {
    public static void main(String[] args) {
        Circle circle = new Circle();
        // 计算周长
        circle.circumference(5);
        // 计算面积
        circle.circleArea(2);
    }
}

class Circle {
    // 半径
    double radius;

    // 圆周长计算方法circumference
    public String circumference(double radius) {
        this.radius = radius;
        // 圆的周长公式：c = 2Π*r
        double circleCircumference = 2 * radius;
        System.out.println("圆的周长是：" + circleCircumference + "Π");
        return "圆的周长是：" + circleCircumference + "Π";
    }

    // 圆面积计算方法circleArea
    public String circleArea(double radius) {
        this.radius = radius;
        // 圆的面积公式：s = 2Π*r
        double circleArea = radius * radius;
        System.out.println("圆的周长是：" + circleArea + "Π");
        return "圆的面积是：" + circleArea + "Π";
    }
}
```

6、需求：创建一个Cale计算类

（1）在其中定义2个变量表示两个操作数，创建四个方法实现和、差、乘、商(要求除数为0的话要提示)

（2）创建两个对象分别进行测试

```java
// 需求：创建一个Cale计算类
// 1、在其中定义2个变量表示两个操作数，创建四个方法实现和、差、乘、商(要求除数为0的话要提示)
// 2、创建两个对象分别进行测试
public class Test {
    public static void main(String[] args) {
        Cale cale = new Cale(10,0);
        double res = cale.discuss();
        System.out.println(res);
    }
}
class Cale {
    double num1;
    double num2;
    // 为属性赋值
    public Cale(double num1,double num2){
        this.num1 = num1;
        this.num2 = num2;
    }
    // 求和
    public double sum() {
        return this.num1 + this.num2;
    }
    // 求差
    public double burden() {
        if(this.num1 < this.num2) {
            return this.num2 - this.num1;
        }else {
            return this.num1 - this.num2;
        }
    }
    // 求乘
    public double ride(){
        return this.num1 * this.num2;
    }
    // 求商
    public double discuss() {
        if(this.num2 == 0) {
            System.out.println("除数不允许为0哦~");
            return -1;
        }else {
            return this.num1 / this.num2;
        }
    }
}
```

7、需求：设计一个Dog类

（1）有名字、颜色、年龄3个属性【使用this进行属性赋值】

（2）定义输出方法show()显示其信息

（3）并创建对象进行测试

```java
// 需求：设计一个Dog类
// 1、有名字、颜色、年龄3个属性【使用this进行属性赋值】
// 2、定义输出方法show()显示其信息
// 3、并创建对象进行测试
public class Test {
    public static void main(String[] args) {
        Dog dog = new Dog("jack","白色",3);
    }
}

class Dog {
    // 全局属性
    String name;
    String color;
    int age;
    // 构造器
    public Dog(String name,String color,int age) {
        this.name = name;
        this.color = color;
        this.age = age;
        show();
    }
    // 方法
    public void show() {
        System.out.println("狗狗的名字是：" + this.name);
        System.out.println("狗狗的颜色是：" + this.color);
        System.out.println("狗狗的年龄是：" + this.age);
    }
}
```

