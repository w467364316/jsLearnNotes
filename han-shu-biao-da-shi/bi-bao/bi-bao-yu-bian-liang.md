# 闭包与变量

闭包会引用包含其函数的整个活动对象，而不是某个特殊的变量，所以是包含了包含函数中任何变量的最后一个值。

```
function createFunctions () {
    var array = []
    for (var i = 0;i<10;i++) {
        array[i] = function () {
            return i;
        }
    }
    return array
}
```

如上代码所示，数组中包含了10个匿名函数，**但是一一调用的结果是全部都会返回10**。因为数组中的匿名函数包含了createFunctions的活动对象，该活动对象中变量i的最后的值为10。

可用的解决方法：

```
function createFunctions () {
    var array = []
    for (var i = 0;i<10;i++) {
        array[i] = function (num){
            return function(){
                return num
            }
        }(i)
    }
    return array
}
```

如上代码所示，数组中任然是10个匿名函数，但是这些匿名函数的作用域链中包含了外部函数的活动对象，该对象中num的值就是0-9



