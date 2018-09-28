# 模块模式

静态私有变量模式是为了给自定义类型创建私有变量和特权方法的。

模块模式则是为单例创建私有变量和特权方法的。

单例（singleton）一般表示只有一个实例的对象。一般直接使用字面量来定义单例

```
var singleton = {
    name: value,
    methods: function (){

    }
}
```

使用模块方式为单例添加私有变量和特权方法

```
var singleton = function () {
    var privateVariable = 10;
    function privateFunction () {
        return false
    }
    return {
        publicProperty: true,
        publicMethod: function () {
            privateVariable ++;
            return privateFunction()
        }
    }
}()
```

利用一个返回对象的匿名函数，函数内部定义私有变量和函数。然后将一个对象字面量作为函数的返回值。返回的对象字面量中只包含可以公开的属性和方法，由于这个对象是在函数内部定义的，因此它的公有方法有权访问私有变量和函数。

这种模式对于单例进行某些初始化，同时又需要维护其私有变量时是非常有用的。

