# 利用对象封装自己的数学对象

## 一、什么叫做利用对象封装自己的数学对象？

解析：比如Math就是一个数学对象，我们在使用的时候只需要调用它即可；但是现在我们想要书写一个属于自己的对象，并且是已经被封装好了的，像Math一样

## 二、作业：利用对象封装自己的数学对象 里面有PI和最大值、最小值【这个案例会在以后经常去写，所以这个案例非常有锻炼价值】

```javaScript
var myMath = {
    PI: 3.14159265358972,
    max: function() {
        var max = arguments[0];
        for (var i = 1; i < arguments.length; i++) {
            if (arguments[i] > max) {
                max = arguments[i];
            }
        }
        return max;
    },
    min:function() {
        var min = arguments[0];
        for (var i = 1; i < arguments.length; i++) {
            if (arguments[i] < min) {
                min = arguments[i];
            }
        }return min;
   }
}
// 由于上述的myMath已经被我们封装成为一个函数对象了，所以只需要直接调用就可以了
console.log(myMath.PI);
console.log(myMath.max(1,2,3,4,5));
console.log(myMath.min(5,4,3,2,1));
```

