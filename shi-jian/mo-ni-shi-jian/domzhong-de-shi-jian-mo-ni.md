使用document对象的createEvent\(\)方法，传入字符串生成一个事件对象。

主要有这几种事件字符串：

* UIEvents 一般化的UI事件
* MouseEvents 鼠标事件
* MutationEvents  一般化的DOM变动事件
* HTMLEvents 一般化的HTML事件



## 1 模拟鼠标事件

```
var app = document.querySelector('#app')
addEvent(app,'click',function(){
    console.log('123')
})
var event = docoument.createEvent('MouseEvents')
event.initMouseEvent('click',true,true,document.defaultView,0,0,0,0,0,false,false,flase,flase,0,null)
app.dispatchEvent(event)
```

使用createEvent\('MouseEvents'\)生成的对象会有一个initMouseEvent\(\)方法，用来设定事件的具体信息：

* type 事件类型
* bubbles 是否支持冒泡
* cancelable 是否可以取消默认行为
* view 相关联的视图，一般设置为document.defaultView
* detail 与事件相关的详细信息，一般设置为0
* screenX
* screenY
* clientX
* clientY
* ctrlKey
* altKey
* shiftKey
* metakey
* button  表示按下了哪一个鼠标键，默认值为0
* realtedTarget 一般只有在mouseup和mousedown时设置，其他设置为null



## 2 模拟键盘事件

跟模拟鼠标事件类似，也有自己的事件字符串和配置项



## 4 自定义DOM事件

不是DOM原生触发的事件（click等），而是开发者自定定义事件，然后让相应的元素进行监听。

使用CustomEvent创建自定义事件，生成的对象有一个名为initCustomEvent的方法，可以接受如下4个参数：

* type 字符串，定义事件类型
* bubbles 是否冒泡
* cancelable 是否可以取消
* detail 任何值，保存在event.detail中的值

```
addEvent(div,'myEvent',function(){})
var event = document.createEvent('CustomEvent')
event.initCustomEvent('myEvent',true,true,null)
div.dispatchEvent(event)
```







