## 1 load事件

当页面全部加载完毕之后（包括所有图像，js文件，css文件等外部的资源）就会触发window上面的load事件。有两种方法定义onload事件处理程序：

1. 直接使用javaScript指定处理程序
   1. ```js
      addEvent(window,'load',function(){})
      ```
2. 在body上面添加一个onload特性

   1. ```js
      <body onload='alert(123)'>
      ```
   2. 一般来说window上发生的任何事件都可以在body元素上面通过特性指定，因为HTML中访问不到window元素。

window上onload事件处理函数也会传递一个event对象，目标target为document



**图像img也可以触发load事件**，也有着两种指定方式

* img元素在设置了src属性之后就会去加载图像资源，不一定要从添加到文档后才开始下载，**所以load事件应该添加在设置src属性之前。**
* 事件处理程序中的this值为img元素



还有其他的元素以非标准的方式支持load事件。比如在IE9+，firfox，chrome，safari3+ opera等中，script也有onload事件。

* **在设置了script标签的src属性并添加到文档中时，才开始加载js文件，所以设置src和添加onload事件不用注意前后顺序。**



## 2 unload事件

在文档完全卸载后触发。也有js指定处理程序和body上面添加onunload特性两种方法指定事件处理程序。



## 3 resize事件

当浏览器窗口大小发生变化时触发resize事件。支持使用js或者在body元素定义onresize特性来指定事件处理程序。

event有一个target值，为document

关于何时触发resize事件，不同浏览器的机制不一样，firfox会在停止调整窗口大小时触发，其他浏览器会在窗口变化1像素时就触发。



## 4 scroll事件

虽然scroll事件是在windows对象上发生的，但是它实际表示的则是页面中相应元素的变化。

在混杂模式下，通过body的scrollLeft和scrollTop来监控这一变化，标准模式下使用document的scrollLeft和scrollTop监控

```
addEvent(window,'scroll',function(){
    if (document.compatMode == 'CSS1Compat') {
        alert(document.documentElement.scrollLeft)
    }else {
        alert(document.body.scrollLeft)
    }
})
```







