访问IE中的event对象有几种方式，取决于指定事件处理程序的方法

1. 如果使用**DOM0和DOM2级**添加事件处理程序方法，那么就需要使用**window.event访问event对象**。
2. 如果是使用**attachEvent**创建的，那么会有一个**event**对象作为参数被传入事件处理程序。
3. 如果是通过HTML特性指定的事件处理程序，那么可以通过一个event的变量访问event

因为IE中使用的this和DOM中的不一样，所以最好使用**event.srcElement**比较保险。

```
var btn = document.querySelector('#btn')
btn.attachEvent('onclick',function(event) {
    event.srcElement == this  //false
})

btn.onClick = function (event) {
    event.srcElement == this //true
}
```

常用的属性方法：

* returnValue 属性相当于DOM中的preventDefault\(\)方法，只要设置为false，就能取消默认行为
* cancleBubble属性与stopPropagation（）方法作用相同，设置为true则就会停止冒泡和捕获。



