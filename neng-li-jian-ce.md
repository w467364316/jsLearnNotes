# 能力检测

也叫特性检测，不是识别特定的浏览器，而是识别浏览器的能力。

通常的方式为：

```
if (object.propertyInQuestion) {
    //可以使用propertyInQuestion
}
```

首先检测对象的属性（特性是否存在，如果存在，那么就可以使用）

注意两个概念：

1. 要先检测达成目的的最常用的特性，如下代码中先检测getElement然后在检测all方法
2. 必须测试实际要用到的特性，不能测试的时候是一个特性，使用的却是另外一个特性。

```
function getElement(id) {
    if (document.getElementById) {
        return document.getElementById(id)
    }else if (document.all) {
        return document.all(id)
    }else {
        throw new Error('no way to retrieve element!')
    }
}
```



