# 创建对象

## 一、对象的含义：

现实生活中，万物皆对象，对象是一个`具体的事物`【注：是具体的，不是笼统的、泛指的】，看得见、摸得着的实物，例如：一本书、一辆汽车、一个人可以是对象，一个数据库、一个与远程服务器的连接也可以是`对象`

例：

1. 明星（不是）
2. 周星驰（是）
3. 女朋友（不是）
4. 迪丽热巴（是）
5. 班主任（不是）
6. 咱们班班主任（是）
7. 苹果（不是）
8. 这个苹果（是）
9. 手机（不是）
10. pink老师的小米手机（是）
11. 游戏（不是）
12. 刺激战场（是）

![image-20221215124854372](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221215124854372.png)

## 1.JS中的属性：事物的外在特征，在对象中用属性来表示（名词）

## 2.JS中的方法：事物的行为（即它可以做什么），在对象中方法来表示（动词）



## 二、为什么需要对象？

解析：保存一个值时，可以使用变量，保存多个值（一组值）时，可以使用数组，如果要保存一个人的完整信息呢？

例如1：将张三疯的个人信息保存在数组中的方式为：

```javaScript
// 使用数组保存个人的信息：
var arr = ['张三疯','男',124,154];
```

但是你将这一组数组传输给其他人的时候，会出现歧义，不知道124 和154代表的数据是什么，怎么去解决呢？

解决例如1：JS中的表达结构更清晰，更强大，张三疯的个人信息在对象中的表达结构如下：

![image-20221215130043163](C:\Users\谭磊\AppData\Roaming\Typora\typora-user-images\image-20221215130043163.png)

