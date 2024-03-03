# 一、面向对象——封装★★★★★

介绍：封装（encapsulation）就是把“抽象出的数据【属性】”和对“数据进行的操作【方法】”封装在一起。数据被保护在了内部，程序的其它部分只有通过“被授权的操作【方法】”，才能对数据进行操作

比喻：使用“遥控器”对“电视机”的操作就是典型的“封装”

#### <span style="color:red">为什么说使用遥控器对电视机的操作属于是典型的封装？</span>

解析：因为电视机内部是十分复杂的，我们在看电视切换节目的时候，只是通过了遥控器上的按钮，就实现了节目的切换。这看似是一个很平常的过程，但是在电视机内部却进行了很大的变化，只是用户并不关心内部是怎么实现的，只用关心节目是否被切换了

## 一、封装的好处？

1、实现了对细节的隐藏

```
为什么说实现了堆细节的隐藏？
解析：就像是使用遥控器切换节目，用户并不知道电视机内部在做什么，但是还是实现了换台，这就是隐藏了电视机执行换台的过程
例子：方法（连接数据库）<——调用方法（传入参数）
```

2、对数据进行验证，保证其安全和合理性

```java
// 为什么说封装可以对数据尽心验证，保证其合理性？
// 解析：下面是一个类，类中有人的年龄，假如不对数据进行验证的话，那么这个数据就不具有合理性

// 这是一个Perosn类,在这里面并没有对于age进行数据验证
class Person{
    String name;
    int age;
}

// 这是在main主方法中进行的操作，就可以改变数据的合理性
public class Test {
    public static void main(String[] args) {
        Person person = new Person();
        person.name = "jack";
        // 一个人的年龄是不可能是2024岁的，这就是没有使用数据验证，造成了数据的不合理
        person.age = 2024;
    }
}
```



# 二、如何实现封装/封装的实现步骤？

## <span style="color:red">一、封装的实现步骤（三步）</span>

#### 1、将属性进行私有化，即使用private来进行修饰【私有化之后就意味着无法被修改。但是外部想要修改和判断需要怎么办呢？使用set方法】

#### 2、提供一个公共的(public)公共的set方法，用于对属性的判断和赋值【即修改/设置数据属性值】

set语法格式如下：

```java
// set方法是用来对属性进行判断并且赋值的【即修改属性】
// 语法格式如下：
public void setXxx(参数类型 参数名) { // Xxx表示某个属性的名字
    // 可以在这里面加入数据验证的业务逻辑
    属性 = 参数名;
}
```

set语法格式解析以及为什么需要提供一个set方法：

```
因为我们将“属性”私有化了，所以会导致外部无法修改属性，但是我们的某些场景又需要去修改属性，所以需要向外部提供一个公共的(public)公共的set方法，用于对属性的判断和赋值【即修改】
```

#### 3、提供一个公共的(public)公共的get方法，用于获取属性值【即获取/读取数据属性值】

<span style="color:red">get方法主要是：为了可以向外暴露属性值，便于其它类可以通过get方法访问私有属性值</span>

get语法格式如下：

```java
// get方法是用来获取属性值的【即获取数据】
// 语法格式如下：
public 数据类型 getXxx() { // 权限判断，判断是否有权限访问该属性，Xxx表示某个属性的名字
    return xx;
}
```

get语法格式解析以及为什么需要提供一个get方法：

```
因为在开发中，有时候是需要去访问/获取数据属性的，但是数据属性被私有化了，所以是无法访问的。这个时候就需要提供一个get方法去供外部访问/获取数据属性，这样外部就可以得到数据属性，从而进行一些操作
```



# 三、封装快速入门？

需求：请写一个程序，这个程序包含人的姓名、年龄、工资

（1）人的名字是可以公开查看的，但是名字的长度要在2-6个字符之间

（2）人的年龄要私有化，并且要在1-120之间，超出则设置21岁

（3）人的薪水也是要私有化，并且不允许直接被外部查看

