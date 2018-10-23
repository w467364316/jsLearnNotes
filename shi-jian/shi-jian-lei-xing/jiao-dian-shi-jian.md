## 焦点事件

在页面元素获取或者失去焦点时触发。利用这些事件并与document.hasFocus\(\)与document.activeElement配合，可以知晓用户在页面上的行为。

主要有下列的焦点事件：

* blur 失去焦点时触发 不冒泡
* focus 获得焦点时触发，不冒泡
  * **尽管blur和focus不支持冒泡，但是仍然可以在捕获阶段侦听他们。**
* focusin 获取焦点时触发，冒泡
* focusout 获取焦点时触发，冒泡

焦点从元素a移动到元素b的大致事件过程为：

1. focusOut 在失去焦点的a元素触发
2. focusin 在获取焦点的b元素触发
3. blur 在失去焦点的a元素触发 
4. focus在获得焦点的b元素触发



