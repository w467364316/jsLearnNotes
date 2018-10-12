## 1 屏蔽字符

```js
 EventUtil.addHandler(textbox, "keypress", function(event){
        event = EventUtil.getEvent(event);
        var target = EventUtil.getTarget(event);
        var charCode = EventUtil.getCharCode(event);
        if (!/\d/.test(String.fromCharCode(charCode)) && charCode > 9 &&
                 !event.ctrlKey){
          EventUtil.preventDefault(event);
    }
});
```

上述代码使用keyperss事件，然后对其charcode进行正则匹配，同时避免输入的是非字符串按键，和防止按了ctrl+c v等按键。



## 2 操作剪贴板

一下6个剪切板事件：

* beforecopy 发生复制钱
* copy 发生复制操作时
* beforecut 发生剪切操作前

* cut 发生剪切操作
* beforepaste  发生粘贴操作前
* paste 发生粘贴操作

注意点：

* **三个before事件可以在向剪贴板发送数据，或者从剪贴板获取的数据之前修改数据。**
* 取消复制 剪切 粘贴只能在copy cute paste方法中取消行为

要获取设置清除剪贴板的数据，可以使用clipboarddata对象，IE中使用window.clipboardData获取，其他的使用event.clipboardData获取。

它有三个方法：

* setData\(\)
  * 第一个参数为数据类型，第二参数为放在剪贴板中的文本。
  * 第一个参数在IE中支持text,URL，但是chrome仍然只是支持MIME类型，而且safari chrome 的setdata方法不能识别'text'类型。
* getData\(\)
* clearData\(\)

```js
综合方法：   
 function getClipboardText (event) {
      var clipboardData = event.clipboardData || window.clipboardData;
      return clipboardData.getData('text');
    }

    function setClipboardText (event,value) {
      if (event.clipboardData) {
       return event.clipboardData.setData('text/plain',value)
      }else if (window.clipboardData) {
        return window.clipboardData.setData('text',value)
      }
    }
```







