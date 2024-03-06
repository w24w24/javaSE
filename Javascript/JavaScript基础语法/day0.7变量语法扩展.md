# 变量的语法扩展

## 1.更新变量：一个变量被重新赋值后，原有的值就会被覆盖，变量值将以最后一次赋的值为准

```javaScript
//初始化一个变量
        var myname = 'pink老师';
        console.log(myname);
        //由于已经开辟过了空间，直接赋值即可,不需要再开辟额外的空间
        myname = '迪丽热巴';
        console.log(myname);//最终在控制台输出的就是迪丽热巴
```

## 2.声明多个变量:沿着第一个写就可以了，期间使用逗号隔开，最后一个使用得分号隔开

```javaScript
var age = 18,
    address = '火影村'，
    salary = 2000;
```

## 3.声明变量的特殊形式：

```javaScript
var age;console.log(age);//只声明不赋值，结果为undefined
consolelog(age);//不声明，直接使用，结果报错
age = 10;cnsole.log(age);//不声明，直接赋值，结果为：10
```

## 注：在JS中，假设一个模块的代码出问题，那么下面的代码就不会再执行

