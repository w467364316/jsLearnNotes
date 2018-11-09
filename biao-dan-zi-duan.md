表单元素可以像原生DOM方法访问表单元素，此外每个表单都有elements属性，是表单中所有表单元素的集合，列如input textarea buton fieldset等。

elements

* 可以通过elements\[inex\]或者elements\[name\]来获取表单中的元素
* 如果有多个name一样的表单元素，那么elements\[name\]只会获取到第一个。

## 1 共有的表单字段（元素）属性

* disable 布尔值，当前字段是否被禁用
* form 指向当前所在的表单的指针，只读
* name 当前字段的名字
* readOnly 布尔值，表示当前字段是否只读
* tabIndex 表示当前字段的切换符号
* type 当前字段的类型，如‘checKbox’，‘radio’等。
* value 当前字段被提交给服务器的值，对于文件字段来说，这个属性包含着计算机中的路径。

除了form属性之外，其他的属性都可以进行更改。

常用的方式，在表单提交之后，禁用提交按钮

```
addEvent(form,'submit',function(){
    var btn = form.elements['btn-submit']
    btn.disabled = true;
})
```

注意：不能通过onclick来触发上述代码中的事件，因为不同的浏览器之间存在时差。

除了fieldset，所有的表单字段都有type属性，input元素的值等于HTML type特性的值。其他的元素type稍有区别。

## 2 共有的表单字段方法

* focus\(\)将焦点移动到目标元素上
* blur\(\) 将焦点从目标元素移走
* HTML5新增了一个autofocus属性，在支持的浏览器中只要设置了该属性，不用js就能自动把焦点移动到相应字段。

## 3 共有的表单字段事件

* blur
* focus
* change
  * **对于input和textare，在他们失去焦点且value值改变时触发。对于select元素，再起选项改变时触发。**

当用户改变了当前字段的焦点，或者是调用了focus或者blur方法，都会触发focus和blur事件。

