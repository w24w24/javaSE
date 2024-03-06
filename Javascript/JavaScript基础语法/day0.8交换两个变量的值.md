# 交换两个变量的值

## 我们在书写代码的时候，需要厘清思路和逻辑，我们可以先使用文字进行叙述，然后再书写代码

```javaScript
//要求：交换两个变量的值
//1.需要一个临时变量作为容器
//2.然后把apple1赋给临时变量temp
//3.然后apple1就空出来了，然后把apple2赋给apple1
//4.再把临时变量temp中多的apple1赋给apple2
var temp;
var apple1 = '青苹果';
var apple2 = '红苹果';
//开始交换：
temp = apple1;
apple1 = apple2;
apple2 = temp;
//在控制台输出：
console.log(apple1);
console.log(apple2);
```

