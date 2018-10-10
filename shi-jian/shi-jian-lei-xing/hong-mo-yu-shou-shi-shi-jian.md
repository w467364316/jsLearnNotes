W3C定制了Touch Events规范，用于移动端的浏览器的一些事件。

## 1 触摸事件

* touchstart 手指触摸屏幕时触发，有一个只手指在屏幕上了也会触发
* touchmove 手指在屏幕上滑动时连续的触发
* touchend 手指从屏幕上移开时触发
* touchcancle 系统停止跟踪触摸时触发

这几个事件都会冒泡，也都可以取消。每个对应的event对象都有鼠标事件中的常见属性，clientx,clienty等。

除了常见的之外，还有一些跟踪触摸的属性：

* touches 当前跟踪的触摸操作的Touch对象的数组
* targetTouches 特定于事件目标的Touch对象的数组。
* changeTouches 表示自上次触摸以来发生了什么改变的Touch对象的数组。

每个Touch对象包含下列属性：

* clientX
* clientY
* identifier
* pageX
* pageY
* screenX
* screenY
* target



## 2 手势事件

主要有三个手势事件：

* gesturestart  一个手指已经按在屏幕上，另外一个手指又触摸屏幕时触发
* gesturechange 当触摸屏的任何一个手指的位置发生改变时。
* gestureend 当任何一个手指从屏幕上面移开时触发

只有两个手指都触摸到事件的接受容器曹辉触发这些事件。在一个元素上设置事件处理程序，意味着两个手指必须同时位于该元素的范围之内，才能出发手势事件。由于冒泡，所以可以在文档上处理所有的手势事件。此时事件的目标就是两个手指都位于其范围内的那个元素。

触摸事件和手势事件之间存在某种关系。当一个手指放在屏幕上时，会触发touchstart事件。如果另一个手指又放在了屏幕上，则会先触发gesturestart事件，随后触发基于该手指的touchstart事件。如果一个或两个手指在屏幕上滑动，将会触发gesturechange事件。但只要有一个手指移开， 就会触发gestureend事件，紧接着又会触发基于该手指的touchend事件。

对应的event对象有两个属性：

* rotation 表示手指变化引起的旋转角度，从0开始，逆时针为负，顺时针为正。
* scale 表示手指变化引起的距离变化，从1开始



