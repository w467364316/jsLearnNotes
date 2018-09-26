# 寄生式继承

仅创建一个用于封装继承过程的函数，包裹原型式继承和实例对象的扩展，然后返回对象

```
function object (o) {
    function F (){}
    F.prototype = o;
    return new F()
}

function createAnother (original) {
    var clone = object(original)
    clone.sayHi = function () {
        alert('hi')
    }
    return clone;
}
```



