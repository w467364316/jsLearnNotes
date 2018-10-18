相比函数绑定，柯里化是在函数被调用是，返回的函数还需要设置一些传入的参数，大致的表现形式为：

```
function cury (fn) {
    var args = Array.prototype.slice.call(argments,1)
    return function () {
        var innnerArgs = Array.prototype.slice.call(argumemnts);
        var finalArgs = innerArgs.concat(arguments);
        return fn.apply(null,finalArgs);
    }
}
```

ECMAScript的bind\(\)方法中也实现了函数柯里化，只要再this的值之后在传入另一个参数即可。

```js
var handler = {
        message: "Event handled",
        handleClick: function(name, event){    //注意此处的event参数在后面。
            alert(this.message + ":" + name + ":" + event.type);
}
    };
    var btn = document.getElementById("my-btn");
EventUtil.addHandler(btn, "click", handler.handleClick.bind(handler, "my-btn"));

```





