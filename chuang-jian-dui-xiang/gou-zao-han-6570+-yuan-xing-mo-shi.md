# 构造函数+原型模式

在构造函数中定义对象应该本身拥有的属性，而在原型模式中定义共享的方法和属性

```
function Person () {
    this.name = '123';
    this.age="123';
}

Person.prototype = {
    constructor: Person,
    sayName: function () {
        alert(this.name)
    }
}

var p1 = new Person();
var p2 = new Person();
```

**特别注意：不能再重写prototype之前创建实例变量，这样的话就会切段实例与新原型对象的联系！**

因为实例在创建是会默认生成一个\[\[prototype\]\] 属性指向构造函数的原型对象，创建实例对象之后，在替换构造函数的原型对象。此时实例的\[\[prototype\]\]是指向原来的原型对象，和新的原型没有关系！



