# 一、作用域？

#### 简单、跳过



# 二、作用域细节？

1、属性和局部变量可以重名，在访问的时候遵循就近原则

```java
public class Test {
    public static void main(String[] args) {
        Exercise exercise = new Exercise();
        exercise.test(); // 输出：king
    }
}
class Exercise {
    // 这是属性
    String name = "jack";
    public void test() {
        // 这是局部变量
        String name = "king";
        // 这里的name和外部的name重名了，但是根据就近原则，采用的是内部的name
        System.out.println(name); // 输出：king
    }
}
```

2、在同一个作用域中，比如同一个成员方法中，两个局部变量，不能重名

```java
public class Test {
    public static void main(String[] args) {
        Exercise exercise = new Exercise();
        exercise.test(); // 直接报错
    }
}
class Exercise {
    public void test() {
        // 因为在同一个成员方法中，两个局部变量不允许重名
        String name = "jack";
        String name = "king";
    }
}
```

3、属性的生命周期较长，伴随着对象的创建而创建，伴随着对象的销毁而销毁

```java
public class Test {
    public static void main(String[] args) {
        // 创建了对象
        Exercise exercise = new Exercise();
        String res = exercise.name;
        System.out.println(res); // 输出：jack

        // 代码执行完毕，Exercise对象销毁，name也被销毁
    }
}
class Exercise {
    // 这里只是定义了属性，并没有创建
    // 只有在main主方法中创建对象的时候，name才会被创建
    // 这个属性的生命周期是伴随着对象的创建而出现的
    // 一旦对象被销毁，这个属性也被销毁
    String name = "jack";
}
```

4、局部变量，生命周期短，伴随着代码块的执行而创建，伴随着代码块的结束而销毁，即局部变量的生命周期存在于一次方法的调用过程中

```java
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Exercise exercise = new Exercise();
        // 这里执行了test方法，所以name被创建
        exercise.test();
        // 当test方法执行完毕，name就会被销毁了
        // 注意：这里的name的生命周期并不是出现在创建对象的时候，而是出现在test方法执行的时候
        // 简而言之就是：局部变量的生命周期出现在成员方法执行的时候
    }
}
class Exercise {
    public void test() {
        String name = "jack";
        System.out.println(name);
    }
}
```

#### 5、作用域范围不同：3种跨类访问对象属性的方式

（1）全局变量/属性：可以被本类使用，或其它类使用（通过对象调用）

```java
// 1、在本类中使用全局变量/属性
class Exercise {
    // 这是全局变量/属性
    String name = "jack";
    // 这是本类中的test方法
    public void test() {
        // 都可以使用name全部变量/属性
        System.out.println(name);
    }
    // 这是本类中的exercise方法
    public void exercise() {
        // 都可以使用name全部变量/属性
        System.out.println(name);
    }
}

==============================================================================

// 2、在其它类中使用
public class Test {
    public static void main(String[] args) {
        // 创建对象
        Example example = new Example();
        example.test();

    }
}
// 2、在其它类中使用——————通过创建对象来进行引用
// 这是Exercise
class Exercise {
    // 这是全局变量/属性
    String name = "jack";
}

// 要在这一个类中使用Exercise中的name属性
class Example {
    public void test() {
        // 使用原理和在main主方法中使用方式一致：创建对象、通过对象进行调用
        Exercise exercise = new Exercise();
        String res = exercise.name;
        System.out.println(res); // 输出：jack
    }
}

==============================================================================

public class Test {
    public static void main(String[] args) {
        // 创建对象
        Example example = new Example();
        example.test();

        // 创建对象，将exercise当作参数传递给test1方法，即可访问Exercise类中的属性
        Exercise exercise = new Exercise();
        example.test1(exercise);
    }
}
// 2、在其它类中使用
// 这是Exercise
class Exercise {
    // 这是全局变量/属性
    String name = "jack";
}

// 要在这一个类中使用Exercise中的name属性
class Example {
    // 使用原理和在main主方法中使用方式一致：创建对象、通过对象进行调用
    public void test() {
        Exercise exercise = new Exercise();
        String res = exercise.name;
        System.out.println(res); // 输出：jack
    }

    // 直接传递一个对象p，名字无所谓，可以是s、t、e、f...
    public void test1(Exercise p) {
        String res = p.name;
        System.out.println(res);
    }
}
```

（2）局部变量：只能在本类中对应的方法中使用【这个很容易理解，就是作用域限制】



#### 6、修饰符不同：

（1）全局变量/属性：可以加修饰符

```java
class Example {
    // 因为是全局变量/属性，可以加修饰符【修饰符：public、private、protected】
    public String name = "jack";
}
```

（2）局部变量：不可以加修饰符

```java
class Example {
    // 因为是全局变量/属性，可以加修饰符【修饰符：public、private、protected】
    public String name = "jack";

    public void test() {
        // 因为是局部变量，不允许添加修饰符
        String name = "king";
    }
}
```



