# 稳妥构造函数模式

构造函数中不适用this，创建实例时不适用new关键字

```js
function Person (name) {
    var o = new Object();
    o.sayName = function () {
        alert(name)
    }
}

var p = Person('123')
p.sayName()  //123
```

对于传递进去的形参，只有sayName可以获得，实例本身并没有name属性



