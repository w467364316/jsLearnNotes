## select\(\)方法

手动调动select\(\)方法会选择文本框中的所有文本

## select事件

在选择了文本框中的文本时，就会触发select事件，调动select\(\)方法时也会触发select事件。

## 取得选择的文本

HTML5规范了俩个属性selectionStart和selectionEnd来表示选择文本的范围。

IE8以及之前版本不支持，但是提供另外一个方案：

* 有一个document.selection对象，保存着整个文档范围内选择的文本信息，适合和select事件引起使用：

```
function getSelectedText (textbox) {
    if (typeof textbox.selectionStart == 'number') {
        return textbox.value.subString(texbox.selectionStart,textbox.selectionEend)
    }else if (document.selection) {
        return document.selection.createRange().text;
    }

}
```

## 选择部分文本

* HTML5定义了selectionRange方法，接受两个参数，要选择的第一个字符的索引和最后一个字符的索引（类似substring方法的两个参数）。
* IE8以及之前使用文本框上使用的createTextRange（）创建一个范围，然后使用moveStart（）和moveEnd这两个范围将范围移动到底。最后调用select\(）方法

  * 但是调用之前必须使用collpase（）将范围折叠到文本框开始的位置
  * ```
    textbox.value = 'hello world'

    var range = textbox.createTextRange();

    range.collapse(true)
    range.moveStart('character',0)
    range.moveEnd(‘character’,textbox.value.length)
    range.select();
    ```

**要选择文本后看到 效果，必须让文本框获取焦点，所以可以在后面或者前面调用focus\(\)方法。**

