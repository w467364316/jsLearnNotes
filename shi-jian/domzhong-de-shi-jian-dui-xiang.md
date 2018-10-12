兼容DOM的浏览器会讲一个event对象传入事件处理程序中，无论指定时间处理程序使用什么方法（DOM0或者DOM2）,都将会传入event对象。

```
var btn = document.querySelector('#btn')
btn.onclick = function(event) {
    console.log(event.type) //click
}
```

一些重要的属性和方法：

* 在事件处理程序中，对象this始终等于currentTarget的值
* target ，只包含事件的实例目标
  * 如果直接将事件处理程序指定给了目标元素，则this target currentTarget包含相同的值。
* type 事件的类型 比如 'click'
* preventDefault\(\) 阻止事件的默认行为，比如a标签点击后跳转到href指定的标签，使用event.preventDefault\(\)就可以阻止
* stopPropagation\(\) 立即停止事件在DOM层次中的传播，即取消进一步的事件捕获或者冒泡。
* eventPhase 确定当前事件正处在那个阶段 值为1 表示捕获阶段， 2 目标阶段， 3 冒泡阶段
  * 尽管处于目标发生在冒泡阶段，但是eventPhase还是显示2



