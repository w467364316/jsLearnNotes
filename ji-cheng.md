# 原型链

继承就是基于原型链的原理实现的。

原型链基本解释：构造函数A的原型对象是构造函数B的实例对象b，实例对象b有proto属性指向构造函数B的原型对象，构造函数B的原型对象又是构造函数C的实例对象c，如此就形成了一条原型链条。

```js
function SuperType () {
    this.property = true;
}

SuperType.prototype.getSuperValue = function () {
    return this.property
}

function SubType () {
    this.subProperty = false
}

//替换原型对象
SubType.prototype = new SuperType()
SubType.prototype.getSubValue = function () {
    return this.subProperty;
}
var instance = new SubType()
alert(instance.getSuperValue)  //true
```

如上图所示，SubType的原型为SuperType的实例对象，那么在instance调用getSuperValue方法时，查询步骤大致为：

1. 在instance本身查询是否有getSuperValue方法，没有找到
2. 在SubType原型对象中查询是否有getSuperValue方法，即SuperType的实例对象，没有找到
3. 然后去SuperType的原型对象中查询是否有getSuperValue方法，查询到了，返回。



注意点： 此时instance实例对象的constructor为SuperType，并不是SubType。因为SubType的**原型对象**替换成了SuperType的实例，SuperType实例对象的constructor指向SuperType，所以instance的constructor指向SuperType。流程表示如下：

instance.constructor--&gt;new SuperType\(\).constructor--&gt;SuperType



## 2. 默认原型

所有函数的默认原型都是Object的实例，所以默认原型中都包含一个指针proto指向Object.prototype。这要是所有自定义类型都会继承toString（）等方法的原因。





