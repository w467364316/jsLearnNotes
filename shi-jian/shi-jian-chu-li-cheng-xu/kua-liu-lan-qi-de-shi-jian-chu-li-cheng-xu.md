基于浏览器的差异和DOM0 DOM2级的处理方式不同，跨浏览器的事件添加和删除方法使用检测然后选用恰当的方法操作即可。

```js
 function addEvent(element,type,handle) {
      if (element.addEventListener) {
        element.addEventListener(type,handle,false)
      }else if (element.attachEvent) {
        element.attachEvent('on'+type,handle)
      }else {
        element['on'+type] = handle
      }
    }

    function removeEvent(element,type,handle) {
      if (element.removeEventListener) {
        element.removeEventListener(type,handle,false)
      }else if (element.detachEvent) {
        element.detachEvent('on'+type,handle)
      }else {
        element['on'+type] = null
      }
    }
```







