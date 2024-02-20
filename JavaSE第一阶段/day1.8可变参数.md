# 一、可变参数？

介绍：java允许将同一个类中多个`同名同功能`但参数个数不同的方法，封装成为一个方法。这个就可以通过可变参数实现

基本语法：

```java
访问修饰符 返回类型 方法名(数据类型... 形参名) {
    // 代码块
}
```

#### <span style="color:red">注意：可变参数的本质是数组的形式，所以在访问可变参数的时候，需要使用数组的形式来进行访问</span>

示例解析：int... 表示的是接收的是可变参数，类型是int，即接收多个参数【这里的多个是指：0—多，可以没有参数，也可以有多个参数】

```java
class HspMethod{
    public void sum(int... nums) {
    }
}
```

示例需求：书写一个方法，可以动态的接收main主方法中的实际参数，然后计算结果

```java
public class Test{
    public static void main(String[] args) {
        HspMethod hspMethod = new HspMethod();
        int res = hspMethod.sum(10,20,30);
        System.out.println(res);
    }
}
class HspMethod{
    public int sum(int... nums) {
        // 因为可变参数的本质是”数组“，所以使用数组的形式来进行访问
        System.out.println("元素个数是：" + nums.length);
        // 使用for循环遍历数组，然后进行元素值相加，即可得到sum值
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
        }
        return sum;
    }
}
```



# 二、可变参数的注意事项？

1、可变参数的实参可以为0个或任意多个【即可以一个参数也没有，也可以有多个】

2、可变参数的实参可以为数组

```java
public class Test{
    public static void main(String[] args) {
        HspMethod hspMethod = new HspMethod();
        // 这是一个数组
        int[] number = {1,2,3,4,5};
        // 在传递参数的时候，可以传递数组进入
        int res = hspMethod.sum(number);
        System.out.println(res);
    }
}
```

3、可变参数的本质就是数组【因此在访问的时候，可以使用for循环进行遍历，可以使用length去查看元素长度】

4、可变参数可以和普通类型的参数一起放在形参列表，但是必须保证可变参数在最后

```java
class HspMethod{
    public int sum(String res, double number, int... nums) {
        ....
    }
}
```

5、一形参列表中只允许出现一个可变参数【即可变参数只允许有一个】

```java
// 这是一种错误的写法，因为可变参数只运行出现一个
class HspMethod{
    public int sum(String... res, int... nums) {
        ....
    }
}
```

# 三、可变参数练习？

1、需求：有3个方法，分别实现返回姓名和两门课程成绩(总分)、实现返回姓名和三门课程成绩(总分)、实现返回姓名和五门课程成绩(总分)。封装成为一个可变参数的方法

类名是：HspMethods

方法名是：showScore

2、代码示例：

```java
public class Test {
    public static void main(String[] args) {
        HspMethod hspMethod = new HspMethod();
        // 为什么这里可以使用String来进行接收呢？
        // 解析：因为在方法中返回的是String，所以在这里可以使用String来进行接收
        String res = hspMethod.showScore("谭磊",90,80);
        System.out.println(res);
    }
}
class HspMethod {
    // 因为我们最终要返回出去的是“拼接的字符串”，所以这里使用的是String
    public String showScore(String name, double... scores) {
        double totalScores = 0;
        for (int i = 0; i < scores.length; i++) {
            totalScores += scores[i];
        }
        return name + scores.length + "门课的总成绩是：" + totalScores;
    }
}
```

