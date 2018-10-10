鼠标和滚轮事件：

* click ： 用户单机鼠标按钮或者按下回车按钮
* dblclick：双击按钮
* mousedown ： 用户按下任意鼠标按钮触发
* mouseup : 用户释放鼠标按键
* mouseenter ： 鼠标从外部首次移动到元素范围之内触发，不冒泡，而且移动到子元素上时不触发
* mouseleave： 位于元素上方的鼠标光标移动到元素范围之外时触发。
* mousemove ： 鼠标指针在元素内部移动是重复触发。
* mouseout ： 鼠标指针在一个元素上方，然后用户将其移入另外一个元素时触发，另外移入的元素可能是位于前一个元素的外部或者是他的子元素
* mouseover ： 鼠标位于一个元素外部，然后用户将其首次引入另外一个元素边界之内时触发 。

注意点：

* 上面的事件除了mouseenter和mouseleave之外，所有鼠标事件都会冒泡，也可以被取消。

同一个元素相继触发mousedown和mouseup事件，才会触发click事件。类似的只有触发两次click事件才会触发一次dblclick事件。



## 1 客户区坐标位置

使用event.clientX和clientY可以获取鼠标事件位置相距视口的水平和垂直坐标。



## 2 页面坐标位置

event.pageX和pageY可以获取鼠标事件位置在页面上面的位置。

注意点：

* 是从页面本身而不是视口的左边和顶边计算。
* 在页面没有滚动的情况下，clientX和clientY的值与pageX和pageY的值相等 。、
* IE8以及更早的版本没有页面坐标，那么可以使用页面的scrollLeft和scrollTop与clientX和clientY之和表示
  * ```
    pageX = event.clientX + document.documentElement.scrollLeft||doumeng.body.scrollLeft
    ```

## 3 屏幕坐标位置

使用event.screenX和screenY表示事件位置和整个电脑屏幕的位置。



## 4 修改键

为了区别在鼠标按下时，同时按了其他的键，DOM规定了4个属性。

* shiftKey  是否按了shift键
* ctrlKey 是否按了control键
* altKey  是否按了alt键
* metaKey  是否按了window键或者command键  IE不支持



## 5 相关元素

发生mouseout和mouseover事件时，还会涉及到更多的元素。

DOM通过event的relatedTarget表示相关元素。

* 比如鼠标从a元素移动到b，a元素触发mouseout事件，那么事件目标为a元素，相关元素为b，而b触发了mouseover事件，事件目标是b，相关元素是a元素。
* IE中针对mouseout事件使用toElement保存相关元素，mouseover事件使用fromElement保存相关元素。



## 6 鼠标按钮

只有在主鼠标按键按下才会触发click事件，但是对于mousedown和mouseup事件，则在event中存着一个button属性，在DOM中有3个值：0表示主鼠标按钮，1 表示中间的按钮，2表示左边的鼠标按钮。

IE8以及之前版本之前也提供了button属性，但是值却不一样。





## 8 鼠标滚轮事件

* mousewheel事件，这个事件可以在任何元素上触发，最终会冒泡到document（IE）和window\(其他浏览器\)。
* 对应的event对象包含标准信息之外，还包含一个特殊的wheelDelta属性，是120的倍数，当用户向后滚动滚轮时，wheelDelta是-120的倍数。向前滚动则为120的倍数。



## 9 触摸设备

针对iOS和安卓设备

* 不支持click事件
* 轻击可单机元素会触发mousemove事件，
  * 如果会导致内容变化，则不会在发生其他事情
  * 如果屏幕美誉因此发生变化，那么就会一次发生mousedown,mouseup和click事件。
* mousemove事件也会触发mouseover和mouseout事件
* 两个手指放在屏幕上且页面随手指移动而滚动时会触发mousewheel和scroll事件。







