# 统计出现次数最多的字符

```javaScript
// 统计出现次数最多的字符
var str = 'sdsadasdasdas';
var o = {};
for (var i = 0; i < str.length; i++) {
    var chars = str.charAt(i);
    if(o[chars]) { // o[chars]得到的是属性值
        o[chars]++;
    }else {
        o[chars] = 1;
    }
}
console.log(o);

// 遍历对象
var max = 0;
var ch = '';
for (k in o) {
    // k得到的是属性名
    //o[k]得到的是属性值
    if(o[k] > max) {
        max = o[k];
        ch = k;
    }
}
console.log('最多的字符是' + ch + '\n出现了' + max + '次数');
```

解析：理解即可