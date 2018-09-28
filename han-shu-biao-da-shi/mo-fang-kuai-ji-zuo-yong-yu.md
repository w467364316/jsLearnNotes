# 使用匿名函数模仿私有作用域

主要是利用包含函数不能向下访问被包含函数中的变量，被包含的函数因为是闭包，可以访问包含函数的变量。

```
函数形式为：
(function(){
    //私有作用域
}）()
    
其实等同于
var func = function () {}
func();
```

应用：

```
functon count (number) {
    var result = 0;
    (function(){
        for(var index = 0;index<number;index++) {
            result += index
        }
    })()
    
    console.log(index)//报错
    return result;
}
```

如上代码所示，使用了私有作用域，那么在外部函数count中就不能访问到变量index了。

私有作用域经常用于在全局环境下使用，可以减少定义在全局执行环境下的变量。



