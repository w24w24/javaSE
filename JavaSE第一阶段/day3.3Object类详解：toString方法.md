# 一、Object类详解：toString方法？

基本介绍：

1、toString默认返回`全类名 + @ + 哈希值的16进制`

```java
// 全类名就是：包名 + 类名
// 源代码示意：
// getClass.getName：获取到全类名，即包名+类名
// Integer.toHexString：将哈希值转换为16进制的字符串
// hashCode：就是获取到哈希值
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}

// 实际例子：不重写toString方法
package com.Extend;
public class StaticMethods {
    public static void main(String[] args) {
        AA aa = new AA();
        System.out.println(aa.toString()); // com.Extend.AA@2dda6444
    }
}
class AA{}
```

2、子类往往重写toString方法，打印对象或是拼接对象时，都会自动调用该对象的toString方法，示例：

```java
package com.Extend;

public class StaticMethods {
    public static void main(String[] args) {
        Monster monster = new Monster("jack", "IT工程师", 15000);
        System.out.println(monster.toString());
    }
}
class Monster {
    private String name;
    private String job;
    private double salary;

    public Monster(String name, String job, double salary) {
        this.name = name;
        this.job = job;
        this.salary = salary;
        setName(name);
        setJob(job);
        setSalary(salary);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getJob() {
        return job;
    }

    public void setJob(String job) {
        this.job = job;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }

    // 重写toString方法
    @Override
    public String toString() {
        return "Monster{" +
                "name='" + name + '\'' +
                ", job='" + job + '\'' +
                ", salary=" + salary +
                '}';
    }
}
```

3、当直接输出一个对象的时候，toString会被默认的调用

```java
public class StaticMethods {
    public static void main(String[] args) {
        Monster monster = new Monster("jack", "IT工程师", 15000);
        System.out.println(monster); // 默认会调用Object的toString的方法
        // 直接输出：全类名 + @ + 哈希值的16进制
    }
}
```

