# 增强的模块模式

模块模式适用于创建一个Object类型的单例。如果要创建一个指定类型的单例对象，还需要稍微修改一下增加属性或者方法，适用增强的模块模式

```
var singleton = function () {
    var privateVariable = 10;
    function privateFunction() {

    }

    var object = new SomeObject()
    object.getComponent = function () {
        return privateVariable
    }
    return object;
}();
```

在函数中创建自定义类型的实例变量，然后可以增加相应的方法或属性。



