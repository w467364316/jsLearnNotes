# 寄生组合式继承

在使用组合继承方式时，一同需要两次调用超类型构造函数

1. 借用构造函数时需要调用一次。
2. 给子类型重定义原型使需要调用一次

如果超类型有定义自己的属性，那么这就导致了子类型和子类型原型上有同样的属性，重复创建

```js
function Person (name) {
    this.name = name
    this.colors = []
}

Person.prototype.sayName = function () {
    console.log(this.name)
}

//借用构造函数
function Stu (name) {
    Person.call(this,name)
}

//替换原型对象
Stu.prototype = new Person();
Stu.prototype.constructor = Stu;

var stu1 = new Stu('stu1');
var stu2 = new Stu('stu2');

stu1.sayName();// stu1
stu2.sayName(); // stu2
```

如上代码所示：

* Person本身有name和colors两个属性，在使用借用构造函数时，Stu的实例对象会拥有这两个属性。在替换原型对象时，Stu的原型对象（Person实例对象）也会拥有这两个属性。



为了让替换原型对象时不多调用一次超类型的构造函数，可以使用寄生组合继承类型+借用构造函数代替上述实现过程

```js
//寄生组合式继承
function inheritPrototype (subTyp,superType) {
    var clone = Object.create(superType.prototype);
    clone.constructor = subType;
    subType.prototype = clone
}

function Person (name) {
    this.name = name
    this.colors = []
}

Person.prototype.sayName = function () {
    console.log(this.name)
}

//借用构造函数
function Stu (name) {
    Person.call(this,name)
}

//替换原型对象
inheritPrototype(Stu,Person)

var stu1 = new Stu('stu1');
var stu2 = new Stu('stu2');

stu1.sayName();// stu1
stu2.sayName(); // stu2
```

集组合继承和寄生式继承于一身，是最有效的方式





