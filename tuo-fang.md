利用mouedown mousemove和mouseup来实现对DOM元素的拖动。

* 直接在document添加三个鼠标的事件
* 然后在事件处理程序中针对不同的事件类型进行处理
  * mousedown事件中可以区分是否要拖动的元素，对拖动元素添加引用。
    * 在down事件中，可以添加拖动开始的自定义事件
  * mousemove中对要拖动的元素进行位置的变换。
    * move事件中可以添加正在拖动的事件
  * mouseup事件中释放拖动的引用。
    * up事件中可以添加拖动结束的事件。

注意：自行实现拖放功能，需要被拖动的元素设置了postion，一般为设置了postion:absolute样式。





