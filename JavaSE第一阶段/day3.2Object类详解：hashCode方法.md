# 一、Object类详解：hashCode方法？

## 了解hashCode方法，只需要了解这6个点就可以了

1、hashCode方法是用来`提高具有哈希结构的容器的效率的`【后面会逐步了解的】

2、两个引用，如果指向的是同一个对象，则哈希值是一样的

```java
Father father = new Father();
Son son = new Father();
System.out.println(father == son); // true
// son引用和father引用指向的都是同一个对象
```

3、两个引用，如果指向的不是同一个对象，则哈希值是不一样的

```java
Father father = new Father();
Son son = new Son();
System.out.println(father == son); // false
// son引用和father引用指向的不是同一个对象
```

4、哈希值主要是根据内存地址号来的！虽然是根据内存地址号来的，但是你不能将哈希值等价于内存地址

```java
// 这句话的意思是：哈希值是根据对象的内存地址生成的整数
// 虽然是根据地址生成的整数，因为java代码是运行在虚拟机上的，这个生成的整数不是原始的内存地址号
// 所以你不能将这个整数当作内存地址号来看，只当作一个标识符
```

5、后面在集合中，如果需要使用hashCode值的话，会重写hashCode方法的【注意：在讲解集合的时候再学习】