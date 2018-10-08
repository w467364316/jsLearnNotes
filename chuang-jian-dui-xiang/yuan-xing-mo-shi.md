# 原型模式

## 1 prototype属性

每一个函数都有一个prototype（原型）属性，为一个指针，指向一个对象，简单理解为指向通过调用构造函数创建的实例对象的原型对象

## 2 理解原型对象

* 创建一个函数，就会根据特定的规则生成一个prototype属性，指向函数的原型对象。
* 原型对象默认会有一个contructor属性，一个指向prototype属性所在函数的指针。
* 使用构造函数创建实例对象之后，实例对象会生成\__proto\__指向函数的原型对象。

isPrototypeOf\(\)

* 原型对象.isPrototype\(实例对象\)  检测原型对象和实例之间是否有对应的关系

Object.getPrototypeOf（实例对象\)

* 获取实例对象对应的原型对象

### 2.1 **当代码读取对象的某个属性时，是怎样进行查询的呢？**

1. 首先会在实例对象自身的属性中查询是否有，如果有则返回，如果没有的话，进行下一步
2. 如果本身没有该属性，那么就会去原型对象中查找是否有该属性，如果有，则返回。

关于实例对象的constructor指向其构造函数的问题

* 因为原型对象初始化时就会有一个constructor属性指向包含自身指针的函数，那么使用实例对象.constructor时，就会在对应的原型对象中搜寻constructor，进而找到实例对象的构造函数

### 2.2 对象实例可以访问原型的属性，但是不能修改原型中属性的值

* 如果使用实例对原型中的属性进行值的修改，那么其实会在实例本身创建一个同名的属性，以后读取该属性时，就会直接读取实例本身的值而忽略掉原型中同名属性的值
* 使用delete操作符可以删除实例对象中的属性，但是不能删除掉原型对象中的同名属性。

2.2.1 可以利用 实例对象.hasOwnProperty\(\) 方法检测属性是否是实例本身的。

2.2.2 在使用in操作符来判断属性是否是对象中是，’xxx‘ in object ，属性在实例对象中或原型中都会返回true。

2.2.3 使用Object.keys（实例对象） 来获取对象全部可枚举的属性

2.2.4 使用Object.getOwnPropertyNames\(\) 可以 获得全部的实例属性，无论属性是否可枚举

### 2.3 更加简单的原型对象定义

```
funtion Person () {
}

Person.prototype = {
    name:'',
    showName: function () {
        alert(this.name)
    }
}
```

如上代码所示，但是这样写会有一个问题，函数本身产生的原型对象其自动生成的constructor属性本来是指向Person的，**但是现在直接将prototype替换成新对象，那么Person.prototype.constructor就会指向新对象的构造函数Object了。**

```js
Person.prototype = {
    constructor: Person
    name:'',
    showName: function () {
        alert(this.name)
    }
}
```

如上图所以，**定一个constructor属性指向Person**，但是因为原型对象默认生成的constructor属性是不可枚举的，所以可以使用defineProperty的方法添加contructor属性

```
Object.defineProperty(Person.prototype,'constructor',{
    enumerable: false,
    value: Person
})
```

### 2.4 原型的动态性

2.4.1 **实例对象中的\_**_**proto**_**属性指向的是原型对象，并不是构造函数！**

2.4.3 如果直接替换构造函数的prototype，因为实例对象的proto属性是自动默认指向构造函数自动生成的原型对象的，那么实例对象在调用属性或者方法时，也就不会去新的原型对象中找寻了。

```js
    function Person () {

    }

    var p = new Person();

    Person.prototype = {
      sayName: function () {
        console.log('原型方法')
      }
    }
    p.sayName()  error报错

    /************************************/

    function Person () {

    }
    Person.prototype = {
      sayName: function () {
        console.log('原型方法')
      }
    }
    var p = new Person();
    p.sayName() //打印 原型方法
```

如上图所示，创建p实例之后，然后改写Person的实例对象，那么此时p的proto指向的是Person默认创建的原型对象，那么调用sayName时就会报错。内幕参照下图：

![](/assets/import4.png)

但是如果是先改写Person.prototype，然后在创建p实例的话，那么此时p实例的proto指向的就是改写的原型对象！

### 2.5 原型模式的缺点

因为其共享的性质，对于属性值是变量，而且多个实例对象的该属性值都不一样来说，多个实例对象其中一个修改，其他的实例对象也会跟着变化，这对于需要分开独立管理有冲突。

