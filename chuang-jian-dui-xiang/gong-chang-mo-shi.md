# 工厂模式

定义一个函数，在函数内创建对象并返回

```js
function createPerson(name,age) {
    var obj = new Object()
    obj.name = name;
    obj.age = age;
    return obj
}
```

缺点： 不能够对对象进行类型识别，所以慢慢采用了构造函数模式



