重置表单的集中方法：

1. 使用type特性值为reset的&lt;input&gt;和&lt;button&gt;都可以重置按钮
   1. 重置表单时，所有表单字段都会恢复到页面刚加载完毕时的初始值。
   2. 单击重置按钮重置表单时，会触发reset事件。利用这个操作可以取消重置操作。（调用event.preventdefault\(\)）
2. 也可以通过调动reset\(\)方法调用。与submit\(\)方法不同的是调用reset\(\)方法也会触发reset事件。



