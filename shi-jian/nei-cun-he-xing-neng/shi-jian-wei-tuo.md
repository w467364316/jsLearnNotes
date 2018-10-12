## 事件委托

主要是针对事件处理程序过多的情况下。

事件委托主要采用事件的冒泡机制，指定一个事件处理程序，处理一类事情。

比如多个元素的onclick事件，可以直接在document上指定一个onclick事件处理程序，然后使用event.target.id来区分不同的目标元素。

优点：

* docment对象很快就可以访问到，而且可以在页面生命周期的任何时间点上为他它添加事件处理程序。（不用等到DOMContentLoaded或者load事件之后）
* 在页面中设置事件处理程序所需的时间更小。只需要添加一个事件处理程序所需的DOM引用更少。
* 整个页面占用的内容空间更少，能够提升整体性能。

比较适合采用事件委托的事件包括 click,mousedown mouseup keydown keyup和keypress



