IE中没有addEvenListener这样的方法，但是有类似的实现：

* attachEvent\(\)
* detachEvent\(\)

都是接受两个参数

* 事件名
  * 跟addEvent有区别的是，此处事件名需要使用类似 on+click
* 表示事件处理程序的函数



attach同样可以为同一事件名添加多个事件处理程序，但是执行顺序和定义顺序相反。



IE事件处理程序中的this值并不是目标元素，所以运行的作用域是在 全局作用域中运行。

```js
var btn = document.getElementById("myBtn");
    btn.attachEvent("onclick", function(){
    alert(this === window); //true
});
```



使用detachEvent移除事件时，同样需要传入同一个函数，不能使用匿名函数。





