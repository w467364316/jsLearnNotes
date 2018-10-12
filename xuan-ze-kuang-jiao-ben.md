选择框主要通过select和option元素创建，为了方便交互，除了表单字段共有的属性之外，HTMLSelectElement还提供了其他的属性和方法：

* add\(newOption,relOption\) 在参照的option relOption之前插入新的option
* remove\(index\)  删除指定index位置处的option
* selectIndex 基于0的选中项的索引，没有选择则值为-1，对于支持多选的空间，只保存选中项的第一项的索引。
* options select中全部的option元素，一个HTMLCollection对象。
* size 选择框中可见的元素，等价于HTML中的size特性。
* multiple： 布尔值，表示是否允许多项选择。

option元素都有一个HTMLOptionElement对象，有下列的属性：

* index 当前选项在options集合中的索引。
* label 当前选项的标签
* text 选项的文本
* value 选项的值
* selected 选项是否被选中。



对于select元素的value值：

* 如果没有选中的option元素，则value为空字符串
* 选中的option元素有value属性，为空或者有字符串，则select的value为该字符串
* 选中的option元素没有value特性，则select的value值该option元素的文本。
* 如果是多选，那么就按照前面的规则选取第一个选中项的值。





