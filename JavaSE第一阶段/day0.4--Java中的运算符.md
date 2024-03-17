目录：

1、运算符介绍

2、算数运算符

3、关系运算符

4、逻辑运算符

5、赋值运算符

6、三元运算符

7、运算符优先级

8、二进制★★★★

9、位运算符★★★★

# 一、运算符介绍?

运算符是一种特殊的符号，用以表示数据的运算、赋值和比较

1、算数运算符

2、赋值运算符

3、关系运算符【比较运算符】

4、逻辑运算符

5、位运算符【需要二进制基础】

7、三元运算符

# 二、算术运算符？

算数运算符是对数值类型的变量进行运算的，在java程序中使用得非常多

![image-20231023220329635](https://github.com/w24w24/javaSE/blob/master/Images/%E7%AE%97%E6%95%B0%E8%BF%90%E7%AE%97%E7%AC%A6.png)

重点讲解除法/、模%、加加++



# 三、java中除法/的使用？

注意：java中除法的使用技巧在于数据的类型【整数和整数相除，只可以得到整数！！浮点数和整数相除，得到的是浮点数！！】

```java
public class Test{
    public static void main(String[] args) {
        System.out.println(10 / 4); // 输出：2【因为10和4都是int类型，得到的也必须是Int类型】
        system.out.println(10.0 / 4); // 输出：2.5【因为10.0是double类型是，所以可以取到小数点后面的数字】
        double d = 10 / 4; // 输出：2.0，因为10和4都是int类型，但是前面使用了double来进行接收，所以是double类型
    }
}
```



# 四、取模%？

公式：a % b = a - a / b * b【所有的取模都是运用这一个公式进行计算】

```java
public class Test {
    public static void main(String[] args) {
        System.out.println(10 % 3 ); // 输出：1
        System.out.println(-10 % 3 ); // 输出：-1
        System.out.println(10 % -3); // 输出：1
    }
}
```

#### 注意：假如 a%b 中的a是小数，则在使用公式的时候有一个强制转换的过程，也就是：a%b = a-(int)a/b*b

```java
a % b = a - (int)a / b * b;
也就是说：先将a强制转换为整数，再进行运算
// 示例：
public class BinaryChange {
    public static void main(String[] args) {
        double i = -10.5%3;
        // 因为a是小数，所以使用公式：a%b = a-(int)a/b*b
        // -10.5%3 = -10.5-(int)-10/3*3 = -10.5+9 = -1.5
        System.out.println(i);
    }
}
```

但是还要注意：结果的-1.5只是近似-1.5的数，并不是精确的-1.5【有小数参运算，得到的结果是近似值！！这是因为计算机存储是二进制存储，存储位数有限，存储小数时会无线趋近但不等同，所以最后只能得到近似值】

示例：

```java
public class BinaryChange {
    public static void main(String[] args) {
        double i = -10.4%3;
        // 因为a是小数，所以使用公式：a%b = a-(int)a/b*b
        System.out.println(i); // 输出：-1.4000000000000004
    }
}
```



# 五、自增 ++？

1、作为独立的语句使用：前 ++ 和后 ++ 是完全一样的

```java
++i = i + 1;
i++ = i + 1; 
```

2、和表达式子结合使用：前 ++ 和 后 ++ 是不一样的

```java
// 后置加加：先赋值，再自增—— a = b; b = b + 1
int b = 10;
int a = b++;
System.out.println(a); // 输出：10
System.out.println(b); // 输出：11
0
// 前置加加：先自增，再赋值——b = b + 1;a = b
int b = 10;
int a = ++b;
System.out.println(a); // 输出：11
System.out.println(b); // 输出：11
```



# 六、面试题目？`临时变量`的使用

1、案例：

```java
public class Test {
    public static void main(String[] args) {
        int i = 1;
        i = i++;
        System.out.println(i); // 输出：1
    }
}
```

#### 虽然在前面我们已经讲解到了在`表达式中`的前置加加和后置加加的规则

```2
后置加加：
i++：先赋值，在进行加1操作
例子：
int i = 1;
int b = i++;
System.out.println(i); // 输出：2
System.out.println(b); // 输出：1

前置加加：
++i：先加1，再进行赋值操作
int i = 1;
int b = ++1;
System.out.println(i); // 输出：2
System.out.println(b); // 输出：2
```

但是，在这一道题目中，上述的规则是不完全遵循的，因为它不是赋值给其它变量，而是赋值给到自己，所以这个地方不太一样

```java
int i = 1;
i = i++; // 因为是赋值给自己，所以需要使用到临时变量
System.out.println(i); // 输出：1

// 思路解析；
// 第一步：使用临时变量进行接收这个变量
temp = i; // 因为这里是后置加加，所以是不需要进行+1运算的
// 第二步：然后再进行运算，i + 1
i = i + 1;
// 第三步：运算完毕之后，再将原来赋值给临时变量的值取到给i
i = temp;
```

#### 简要理解：不要将i看作是自己，看作是其它的变量，输出的也是其它变量，最后输出的值就是临时变量temp的值



2、案例：

```java
public class Test {
    public static void main(String[] args) {
        int i = 1;
        i = ++i;
        System.out.println(i); // 输出：2
    }
}
```

解析：这题和上面的题目是一样的，但是不同点在于不再是后置加加了，而是前置加加

```java
int i = 1;
i = ++i; // 也是需要使用到临时变量的，因为同样是赋值给自己

// 第一步：进行运算，因为是前置加加
i = i+1; // 因为这里是前置加加，所以需要直接进行运算
// 第二步：使用临时变量来进行接收
temp = i;
// 第三步：再将临时变量赋值给到i即可
i = temp;
```

# 七、编程思维解决问题？

1、需求：假如还有59天放假，问：合xxx星期零xx天?

```
第一步：给出需求，如上面的需求
```

```
第二步：思路分析【不要一上来就开始写代码】
（1）使用 int 变量 days 来保存天数
（2）星期：一个星期是 7 天，days / 7 即可得到星期数
（3）零xx天：day % 7 即可得到
```

```
第三步：写代码
```

```java
// 实际代码示例：
public class Test {
	public static void main(String[] args) {
		int days = 59;
		int week = days / 7;
		int day = days % week;
		System.out.println("还有" + week + "个星期" + "零" + day + "天"); // 输出: 还有8个星期零3天
	}
}
```

2、需求：定义一个变量保存华氏温度 234.5，华氏温度转换摄氏温度的公式是：

5 / 9*（华氏温度 - 32），请求出华氏温度对应的摄氏温度。

```
第一步：明确需求，如上
```

```
第二步：思路分析【不要一上来就写代码】
（1）解析需求：既然是温度，肯定会有小数的，所以使用double来进行接收
（2）公式的理解，注意，这个需要结合我们的java语言的特性进行使用，不可以对于给出的公式生搬硬套
（3）确认无误之后，开始写需求
```

```
第三步：开始书写代码
```

```java
// 实际代码示例
public class Test {
	public static void main(String[] args) {
		double huaTemperature = 234.5;
		// 华氏温度转摄氏温度公式：5/9*（摄氏温度-100）
		double sheTemperature = 5 / 9*(huaTemperature - 32);
		System.out.println("华氏温度对应的摄氏温度是" + sheTemperature); // 输出：0.0
	}
}

// 解析：这里为什么会输出 0.0？我也按照公式套用了呀！为什么输出的是0.0呢？
```

#### 解析：为什么按照需求给出的业务逻辑会输出不符合逻辑的结果？

这是因为在给出的公式中间，我们是生搬硬套去使用的，并没有结合java语言的特性去进行使用，所以输出了0.0！【java语言中的算数运算符特性，int类型与int类型运算，得到的只能是int类型，所以在5 / 9 的时候，得到的就是一个整数0，所以最终的计算结果就是0.0】

```java
// 改进公式：因为直接使用需求公式，不结合java语言的特性，就会出现数据异常的情况
public class Test {
	public static void main(String[] args) {
		double huaTemperature = 234.5;
		// 华氏温度转摄氏温度公式：5/9*（摄氏温度-100）
		double sheTemperature = 5.0 / 9*(huaTemperature - 100); // 这里只需要把公式转换为double类型，那么java在进行计算的时候，就会自动保留精度，那么后续的数据计算也就不会出现问题！！
		System.out.println("华氏温度对应的摄氏温度是" + sheTemperature);// 输出：正常
	}
}
```



# 八、关系运算符号【比较运算符—relationalOperator】？

介绍：

1、关系运算符的结果都是boolean型，也就是要么是true，要么是false

2、关系表达式【使用关系运算符表达的式子就是关系表达式】，经常使用在if结构中，或者是循环结构中

3、以下是关系运算符概览：

![image-20231116193103288](https://github.com/w24w24/javaSE/blob/master/Images/%E5%85%B3%E7%B3%BB%E8%BF%90%E7%AE%97%E7%AC%A6.png)



```java
public class Test {
	public static void main(String[] args) {
		// 注意：这只是在演示基础，在实际开发中，请不要将变量书写为a、b，因为代码的可读性不高,求他开发人员无法理解这种操作
		int a = 9;
		int b = 8;
		System.out.println(a > b);
		System.out.println(a < b);
		System.out.println(a >= b);
		System.out.println(a <= b);
		System.out.println(a == b);
		System.out.println(a != b);
		boolean flag = a > b;
	}
}
```



# 九、逻辑运算符？【与就是并且的意思，或就是或者的意思！！！与是全真为真，或是一真为真】

介绍：逻辑运算符用于连接多个条件（多个关系表达式），最终的结果是一个boolean值

分为两组进行学习：因为只笼统的进行学习的话，就会混乱

1、符号介绍：

（1）短路与：&&，短路或：||，取反：！

（2）逻辑与：&，逻辑或：|，逻辑异或：^

2、逻辑运算符规则介绍：

（1）短路：

与：&&【a&&b：只有当a和b都为true时，结果才为true】；

或：||【a||b：只要a和b中有一个为true，则结果就为true】；

取反：！【!a：当a为true时候，则结果为false】；

（2）逻辑：

与：&【a&b：只有当a和b都为ture时候，结果才为true】；

或：|【a|b：只要a和b中有一个为true，那么结果就为true】；

异或：^【a^b：当a和b不同时，结果为true，否则为false】；



# 十、逻辑与&、短路与&&的区别？

#### 一、思考：既然逻辑与&，短路与&&之间除了符号不同，判断的结果都是相同的，那么他们二者的区别是什么？

区别：&和&&

1、对于短路与&&而言：如果第一个条件为false，那么后面的条件就不会再进行判断

```java
public class LogicOperator {
	public static void main[String[] args] {
		int a = 4;
		int b = 9;
		// 对于短路与&&：如果第一个条件为false，后面的条件就不会再进行判断和运算了
		if(a < 1 && ++b < 50) {
			System.out.println("ok3000");
		}
		System.out.println("a = " + a + "b = " + b); // 输出：a=4，b=9
	}
}
```

2、对于逻辑与&而言：即使第一个条件为false，之后的条件也是会执行的

```java
public class LogicOperator {
	public static void main[String[] args] {
		int a = 4;
		int b = 9;
		// 对于逻辑与&：即使第一个条件为false，后面的条件依旧会进行判断和运算
		if(a < 1 && ++b < 50) {
			System.out.println("ok3000");
		}
		System.out.println("a = " + a + "b = " + b); // 输出：a=4，b=10
	}
}
```

3、在实际的开发中，我们使用的是短路与&&，因为其执行起来的效率是高于逻辑与&的

# 十一、逻辑或|、短路或||的区别？

区别：

（1）短路或||：如果第一个条件为true，则第二个条件就不会进行判断了，最终的结果就为true，效率高

（2）逻辑与|：不管第一个条件是否为true，之后的条件都是会进行判断的，因此效率低

（3）因此在实际的开发中，我们使用得最多得就是短路或

```java
// 短路或||：只要一个条件为真，就不会再往下执行了
public class LogicOperator {
	public static void main(String[] args) {
		int a = 4;
		int b = 9;
		if(a > 1 || ++b > 4) {
			System.out.println("ok3000");
		}
		System.out.println("a=" + a + "b=" + b); 
        // 输出：a=4, b=9
	}
}
```

```java
// 逻辑或|：不论哪一个条件为真，都会将所有的条件执行完
public class LogicOperator {
	public static void main(String[] args) {
		int a = 4;
		int b = 9;
		if(a > 1 | ++b > 4) {
			System.out.println("ok3000");
		}
		System.out.println("a=" + a + "b=" + b); 
        // 输出：a=4, b=10
	}
}
```

# 十三、取反！、异或^？

取反！：将true变为false，false变为true

逻辑异或^：两个表达式不同为true，相同为false

```java
// 取反！：
public class InverseOperator {
	public static void main(String[] args) {
		System.out.println(60 > 20); // 输出：true
		System.out.println(!(60 > 20)); // 输出：fasle
	}
}
```

```java
// 逻辑异或^:
// 1、为假的情况：
public class InverseOperator {
	public static void main(String[] args) {
		boolean b = (20 > 10) ^ (50 > 30);
		System.out.println("b是：" + b); // 输出：false
	}
}

// 2、为真的情况：
public class InverseOperator {
	public static void main(String[] args) {
		boolean b = (20 > 10) ^ (50 < 30);
		System.out.println("b是：" + b); // 输出：true
	}
}
```



# 十四、典型例题？【赋值等号=、比较符号==的区别】

示例：

```java
public class Test {
	public static void main(String[] args) {
		boolean x = true;
		boolean y = false;
		short z = 46;
		if((z++ ==46)&&(y = true)) {
			z++;
		}
		if((x = false) || (++z == 49)) {
			z++;
		}
		System.out.println("z=" + z); // 50
}
```

解析：在这道题目里面的主要区别是：

1、赋值等号和比较等号所要表达的意思是不一致的

2、我们的短路符和逻辑符号所代表的含义也是不一致的

```java
public class Test {
	public static void main(String[] args) {
		boolean x = true;
		boolean y = false;
		short z = 46;
        // 这里的z先和46比较，因为是相同的，所以为true，然后再+1，z=47；之后就是将y赋值为true；那么整体就是true，所以里面的z++就会执行，所以z=48
		if((z++ ==46)&&(y = true)) {
			z++;
		}
        // 然后就是将x赋值为false【注意：赋值不影响语句的执行】，因为在上述中z=48，所以在这里的++z就会等于49，所以++z==49为true，那么最终的结果就是true，因为是短路与，所以只有遇到true才会终端执行，所以里面的语句就会执行，最终的结果就是50
		if((x = false) || (++z == 49)) {
			z++;
		}
		System.out.println("z=" + z); // 输出：50
}
```



# 十五、赋值运算符【AssignOPerator】？

赋值运算符的分类：

1、基本赋值运算符：=

2、复合赋值运算符：+=、-=、 *=、/=、%=等，重点讲解的是+=，其它的使用是一个道理

```java
a += b 等价于 a = a + b;
a -= b 等价于 a = a - b;
```

赋值运算符的特点：

1、运算顺序从右往左

```java
int num = a + b + c
```

2、赋值运算符号的左边，只能是变量；右边可以是变量、表达式、常量值

```java
int num = 20;
int num2 = 787*34-10;
int num3 = a;
```

3、复合赋值运算符等价于下面的效果

```java
a += 3 等价于 a = a + 3;
其它的以此类推即可
```

4、复合赋值运算符会进行`类型转换`

```java
// 例子：
byte b = 2; b += 3; b++;

// 解析：
由于b的数据类型是byte，而且b += 3 等价于b = b + 3！要知道，在数据类型转化的阶段，b + 3 最终的数据类型会是int类型，但是因为是在复合赋值运算符下的 b += 3，会自动进行数据类型的转换:
即将b += 3 等价于b = (byte)(b + 3)
b++ 也是同样的原理，也是会在底层进行一个数据类型的转换
```



# 十六、三元运算符【TernaryOperator】？

基本语法：

```
条件表达式？表达式1：表达式2
```

运算规则：

```
1、如果条件表达式为true，运算后的结果是表达式1
2、如果条件表达式为false，运算后的结果是表达式2
```

#### 口诀是：一真大师【只要条件表达式为真，那么就返回表达式1】

示例1：

```java
public class Test {
	public static void main(String[] args) {
		int a = 10;
		int b = 99;
		int result = a>b?a++:b--;
		System.out.println("result的值是：" + result); // 输出：99
		System.out.println("a的值是：" + a); // 输出：10
		System.out.println("b的值是：" + b); // 输出：98
	}
}
```

示例2：

```java
public class Test {
	public static void main(String[] args) {
		int a = 10;
		int b = 99;
		int result = a<b?a++:b--;
		System.out.println("result的值是：" + result); // 输出：10
		System.out.println("a的值是：" + a); // 输出：11
		System.out.println("b的值是：" + b); // 输出：99
	}
}
```

# 十七、三元运算符细节？

在使用三元运算符的时候，需要注意数据类型的转换：

#### 1、表达式1和表达式2一定要符合赋值给接收变量的类型（自动转换和强制转换）

（1）数据类型匹配示例：

```java
public class Test {
	public static void main(String[] args) {
		int a = 3;
		int b = 8;
		int c = a > b ? 11 : 22;
	}
}
// 解析：因为a、b都是int类型，c也是int类型，所以数据类型匹配，可以正常输出
```

（2）数据类型不匹配示例：

```java
public class Test {
	public static void main(String[] args) {
		int a = 3;
		int b = 8;
		int c = a > b ? 1.1 : 2.2;
	}
}
// 解析：直接报错，因为1.1和2.2是double类型，直接将double赋值给int类型，肯定会报错
```

（3）`数据类型不匹配`，手动进行强制转换：

```java
public class Test {
	public static void main(String[] args) {
		int a = 3;
		int b = 8;
		int c = a > b ? (int)1.1 : (int)2.2;
	}
}
// 解析：直接使用强制数据类型转换即可
```

（4）数据类型不匹配，自动进行转换：

```java
public class Test {
	public static void main(String[] args) {
		int a = 3;
		int b = 8;
		double c = a > b ? 1 : 2;
	}
}
// 解析：在接收变量的时候，使用表示范围更大的数据类型来进行接收，即可自动进行数据类型的转换
```

#### 2、三元运算符号可以转换为if--else语句

```java
// 三元运算语句：
int res = a > b ? a++ : --b;
// if--else语句
if(a > b) {
    a++;
}else {
    --b;
}
```



# 十八、三元运算符练习？

需求：实现三个数的最大值

思路：

1、先得到num1和num2中的最大数，保存到max1

2、然后再求出max1和num3的中的最大数，保存到max2

```java
public class Test {
	public static void main(String[] args) {
		int num1 = 111;
		int num2 = 222;
		int num3 = 333;
		// 多条语句进行执行
		int max1 = num1 > num2 ? num1 : num2;
		int max2 = max1 > num3 ? max1 : num3;
		System.out.println(max2);
        
		// 单条语句进行执行
		int max = (num1 > num2 ? num1 : num2) > num3 ? (num1 > num2 ? num1 :nuim2) : num3;
	}
}
```

#### 解析：在实际的开发中，为了增强代码的可读性和维护型，避免使用嵌套和复杂度高的写法，如上述中的单条语句的执行



# 十九、运算符优先级？

![image-20231120143553320](https://github.com/w24w24/javaSE/blob/master/Images/%E8%BF%90%E7%AE%97%E7%AC%A6%E4%BC%98%E5%85%88%E7%BA%A7.png)

1、运算符有不同的有限级，所谓的优先级就是表达式运算中的运算顺序，如右表，上一行运算符号总是优先于下一行

2、只有单目运算符、赋值运算符是从右往左的，其它的都是从左往右的

#### 梳理小结：只需要有一个大致的印象就可以了，使用多了，就记得了，不用去死记硬背



1、()、{}等

2、单目运算 ++  --

3、算数运算符

4、位移运算符

5、比较运算符

6、逻辑运算符

7、三元运算符

8、赋值运算符