```java
package com.Test;

public class A {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("jack");
        person.setAge(24);
        person.setSalary(1500);

        // 输出信息
        String information = person.info();
        System.out.println(information);
    }
}

// Person类
class Person {
    // 属性
    public String name;
    private int age;
    private double salary;

    // 使用set和get方法将属性进行封装

    // name属性的set方法
    public void setName(String name) {
        // 加入数据的校验
        if(name.length() > 2 && name.length() < 6) {
            this.name = name;
        }else {
            System.out.println("输入的名字长度需要在2~6");
            this.name = "momoGsnmsa1255";
        }
    }
    // name的get方法
    public String getName() {
        return name;
    }

    // age的set方法
    public void setAge(int age) {
        // 对数据进行校验
        if(age > 1 && age < 120) { // 数据合理
            this.age = age;
        }else { // 数据不合理
            System.out.println("输入的年龄：" + age + "岁不符合");
            this.age = 21;
        }
    }
    // age的get方法
    public int getAge() {
        return age;
    }

    // salary的set方法
    public void setSalary(double salary) {
        this.salary = salary;
    }
    // salary的get方法
    public String getSalary(int password) {
        if(password == 2928) {
            return "你的工资是：" + salary;
        }else {
            return "您当前没有权限访问~";
        }
    }

    // 这个方法可以查看和返回数据
    public String info() {
        return "名字：" + name + "\n年龄：" + age + "\n薪水：" + salary;
    }
}
```

#### <span style="color:red">测试数据自己书写运行查看</span>



# 四、封装与构造器？

问题出现：在上述中，我们使用了set和get方法来对数据进行防护，因此外部类在访问的时候，就必须要经过set方法的验证。`但是，假如我使用构造器来创建对象属性，就可以避开set方法的防护机制了【就是数据验证】，如何解决呢？`

1、示例：使用构造器造成set方法中的数据防护机制【就是数据验证】

```java
package com.Test;

public class A {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("jack");
        person.setAge(30);
        person.setSalary(1500);
        // 直接输出信息
        String information = person.info();
        System.out.println(information);
        System.out.println("===========================");

        // 因为使用了构造器，所以传递参数时候就会绕过set的数据验证机制
        Person personConstructor = new Person("tomHelloWorld",2000,7000);
        String informationConstructor = personConstructor.info();
        System.out.println(informationConstructor);
    }
}

// Person类
class Person {
    // 属性
    public String name;
    private int age;
    private double salary;

    // 无参构造器：这个是为了创建对象的时候传递参数
    public Person() {}

    // 有参构造器：这个为了方便创建对象的时候直接传递参数
    public Person(String name, int age, double salary) {
        this.name = name;
        this.age = age;
        this.salary = salary;
    }


    // 使用set和get方法将属性进行封装

    // name属性的set方法
    public void setName(String name) {
        // 加入数据的校验
        if(name.length() > 2 && name.length() < 6) {
            this.name = name;
        }else {
            System.out.println("输入的名字长度需要在2~6");
            this.name = "momoGsnmsa1255";
        }
    }
    // name的get方法
    public String getName() {
        return name;
    }

    // age的set方法
    public void setAge(int age) {
        // 对数据进行校验
        if(age > 1 && age < 120) { // 数据合理
            this.age = age;
        }else { // 数据不合理
            System.out.println("输入的年龄：" + age + "岁不符合");
            this.age = 21;
        }
    }
    // age的get方法
    public int getAge() {
        return age;
    }

    // salary的set方法
    public void setSalary(double salary) {
        this.salary = salary;
    }
    // salary的get方法
    public String getSalary(int password) {
        if(password == 2928) {
            return "你的工资是：" + salary;
        }else {
            return "您当前没有权限访问~";
        }
    }

    // 这个方法可以查看和返回数据
    public String info() {
        return "名字：" + name + "\n年龄：" + age + "\n薪水：" + salary;
    }
}
```

2、问题解决：<span style="color:red">将set的数据验证方式写在构造器中，这样Jvm在调用构造器的时候依旧可以使用的set方法进行数据验证</span>

