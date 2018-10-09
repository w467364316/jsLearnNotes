通过js指定事件处理程序。将一个函数赋值给一个事件处理程序属性。

每个元素都有自己的事件处理程序属性，**这些属性通常都是小写，比如onclick：**

```
var btn = document.querySelector('#btn')
btn.onclick= function(){
    alert('clicked')
}
```

使用DOM0级的方法指定的时间处理程序被认为是元素的方法，所以事件处理程序是在元素的作用域中运行。也就是说其中的this值也是引用当前的元素。

也可以通过给事件处理程序属性的值赋值为null来移除事件。

```
btn.onclick = null;
```





