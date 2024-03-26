# 一、面向对象——多态参数？★★★★★★★

## 一、什么是多态参数？

解析：多态参数就是，在定义方法的时候，使用的形参是父类类型。在调用方法的时候，传入的参数是子类类型

示例：主人喂食案例【经典的多态参数】★★★★★★

```java
// 主程序
public class Polymorphic {
    public static void main(String[] args) {
        Master master = new Master("jack");
        // 狗的喂食
        Dog dog = new Dog("微微");
        Bone bone = new Bone("大棒骨");
        // 这里就是多态参数：使用的时候传入的实参是子类类型
        master.feed(dog,bone);

        System.out.println("===========");

        // 猫的喂食
        Cat cat = new Cat("洛必达");
        Fish fish = new Fish("小黄鱼");
        // 这里就是多态参数：使用的时候传入的实参是子类类型
        master.feed(cat,fish);
    }
}

// Master类：喂食者
class Master {
    // 这里就是多态参数：定义形参的时候使用的是父类
    public void feed(Animal animal, Food food) {
        System.out.println("主人" + name + "给" + animal.getName() + "喂了" + food.getName());
    }
}

// Food类：食物类
class Food {
    private String name;
    public Food(String name) {
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
// Animal类：动物类
class Animal {
    private String name;
    public Animal(String name) {
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}

// 下面是具体的食物和动物类，继承了Food类和Animal类

// Bone类：继承了Food类，是Food的具体化
class Bone extends Food {
    public Bone(String name) {
        super(name);
    }
}
// Dog类：继承了Animal类
class Dog extends Animal{
    public Dog(String name) {
        super(name);
    }
}
```



# 二、面向对象——多态参数的应用？

需求：

（1）定义一个员工类Employee，这个类里包含姓名、月工资【被private修饰】，以及计算年工资getAnnual的方法。

（2）再定义两个子类，一个是普通员工OrdinaryEmployees、一个是经理Manager。员工类有自己的work方法，经理类多了奖金bonus属性和manage方法。普通员工类和经理类都要重写Emplloyee中的getAnnual方法

（3）添加一个测试类Teste，测试类中有一个方法showEmpAnnual(Employee e)，实现获取任何员工对象的年工资，并且在main主方法中调用该方法【e.getAnnual( )】

（4）测试类Teste中再添加一个方法getEmpIdentity，用来识别员工的身份，如果是普通员工，则调用work方法，如果是经理，则调用manage方法

一、Employee类

```java
package com.Extend;

public class Employee {
    private String name;
    private double monthSalary;
    public Employee () {}
    public Employee(String name,double monthSalary) {
        this.name = name;
        this.monthSalary = monthSalary;
        setName(name);
        setMonthSalary(monthSalary);
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public double getMonthSalary() {
        return monthSalary;
    }
    public void setMonthSalary(double monthSalary) {
        this.monthSalary = monthSalary;
    }

    public String getAnnual() {
        double allYearSalary = monthSalary * 12;
        return "年工资是：" + allYearSalary;
    }
}
```

二、OrdinaryEmployees类

```java
package com.Extend;

public class OrdinaryEmployees extends Employee {
    public OrdinaryEmployees(String name, double monthSalary) {
        super(name, monthSalary);
    }

    public void work() {
        System.out.println("我正在工作~");
    }

    public String getAnnual() {
        return super.getAnnual();
    }
}

```

三、Managers类

```java
package com.Extend;

public class Managers extends Employee {
    private double bonus;
    public Managers(String name, double monthSalary, double bonus) {
        super(name, monthSalary);
        this.bonus = bonus;
    }
    public double getBonus() {
        return bonus;
    }
    public void setBonus(double bonus) {
        this.bonus = bonus;
    }

    public void manage() {
        System.out.println("我正在管理员工~");
    }

    public String getAnnual() {
        double managerBonus = bonus * 12 + getMonthSalary() * 12;
        return "工资是：" + managerBonus;
    }
}

```

四、Test测试类

```java
package com.Extend;

import com.sun.org.apache.xpath.internal.operations.Or;

public class Test {
    public static void main(String[] args) {
        GetEmployeesSalary getEmployeesSalary = new GetEmployeesSalary();
        // 查看工资
        OrdinaryEmployees ordinaryEmployees = new OrdinaryEmployees("Jack",100);
        Managers managers = new Managers("Tom",200,10);
        getEmployeesSalary.getEmpAnnual(ordinaryEmployees);
        getEmployeesSalary.getEmpAnnual(managers);

        System.out.println("==================");

        // 查看员工身份
        // 这里就是多态参数的应用
        getEmployeesSalary.getEmpIdentity(ordinaryEmployees);
        getEmployeesSalary.getEmpIdentity(managers);
    }
}
class GetEmployeesSalary {
    public void getEmpAnnual(Employee e) {
        System.out.println(e.getAnnual());
    }
    public void getEmpIdentity(Employee e) {
        if(e instanceof OrdinaryEmployees) {
            // 向下转型
            ((OrdinaryEmployees) e).work();
        }else if(e instanceof Managers) {
            // 向下转型
            ((Managers) e).manage();
        }
    }
}
```



# 三、static静态方法中不能使用非静态方法？

问题出现：我新建了一个main主方法，我们都知道主方法main就是被static修饰的静态方法。这个情况就出现在这里，我在同一个类中、main方法外，定义了另一个方法noStaticMethods，竟然无法调用

1、代码示意

```java
package com.Extend;

public class StaticMethods {
    // 我是被static修饰的静态main方法
    public static void main(String[] args) {
        // 调用noStaticMethods()
        noStaticMethods(); // 不允许调用
    }
    // 我定义了一个不被static修饰的方法
    public void noStaticMethods() {
        System.out.println("我没有被static修饰~");
    }
}
```

#### <span style="color:red">问题：静态方法中无法调用非静态方法【即没有被static修饰的方法无法被static修饰的防方法调用】</span>

2、解决办法

<span style="color:red">（1）将没有被static修饰方法使用static修饰，这样就可以正常进行调用了</span>

```java
package com.Extend;

public class StaticMethods {
    // 我是被static修饰的静态main方法
    public static void main(String[] args) {
        // 调用noStaticMethods()
        noStaticMethods(); // 允许调用
    }
    // 使用static修饰的方法noStaticMethods
    public static void noStaticMethods() {
        System.out.println("我没有被static修饰~");
    }
}
```

<span style="color:red">（2）将所在的类实例化【即实例化自己】，通过类名引用来进行调用</span>

```java
package com.Extend;

public class StaticMethods {
    // 我是被static修饰的静态main方法
    public static void main(String[] args) {
        // 实例化本类【即实例化自己】
        StaticMethods staticMethods = new StaticMethods();

        // 通过类名引用来调用noStaticMethods()
        staticMethods.noStaticMethods(); // 允许调用
    }
    public void noStaticMethods() {
        System.out.println("我没有被static修饰~");
    }
}
```

