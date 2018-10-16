对于window来说，只要是发生了错误，不管是不是浏览器生成的，都会触发window的error事件，并执行相应的事件处理程序。

window的error事件只支持DOM0级的方式，并且没有event对象返回，只有返回三个参数：错误信息message，错误所在的URL和行号。其中message是常用的。

```js
window.onerror = function (message,url,line) {

} 
```

理想情况下，不应该使用window的error方法，这个是避免浏览器报告错误的最后一道防线。

图像也支持error事件，同样遵循DOM格式，在img元素的src加载图像失败时就会触发改事件。



