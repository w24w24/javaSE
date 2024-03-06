# for循环重复执行代码

## 1.for循环重复执行相同的代码：

连续输出 11句 你是猪：

```javaScript
//for循环重复执行相同的代码
for (var i = 1; i < 11; i++) {
    console.log('你是猪');
}
```

## 2.for循环执行不同的代码：

输出一个人1——100岁的年龄：

```javaScript
//输出一个人1——100岁
//var age = Number(prompt());
for (var i = 1; i < 101; i++) {
    console.log('今年你已经' + i+ '岁了');
}
```

## 3.计算1——100之间的累加和：

```javaScript
//计算1——100之间所有数据的累加和
var sum = 0;
for (var i = 1; i < 101; i++) {
    sum = sum + i;
}
console.log(sum);
```

## 4.计算1——100之间的平均值：

```javascript
//计算1——100之间所有数据的累加和
var num = 100;
var sum = 0;
for (var i = 1; i < 101; i++) {
    sum = sum + i;
}
console.log('1——100之间的总和' + sum);//1——100之间的总和
console.log('1——100之间的平均值' + sum/num);//1——100之间的平均值
```

## 计算1——100之间所有数据的偶数和奇数和

```javaScript
//计算1——100之间所有偶数和奇数的和
var even = 0;
var odd = 0;
for (var i = 1; i <= 100; i++) {
    if (i % 2 === 0) {
        even = even + i;
    }else {
        odd = odd + i;
    }
}
console.log('所有偶数和为:' + even);
console.log('所有奇数和为:' + odd);
```

## 作业：求学生成绩

### 要求：

1. 要求用户输入班级人数
2. 之后依次输入学生的成绩
3. 最后打印出来该班级的总的平均成绩以及总成绩

```javaScript
//1. 要求用户输入班级人数
//2. 依次输入每个学生的成绩
//3. 打印该班级的总的成绩、平均成绩

    //用户输入班级人数：
    var students = Number(prompt('请输入班级人数：'));
    var sum = 0;
    var average = 0;
    //依次输入学生成绩：
    for (var i = 1; i <= students ; i++) {
        var score = Number(prompt('请输入第' + i + '个学生成绩'));
        sum = score + sum;//计算输入的总成绩
    }
    average = sum / students;//计算输入的平均成绩
    alert('该班级的学生总成绩是' + sum + '\n该班级学生的平均成绩是' + average);
```

## 作业：一行打印5颗星星

### 要求：必须在一行里面同时显示5颗星星

```javaScript
//在一行里面打印5颗五角星
//采取追加字符串的方式
var str = '';
for (var i = 1; i <= 5; i++) {
    str = str + '★';
}
console.log(str);
```