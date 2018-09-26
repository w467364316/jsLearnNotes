# 组合继承

组合原型链和借用构造函数，使用原型对象替换实现原型对象中方法属性的共用，使用借用构造函数实现像超类型传参和拥有自己的实例属性

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





