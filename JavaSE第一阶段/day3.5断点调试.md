# 一、断点调试？

#### 断点的意思是：程序执行到这一行就会停住，`之后`要执行的代码需要你手动去步进执行

场景需求：在开发中，新手程序员在查找错误的时候，这时候老程序员就会提示，可以使用断点调试，一步一步的看源码执行的过程，从而发现错误的存在，及时解决

<span style="color:red">重要提示：在断点的过程中，代码是处于运行状态的，也就是说，断点的时候是以代码的运行类型类执行的</span>

```java
Public class Test {
    public static void main(String[] args) {
        b B = new A();
        b.xx();
    }
}
class A {
    public void xx() {}
}
class B extends A {}
```

断点调试介绍：

1、断点调试是指在程序的某一行设置一个断点，调试时，`程序运行到这一行就会停住`，然后你就可以开始一步一步的往下调试，并且在调试的过程中，你可以清晰的看到各个变量的当前值，出错的话，调试到出错的代码行即显示错误，停下。进而分析找到这个bug

2、断点调试是程序员必须掌握的技能

3、断点调试也能帮助我们查看Java的底层源代码的执行过程，可以侧面提高java程序员的编程水平

#### 一张图认识调试的界面：

![image-20240325202521994](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20240325202521994.png)



# 二、debug快捷键？

1、F8：步进执行下一步代码

2、F9：直接执行完毕所有内容，然后跳出这个断点，转到下一个断点

3、F7：进入方法体内【假如你debug的方法存在另一个类中，通过F7，就可进入这个方法内】

4、Alt + shift + F7：强制进入方法体内部，是F7的加强版

5、shift + F8：跳出方法体内部，就像是返回上一层一样

# 三、自己动手体会debug？

1、正常执行，不会出错：foe循环演示

```java
package com.Extend;

public class StaticMethods {
    public static void main(String[] args) {
        // 在第五行打上断点
        // 断点的意思是：程序执行到这一行就会停住，之后要执行的代码需要你手动去步进执行
        int sum = 0;
        for(int i = 0; i < 5 ; i++) {
            sum += i;
            System.out.println("i=" + i);
            System.out.println("sum=" + sum);
        }
        System.out.println("程序退出了~");
    }
}

```

2、执行出错，如此使用debug查找错误：数组下标越界异常

```java
package com.Extend;

public class StaticMethods {
    public static void main(String[] args) {
        // 在第五行打上断点
        int[] arr = {1,2,3};
        for (int i = 0; i <= arr.length; i++) {
            System.out.println(arr[i]); // 在执行的最后，会报下标越界错误
        }
        System.out.println("我退出了~");
    }
}
```

3、使用快捷键F7【可能需要配置】或者是Alt + shift + F7进入源码的方法体内部，去查看java的设计者是怎样设计这个方法的

# 四、假如F7不进入方法体内，如何解决？

1、通过Alt + shift + F7，强制进入方法体内

2、配置IDEA，在Setting —Bild，Execution，Deploment—Debugger—Stepping的Do not step into the classes中的java. *、javax. *取消勾选



# 五、如何执行到下一个断点？

解析：使用快捷键F9

作用：直接执行完所有的这个段点后的所有代码，如果后面还有断点，则跳转到下一个断点。如果后面没有代码，则退出程序。<span style='color:red'>假如在debug中，突然想要再添加断点，也是可以的，不用退出控制台，重新打断点再执行。可以直接打断点执行也是支持的。</span><span style='color:blue'>在你自己的代码中你可以下断点，在jdk的原码中你也可以这样下断点</span>。如果点击了之后发现无法进入到下一个断点，说明这个业务逻辑不会与下一个断点产生关联，所以才无法进入下一个断点，这样久可以很好的知道这些代码之间是否有关联，是否会执行等...

1、演示代码

```java
package com.Extend;
import java.util.Arrays;

public class StaticMethods {
    public static void main(String[] args) {
        int arr[] = {-20, -2, -4, 1, 3, 50};
        Arrays.sort(arr); // 这里打上断点
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }

        int sum = 0; // 这里打上断点
        for (int i = 0; i < 5; i++) {
            sum += i;
            System.out.println("i=" + i);
            System.out.println("sum=" + sum);
        }
        System.out.println("程序退出~");
    }
}
```

#### <span style="color:red">这个快捷键很适合在开发中，想要查看线程之间协作关系的时候，很有用</span>



# 六、断点追踪对象创建时候是如何执行的？

