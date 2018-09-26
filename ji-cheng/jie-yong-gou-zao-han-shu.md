# 借用构造函数

在构造函数中利用call或者apply方法，改变this的值

```
function Person () {
    this.colors = []
}

function Stu () {
    Person.call(this)
}

var stu1 = new Stu()
```

**缺点：**

1. 函数复用不能实现
2. 借用构造函数的模式不能访问超类型原型对象中的方法和属性。



