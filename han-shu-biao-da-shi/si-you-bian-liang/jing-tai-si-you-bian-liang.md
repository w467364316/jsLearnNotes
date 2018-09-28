# 静态私有变量

通过在私有作用域中定义量或者函数，同样可以创建特权方法，其基本模式如下：

```
(function (){
    var privateVariable = 10;
    function privateFunction () {
        return false
    }
    
    //构造函数
    MyObject = function () {
    }
    
    //公有/特权方法
    MyObject.prototype.publicMethod = function () {
        privateVaraiable++;
        return privateFunction();
    }
    
})()
```

上述代码中的MyObject，是未经过声明的变量，那么就会默认创建一个全局变量，所以MyObjecct（构造函数）是全局变量，由MyObject创建的实例对象都能访问到私有作用域中的privateVariable变量和privateFunction方法。

所以私有作用域中的privateVariable变成了一个静态私有变量，由所有MyObject的实例共用。



按照上述方式创建的静态私有变量会因为使用了原型而使得代码复用，但是每个实例都没有自己的私有变量。所以是使用私有静态变量还是实例变量，需要根据情况具体而定。



