# 根据字符返回位置（其实就是返回索引号）

## 接day9.8结论：字符串的所有方法，都不会修改字符串本身（字符串是不可变的），操作完成会返回一个新的字符串

1.这是indexOf：

```javaScript
// 根据字符串返回位置
var arr = '改革春风吹满面，春天来了！'
var test = arr.indexOf('春',3); // 这里才是indexOf的完整用法：indexOf('需要查询的字符'，起始位置)
console.log(test); // 输出：8
```

2.这是lastIndexOf：

```javaScript
// 根据字符串返回位置
var arr = '改革春风吹满面，春天来了！'
var test = arr.lastIndexOf('春',7); // 这里才是indexOf的完整用法：indexOf('需要查询的字符'，起始位置)
console.log(test); // 输出：2
```

