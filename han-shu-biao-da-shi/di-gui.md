# 递归

在递归函数中需要多次调用同一个函数，但是函数也是一个对象，如果对象的引用发生改变，那么调用时可能发生错误。

非严格模式下可以使用argments.callee来代替函数名

```
function Sum (number) {
    if (number <=1) {
        return 1
    }
    return number + arguments.callee(number - 1)
}
```



严格模式下是不能使用脚本访问arguments.callee的，那么可以使用命名表达式来实现

```
var sum = (function func (number) {
    if (number <=1) {
        return 1
    }
    return number + func(number - 1)
})
```



