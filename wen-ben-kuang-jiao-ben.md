## input元素

* type特性设置为text，表示文本输入框
* 通过设置size属性，指定文本框能够显示的字符数
* 通过value设置文本框的初始值
* 通过设置maxlength特性用于指定文本框可以接受的最大字符数。

```
<input type='text' size='25' maxlength='50' value='simple value' />
```

## textarea元素

* 使用row指定字符显示的行数，使用cols特性指定一行显示多少个字符。
* 与input不同的是默认值必须写在标签中间
* 使用value获取其中的值
* 不能指定最大字符数量

```
<textarea rows='5' cols='5'>simple value</textarea>
```



