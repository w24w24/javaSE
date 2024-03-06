# 筛选数组元素

## 一、作业1；筛选数组中工资超过2000元的，并且将其放到一个新数组里面

```javaScript
// 筛选数组
function getArray(salary) {
    var newSalary = []; // 建立一个空的数组，用来替换工资超过2000的数组元素
    if (Array.isArray(salary)) { // 使用Array.isarray()来判断传入的实参是否是数组形式
        for (var i = 0; i < salary.length; i++) { // 使用for循环来遍历数组中的工资
            if (salary[i] >= 2000) { // 设定条件，工资超过2000元的数组元素
                newSalary[newSalary.length] = salary[i]; // 将工资超过2000元的元素传入新数组中
            }
        }
        return newSalary; // 返回新数组中的数组元素
    }
}
var arr = [1500,1200,2000,2100,1800,5300,15452,456221,12344];
var sl = getArray(arr);
console.log(sl);
```

## 二、作业2：筛选数组中工资超过2000元的，将其删除，并且超过2000元的将放到一个新数组里面（后续练习）

```javaScript
var arr = [1500,1200,2000,2100,1800,5300,15452,456221,12344];
var newArray = [];
for (var i = 0; i < arr.length; i++) {
    if (arr[i] >= 2000) {
        newArray.push(arr[i]); // 采用追加数组的方式
    }
}
console.log(newArray);
```