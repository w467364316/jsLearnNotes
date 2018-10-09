1.某个元素支持的每种事件，都可以使用一个与相应事件处理程序同名的HTML特性来指定。这个特性的值应该是能够执行的js代码。

```
<input onclick="alert('clicked')">
```

因为值是js代码，所以不能使用未经转义的HTML语法字符，比如&lt;&gt;""等。

2.HTML元素特性值可以包含要执行的具体动作，也可以调用在页面其他地方定义的脚本。

```
<input onclick="showMessage()">
<script>
function showMessage () {
    alert('hello word')
}
</script>
```

在指定的函数中，this表示事件的目标元素。

并且在函数内部，可以像访问局部变量一样访问元素本身的成员以及document。

```
<input onclick='alert(value)' value='123' />
```





