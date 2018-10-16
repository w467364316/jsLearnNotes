拖放事件

对于被拖放目标元素：

* dragstart 
  * 按下鼠标键并且开始移动鼠标时
* drag 
  * 触发dragstart事件之后，随即会触发drag事件，并且在元素被拖动期间会持续触发该事件。
* dragend 
  * 当拖动停止时，会触发dragend事件。

对于要放置的目标元素：

* dragenter
  * 有元素被拖动到放置目标上，就会触发dragenter事件
* dragover 
  * 触发enter事件之后就会触发over事件，并且是移动式持续触发。
* dragleave 或者 drop
  * 如果元素被拖出了放置目标就会触发leave事件，如果元素被放到了放置目标中，则会触发drop事件，而不是dragleave事件。

## 自定义放置目标

虽然所有的元素都支持放置目标 事件，但这些元素默认是不允许放置的，如果拖动元素经过不允许放置的元素，是不会触发drop事件的。

但是可以通过修改enter和over的默认行为来让元素成为有效的放置目标。

```
addEvent(div,'dragenter',function(event){
    event.preventDefault()
})
addEvent(div,'dragover',function(){
    event.preventDefault()
})
```

## dataTransfer对象

用来在拖动事件中像放置目标元素传递数据，为拖动事件对象event的属性。

主要方法：

* getData\(\)
  * 保存的数据只能在drop事件中才能获取。
* setData\(\)
  * 可以为每一种MIME类型保存一个值。
  * 在拖动文本时，文本将以‘text’格式保存在dataTransfer中，拖动链接和图像时，会调用setData\(\)方法并保存URL。
  * 也可以自dragstart事件中调用setdata\(\)方法中设定数据。

为了兼容浏览器，读取text和url的方式如下：

```
var dataTransfer = event.dataTransfer
var url = dataTransfer.getData('url') || dataTransfer.getData('text/url-list')
var text = dataTransfer.getData('Text')
```

## dropEffect和effectAllowed

dropEffect属性可以定义被拖动的元素可以执行什么操作，主要的值有：

* none 不能把拖动的元素放在这里
* move 移动到目标元素
* copy 复制到目标元素
* link 表示放置目标会打开拖动的元素。

必须在ondragenter事件处理程序中针对放置目标设置他。

effectAllowed属性，表示允许拖动元素的那种dropEffect。

## 可拖动

默认情况下，图形，连接和文本是可以拖动的，对于其他不能拖动的元素可以通过设置draggable特性来设定是否可拖动。

