通过定义两个方法来添加删除方法，并且是全部的DOM节点都具有

* addEventListener\(\) 添加
* removeEventListener\(\)移除方法

都是接受三个参数：

* 要添加的事件名
  * **注意此处不使用on开头，比如 ‘click’**
* 作为事件处理程序的函数
  * **如果要删除指定的事件处理程序，那么该函数不能使用匿名函数，而是应该使用函数的引用，添加和删除时传递同一个函数引用。**
* 布尔值
  * true表示事件在捕获阶段处理
  * false表示事件在冒泡阶段处理，一般选择false

```
var btn = document.querySelector('#btn')
btn.addEventListener('click',functon(){},false);
```



可以同时添加多个同一事件的事件处理程序，并且会按照定义的先后顺序执行。

**再删除指定的事件处理程序时，需要传入添加时的同一个函数，不能是匿名函数，不然无法删除。**

```
var btn = document.querySelector('#btn')
var handle = function message () {

}
btn.addEventListener('click',handle,false)  //添加方法
btn.removeEventListener('click',handle,false)//删除方法
```

该方式定义的函数中的this还是指向目标元素。



