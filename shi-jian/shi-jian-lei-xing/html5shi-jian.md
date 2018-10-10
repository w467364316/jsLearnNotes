## 1 contextmenu事件

用于表示何时应该显示上下文菜单，以便开发人员取消默认的上下文菜单和提供自定义的菜单。

**因为contextmenu事件是冒泡的，所以可以为document指定一个事件处理程序，用以处理页面中发生的所有此类事件。**

在兼容DOM的浏览器中使用event.preventDefault\(\)，IE中将returnvalue设置为false。

通常使用contextmenu来显示自定义的上下文菜单，使用onclick事件处理程序隐藏菜单。

```js
var app = document.querySelector('#app')
    addEvent(app,'contextmenu',function(event){
      event = getEvent(event);
      preventDefault(event);

      var ul = document.querySelector('#list');
      ul.style.left = event.clientX +'px';
      ul.style.top = event.clientY + 'px';
      ul.style.visibility = 'visible';
    })
```

如上所示，div\#app触发contextmenu事件，然后组织其默认行为，然后将ul设置为可见，当做菜单栏。

 

## 2 beforeunload事件

window上的beforeunload事件，为了让开发人员在页面卸载前进行一些操作。

```
addEvent(window,'beforeunload',function(){
        var message = '123';
        event.returnvalue = message;
        return message;
})
```

将event.returnvalue赋值（IE和firefox）然后将信息返回\(其他浏览器\)，这样在离开时就会出现一个弹框。



## 3 DOMContentLoaded事件

该事件在形成DOM树之后就会触发，不理会图像，外链文件等加载是否完毕。

```
addEvent(window,'DOMContentLoaded',function(){
    //进行其他交互
})
```



## 4 readystatechange事件

提供与文档或者元素加载状态的信息，

支持readystatechange的对象都有一个readystate属性，可能的值为：

* uninitialized 未初始化
* loading 对象正在加载数据
* loaded 加载完毕，对象加载数据完毕
* interactive （交互）可以操作对象，但是还没有完全加载
  * 与DOMContentLoaded大致相同时刻触发readystatechange事件。
* complete 完成 对象已经加载完毕

并不是所有的对象都会经过这几个阶段

```
addEvent(document,'readystatechange',function(){
    if (document.readyState == 'interactive') {
        alert('content loaded')
    }
})
```



script和link元素也可是触发readystatechange事件来判断是否已经加载完毕。





## 6 hashchange事件

当URL参数发生变化时通知开发人员，**必须添加到window上面**。

对应的event对象有两个属性：

* oldURL
* newURL

对于不支持oldURL和newURL的浏览器最好使用location.hash来获取当前参数列表



