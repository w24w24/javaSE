# 一、Object类详解：finalize方法？

解析：finalize是一个方法，这个方法是用来释放资源的【资源是指：数据库连接、文件上传等】

```java
package com.Extend;

public class StaticMethods {
    public static void main(String[] args) {
        TestFinalizeClass testFinalizeClass = new TestFinalizeClass("Jack");
        // 使用finalize的前提是该对象没有任何的引用
        // 所以我们将testFinalizeClass置空
        // 就可以使用finalize方法了
        testFinalizeClass = null;
        // 这里不会直接去执行finalize方法，因为这个方法是由jvm自动调用的
        // 但是你可以手动进行调用，语法是：System.gc()
        // 虽然你手动调用了，但是不一定会触发，因为gc有自己的算法机制
        // 不会因为你调用就立即触发
        System.gc();
        System.out.println("main主程序退出了~");
    }
}
class TestFinalizeClass {
    private String name;
    public TestFinalizeClass(String name) {
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    // 重写finalize方法
    // Object中的finalize方法是什么都不做的
    // 只是为你提供了这种机制
    // 假如你想要使用finalize方法，你可以重写finalize方法
    @Override
    protected void finalize() throws Throwable {
        // 做一些资源的释放工作
        System.out.println("我是finalize方法：" + getName());
        System.out.println("我释放了资源~");
    }
}
```

#### <span style="color:red">1、当对象被回收的时候，系统会自动调用该对象的finalize方法。子类是可以重写该方法的，做一些资源释放的操作</span>

#### <span style="color:red">2、什么时候对象被回收？解答：当某个对象没有任何引用的时候，则jvm就认为该对象是一个垃圾对象，就会使用垃圾回收机制来销毁该对象，在销毁该对象之前，会先调用finalize方法</span>

#### <span style="color:red">3、垃圾回收机制的调用，是由垃圾回收系统来决定的【即有自己的GC算法，不是你一调用，它就立即执行的】，如果你想要立即执行，也就是主动出发垃圾回收算法机制，可以通过System.gc( )来主动触发</span>

#### 注意：在实际的开发中，几乎不会去重写fianlize方法，只是为了有应付面试而已