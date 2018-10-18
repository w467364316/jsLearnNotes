使用Object原生的toString方法会返回类似''\[object Object\]'的字符串，可以用于判断实例的类型。

```
判断是否是数组
function isArray (value) {
    return Object.prototype.toString.call(value) === '[object Array]'
}
```

如果是数组的话，那么会返回true。其他的类型也可以用自办法进行判断



