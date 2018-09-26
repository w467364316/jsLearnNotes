# 动态原型模式

在构造函数中直接添加原型对象的方法和属性

```js
function Person () {
    this.name = '123';
    this.age = '12';
    
    if (typeof this.sayName !== function) {
        Person.prototype.sayName = function () {
            alert(this.name)
        }
    }
}
```

构造函数中的添加原型对象的方法和属性也只会执行一次，因为再添加一次之后，下一次判断if时，typeof this.sayName  为function，自然就不会再重新执行if里面的代码了。



