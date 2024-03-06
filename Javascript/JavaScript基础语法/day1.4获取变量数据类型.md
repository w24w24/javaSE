# 获取变量的数据类型

## 1.当我们不知道变量的数据类型的时候，就可以使用typeof关键字来获取数据类型

```javaScript
//检测数据类型
var num = 10;
console.log(typeof num);//number

//检测数据类型
var str = 'pink老师';
console.log(typeof str);//string

//检测变量是不是布尔值
var arr = true;
console.log(typeof arr);//输出：boolean

//检测变量是不是undefined
var timer = undefined;
console.log(typeof timer);//输出：undefined

//检测变量是不是object
var variable = null;
console.log(typeof variable);//输出：object
```

## 2.注：在使用typeof的时候，从prompt中拿到的数据是字符型的，即使输入的数字，它的数据类型也是字符型的

```javaScript
//这里就需要注意了，我们使用的prompt输出的数据类型是 字符型的
var array = prompt('请输入您的年龄');
console.log(array);
console.log(typeof array);//输出：string
```

# 字面量

## 1.数字字面量：8、9、12

## 2.字符串字面量：黑马程序员、前端

## 3.布尔字面量：true、false

### 解析：字面量就是直接可以通过字面来看出数据的类型
