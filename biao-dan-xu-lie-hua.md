将表单的内容发送到服务器的时候，有需要对表单进行一下序列化的操作。可以利用表单字段的type属性，连同name和type属性一起实现对表单的序列化。

主要的规则：

*  对表单字段的名称和值进行URL编码，使用和号\(&\)分隔。

*  不发送禁用的表单字段。

*  只发送勾选的复选框和单选按钮。

*  不发送type为"reset"和"button"的按钮。

*  多选选择框中的每个选中的值单独一个条目。

*  在单击提交按钮提交表单的情况下，也会发送提交按钮;否则，不发送提交按钮。也包括type

  为"image"的&lt;input&gt;元素。

*  &lt;select&gt;元素的值，就是选中的&lt;option&gt;元素的value特性的值。如果&lt;option&gt;元素没有

  value特性，则是&lt;option&gt;元素的文本值。



