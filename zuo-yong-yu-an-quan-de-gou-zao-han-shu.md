在使用构造函数时，一般是使用new关键字，然后调用函数，但是往往会忘记写new关键字，那么可以修改一下构造函数。

```js
function Person (name) {
    if (this instanceof Person) {
        this.name = name
    }else {
        return new Person()
    }
}
```

此种方法如果是直接使用在借用构造函数中，那么可能会出现问题。

```js
function Person (name) {
    if (this instanceof Person) {
        this.name = name
    }else {
        return new Person()
    }
}

function Stu (age,name) {
    Person.call(this,name)
    this.age = age;
}

var sut1 = new Stu(12,'xiaoming')
console.log(stu1.name);  //undefined
```

因为使用了作用域安全的构造函数，那么这样写就不会给Stu添加上name属性。

如果是借用构造函数+原型继承的话，就不会发生这种情况：

```js
function Person (name) {
    if (this instanceof Person) {
        this.name = name
    }else {
        return new Person()
    }
}

function Stu (age,name) {
    Person.call(this,name)
    this.age = age;
}

Stu.prototype = new Person()

var sut1 = new Stu(12,'xiaoming')
console.log(stu1.name);  //xiaoming
```

因为指定了Stu的原型为Person的实例，那么在Person的构造函数中判断时，this instance of是根据原型链来判断的，原型链中出现过的那么就会返回true。

