## 1 orientationchange事件

移动safari的window有一个orientation属性，可能包含3个值：

* 0 比表示肖像模式
* 90表示向左旋转的横向模式
* -90表示向右旋转的横向模式

只要用户改变了设备的查看状态，就会触发orientationchange事件。此时event对象不包含任何有价值的信息，因为唯一相关的信息可以通过window.orientation访问到。



## 2 MozOrientation 事件

Firefox浏览器为检测设备方向引入的一个新事件。也是在window上触发的。

对应的event有三个属性：x y z值都是介于1和-1之间



## 3 deviceorientation事件



## 4 devicemotion事件

告诉开发人员设备什么时候移动



