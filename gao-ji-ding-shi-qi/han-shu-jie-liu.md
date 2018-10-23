函数节流的基本思想是指，某些代码不可以在没有间断的情况下重复执行。

基本的表现形式为：

```js
var processor = {
        timeoutId: null,
        //实际执行处理的方法
        performProcessing: function(){
        },
        //初始处理的方法
        process: function(){
            clearTimeout(this.timeoutId);
            var that = this;
            this.timeoutId = setTimeout(function(){
                that.performProcessing();
            }, 100);
} };
processor.process()
```

这个模式可以用throttle\(\)函数来简化：

```
function throttle (method,context) {
    clearTimeout(method.timeId)
    method.timeId = setTimeout(function(){
        method.call(context);
    },100)
}
```

比如在window的onresize事件中，如果要操作DOM的话，那么就可以使用函数节流的方式，**这样就可以避免函数的重复无间隔调用，实现在指定的时间间隔内有且仅有一次函数调用。**

