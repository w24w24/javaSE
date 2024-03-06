# 分支流程控制语句：switch

## switch语句也是多分支语句，它基于不同的条件来执行不同的代码，当要正对变量设值一系列`特定`的值的选项的时候,就可以使用switch语句



## 语法结构：

```javaScript
//switch语句结构：
switch (语句表达式) {
    case value1:
        //执行语句
        break;
    case value2:
        //执行语句
        break;
    ....
    default:
        //执行语句;
}
```

## 执行思路：利用我们表达式的值，和case后面的value相匹配，如果匹配上，就执行case里的代码，如果都没有匹配上，就执行default里的代码

## 注意事项：

1. 在实际的开发中，我们通常把语句表达式写成一个变量

   ```javaScript
   //在实际的开发中，我们通常将语句表达式写成是 变量
   var num = 3;
   switch (num) {
       case 1:
           console.log('这是case1');
           break;
       case 2:
           console.log('这是case2');
           break;
   }
   ```

2. 语句表达式中的num和case后面的value值必须是全等；也就是说必须是类型和值必须一致

3. 如果当前的执行代码中没有break，则会继续执行下一个语句，直到有break为止

## 作业：水果价格及其查询

```javaScript
//查询水果的价格：
//输入水果的名字 假如有，就直接返回价格  假如没有 就弹出没有此水果
var fruitName = prompt('请输入水果的名字查询价格：');
switch (fruitName) {
    case '苹果':
        alert('苹果的价格是：35元/斤');
        break;
    case '香蕉':
        alert('香蕉的价格是：25元/斤');
        break;
    case '橘子':
        alert('橘子的价格是：15元/斤');
        break;
    case '葡萄':
        alert('葡萄的价格是：12元/斤');
        break;
    default:
        alert('没有此水果');
}
```
