直接使用确定对象的某个特性是否存在，但是并不能知道该特性是不是你想要的。

比如如下代码：

```js
function isSortAble (object) {
    return !!object.sort
}
注释：使用 !!会模拟调用Boolean（）方法
```

虽然可以检测到sort这个属性是否存在，但是检测不到sort是否是我们需要的排序函数，所以使用typeof会更加的可靠

```js
function isSortAble (object) {
    return typeof object.sort === 'function';
}
```

但是在IE中会有些不同，比如IE8和以前的IE版本中使用的是COM对象不是函数，IE中的ActiveX对象对其方法使用typeof会返回unknown，所以可以使用如下的方法去判断：

```js
function isHostMethod (object,propertyName) {
    var t = typeof object[propertyName]
    
    retur t==='function' || (!!(t==='object'&&object[propertyName])) || t == 'unknown'
}
```



