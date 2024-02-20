# 一、方法重载？

重载入门：你有没有发现在java中，重复使用system.out.println( )这个方法可以既可以打印字符、字符串、double数据、int数据、float数据、char数据...，使用的方法是相同的，但是传递的参数是不同的。使用相同的方法，但是传入的参数不同，这个就是“方法的重载”

介绍：java允许在同一个类中，多个同名方法的存在，但是要求“形参列表”不一致

示例：java自带的system.out.println( )方法

```java
public class Test {
    public static void main(String[] args) {
        // 重复的使用一个方法，但是传入的参数是不同的，这个就是方法的重载
        // 下面重复使用的方法是println，传入的参数是括号里面的，每一个都是不一样的
        System.out.println(10);
        System.out.println("你好");
        System.out.println('h');
        System.out.println(1.1);
        System.out.println(1.3F);
    }
}
```

# 二、重载快速入门示例？

需求：书写一个calculate方法，可以传递不同的参数，调用之后可以计算出相应的结果

```java
public class Test {
    public static void main(String[] args) {
        MyCalculator myCalculator = new MyCalculator();
        // 这里传入参数之后，系统会自己去类的方法中进行匹配
        System.out.println(myCalculator.calculate(10,20));
        System.out.println(myCalculator.calculate(1.1,20));
        System.out.println(myCalculator.calculate(10,20,10));
    }
}
// 书写一个calculate方法
class MyCalculator {
    // 计算两个int值
    public int calculate(int n1,int n2) {
        return n1 + n2;
    }
    // 计算一个int值 + double值
    public double calculate(int n1,double n2) {
        return n1 + n2;
    }
    // 计算一个double值 + int值
    public double calculate(double n1,int n2) {
        return n1 + n2;
    }
    // 计算3个int值
    public int calculate(int n1,int n2,int n3) {
        return n1 + n2 + n3;
    }
}
```

#### 注意：使用重载的时候，只是传递的参数是不同，方法的名字是相同的。因为有多个相同的方法，所以在传递参数的时候，系统会自动去匹配符合参数类型的方法进行执行

# 三、方法重载细节？

1、方法名：必须相同

```java
class MyCalculator {
    
    public int calculate(int n1,int n2) {
        return n1 + n2;
    }
    
    public double calculate(int n1,double n2) {
        return n1 + n2;
    }
    
}
```



2、形参列表：必须不同【形参类型或个数或顺序，至少有一样不同，参数名字无要求】

```java
class MyCalculator {
    
    public int calculate(int n1,int n2) {
        return n1 + n2;
    }
    
    public double calculate(int n1,double n2) {
        return n1 + n2;
    }
    
}
// 形式参数的数据类型、个顺、顺序必须不同，名字无所谓
```



3、返回类型：无要求

```java
class MyCalculator {
    
    public int calculate(int n1,int n2) {
        return n1 + n2;
    }
    
    public void calculate(int n1,double n2) {
        int res =  n1 + n2;
    }
    
}
// 这里的int类型和void类型是不会影响方法的重载的
```

# 四、重载练习？

需求：在类Methods中书写3个max方法，第一个方法传入2个int类型进行比较，将比较大的数据返回出去；第二个方法，传入2个double类型进行比较，将比较大的数据返回出去；第三个方法，传入3个double类型进行比较，将比较大的数据返回出去

```java
public class Test {
    public static void main(String[] args) {
        Methods methods = new Methods();
        System.out.println(methods.max(10,20));
        System.out.println(methods.max(10.0,80.0));
        System.out.println(methods.max(10.0,50.0,30.0));
    }
}
class Methods {
    public int max(int n1,int n2) {
        int maxNum = n1;
        if(n2 > maxNum) {
            maxNum = n2;
        }
        return maxNum;
    }
    public double max(double n1,double n2) {
        double maxNum = n1;
        if(n2 > maxNum) {
            maxNum = n2;
        }
        return maxNum;
    }
    public double max(double n1,double n2,double n3) {
        double maxNum = n1;
        if(n2 > maxNum) {
            maxNum = n2;
            if(n3 > maxNum) {
                maxNum = n3;
            }
        }
        return maxNum;
    }
}
// 可以简化了之后使用三元运算符号
```