```java
package com.Test;

public class A {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("jack");
        person.setAge(30);
        person.setSalary(1500);
        // 直接输出信息
        String information = person.info();
        System.out.println(information);
        System.out.println("===========================");

        // 因为将set方法写在了构造器中，所以传递参数时候就不会绕过set的数据验证机制
        Person personConstructor = new Person("tomHelloWorld",2000,7000);
        String informationConstructor = personConstructor.info();
        System.out.println(informationConstructor);
    }
}

// Person类
class Person {
    // 属性
    public String name;
    private int age;
    private double salary;

    // 无参构造器：这个是为了创建对象的时候传递参数
    public Person() {}

    // 有参构造器：这个为了方便创建对象的时候直接传递参数
    public Person(String name, int age, double salary) {
        // 这里的this可以写，也可以不写，因为它们都是在同一个类中的
        setName(name);
        setAge(age);
        setSalary(salary);
    }


    // 使用set和get方法将属性进行封装

    // name属性的set方法
    public void setName(String name) {
        // 加入数据的校验
        if(name.length() > 2 && name.length() < 6) {
            this.name = name;
        }else {
            System.out.println("输入的名字长度需要在2~6");
            this.name = "momoGsnmsa1255";
        }
    }
    // name的get方法
    public String getName() {
        return name;
    }

    // age的set方法
    public void setAge(int age) {
        // 对数据进行校验
        if(age > 1 && age < 120) { // 数据合理
            this.age = age;
        }else { // 数据不合理
            System.out.println("输入的年龄：" + age + "岁不符合");
            this.age = 21;
        }
    }
    // age的get方法
    public int getAge() {
        return age;
    }

    // salary的set方法
    public void setSalary(double salary) {
        this.salary = salary;
    }
    // salary的get方法
    public String getSalary(int password) {
        if(password == 2928) {
            return "你的工资是：" + salary;
        }else {
            return "您当前没有权限访问~";
        }
    }

    // 这个方法可以查看和返回数据
    public String info() {
        return "名字：" + name + "\n年龄：" + age + "\n薪水：" + salary;
    }
}
```



# 五、封装课堂练习？

需求：创建一个程序，在其中定义两个类：AccountTest.java、Account.java

（1）Account类要求有以下属性：姓名（长度为2位、3位、4位）、余额（必须>20）、密码（必须是6位），如果不满足，则给出提示信息，并且给定默认值

（2）通过setXxx方法给Account赋值

（3）在AccountTest中进行测试

1、Account.java代码示例：

```java
package com.Test;

public class Account {
    // 属性
    private String name;
    private double balance;
    // password使用String是因为很多密码都是字符和数字组成的，所以是String
    private String password;

    // 创建一个”无参构造器“
    public Account() {}
    // 避免被使用构造器绕过set数据验证，将set方法写在”有参构造器中“
    public Account(String name,double balance,String password) {
        this.setName(name);
        this.setBalance(balance);
        this.setPassword(password);
    }

    // 使用set、get方法封装属性并且进行数据验证

    // name的set、get方法
    public void setName(String name) {
        // 名字的长度必须为2位/3位/4位
        if(name.length() == 2 || name.length() == 3 || name.length() == 4) {
            this.name = name;
        }else {
            this.name = "momo";
            System.out.println("名字长度不符合，已随机生成新名字：" + this.name);
        }
    }
    public String getName() {
        return this.name;
    }

    // balance的set、get方法
    public void setBalance(double balance) {
        if(balance > 20) {
            this.balance = balance;
        }else {
            this.balance = 0.0;
            System.out.println("余额不足，剩余：" + this.balance);
        }
    }
    public double getBalance() {
        return this.balance;
    }

    //password的set、get方法
    public void setPassword(String password) {
        if(password.length() == 6) {
            this.password = password;
        }else {
            this.password = "123456";
            System.out.println("密码必须是6位~");
        }
    }
    public String getPassword() {
        return this.password;
    }

    // 增加数据验证，只有身份符合，才有资格查数据
    public void showInfo() {
// 这里可以身份的校验，例如：只有身份是管理员、超级管理员、开发者才有权查看信息
//        if() {
//            System.out.println("姓名：" + this.name + "\n余额：" +
//                    this.balance + "\n密码：" + this.password);
//        } else {
//            ....
//        }
        System.out.println("姓名：" + this.name + "\n余额：" +
                this.balance + "\n密码：" + this.password);
    }
}
```

2、AccountTest.java代码示例：

```java
package com.Test;

public class AccountTest {
    public static void main(String[] args) {
        // 在这个类中创建Account类
        Account account = new Account();
        account.setName("jack");
        account.setBalance(7000);
        account.setPassword("292833");

        // 查看数据
        account.showInfo();
    }
}
```

#### <span style="color:red">为什么使用有参构造器的时候，必须写上无参构造器呢？</span>

解析：

（1）因为在Jvm在创建对象的时候，会自动生成“无参构造器”，这样就可以在创建对象时，不传递参数，之后通过`对象名.方法名/属性名`传递参数

（2）假如程序员手动提供了“有参构造器”，那么“无参构造器”就会被覆盖，这就是导致后续想要像（1）中使用无参构造传递参数无法使用

（3）所以在创建`有参构造器`的时候，建议必须带上`无参构造器`
