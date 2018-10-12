常见场景为文本框输入了指定的字符数量之后，自动切换下一个输入框焦点。

使用input的keyup事件处理程序，对比input.value.length和input.maxLength是否相等来决定是否自动切换到下一个输入框。

```js
 function changeFocus (event) {
      event = getEvent(event)
      var target = getTarget(event)
      if (target.value.length == target.maxLength) {
        //焦点移动到下一个
        var form = document.forms[0]
        for (let index = 0,len = form.elements.length; index < len; index++) {
          const element = form.elements[index];
          if (element === target) {
            if (form.elements[index +1]) {
              form.elements[index+1].focus()
            }
          }
        }
      }
    }
```



