# 布尔型

## 布尔型分为：true、false

```javaScript
var arr = true;//表示布尔型中的true
var arr1 = false;//表示布尔型中的false
console.log(true + 1);//输出：2【在参与运算的时候，true相当于1】
console.log(false + 1);//输出：1【在参与运算的时候，false相当于0】
```

## Undefined和Null

### 1.如果一个变量定义未赋值，就是undefined 未定义数据类型

```javaScript
//定义一个未定义的变量
var str;
console.log(str);//输出：Undefined

var variable = undefined;
console.log(variable + 'pink');//输出：undefinedpink
console.log(variable + 1);//输出：NaN
```

### 2.Null空值

```javaScript
//空值
var arr = null;
console.log(arr + 1);
```

