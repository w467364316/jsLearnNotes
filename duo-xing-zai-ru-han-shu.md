对于需要使用if判断来区分函数内不同实现的函数，可以让if不必每次都执行。方案为惰性载入，主要有两种方式：

1

```
var func1 = function () {
    if (xxxxx) {
        func1 = function () {
        
        }
    }else {
        func1 = function () {
        
        }
    }
    return func1 ();
} 
```

在第一次调用时，判断之后就将函数替换为相应实现。以后调用时就不会在经过判断。



2 

```
var func1 = (function(){
    if (xxxxx) {
        return function () {
            xxx
        }
    }else {
        return function () {
            xxx
        }    
    }
})()
```

在声明函数时，使用一个自调用函数去进行第一次判断，然后返回对应的函数。



