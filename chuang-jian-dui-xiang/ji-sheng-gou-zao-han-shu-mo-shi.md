# 寄生构造函数模式

跟工厂模式类似，但是函数叫做构造函数而非包装函数，而且使用new关键字

```js
function Person (name,age) {
    var o = new Object();
    o.name = name;
    o.age = age;
    o.sayName = function () {
        alert(this.name)
    }
    return o
}

var p = new Person('123',24)
```

这个模式可以在特殊情况下为对象创建构造函数，概念类似继承：

![](/assets/import5.png)





