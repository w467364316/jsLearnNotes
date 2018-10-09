```js
    //获取事件对象
    function getEvent (event) {
      return event?event:window.event;
    }

    //获取事件目标
    function getTarget (event) {
      return event.target || event.srcElement;
    }

    //阻止默认行为
    function preventDefault (event) {
      if (event.preventDefault) {
        event.preventDefault()
      }else {
        event.returnValue = false;
      }
    }

    //阻止冒泡
    function stopPropagation (event) {
      if (event.stopPropagation) {
        event.stopPropagation()
      }else {
        event.cancleBubbles = true;
      }
    }}
```

IE不支持事件捕获，因此这个方法在跨浏览器的情况下，也只能用来阻止 事件冒泡。



