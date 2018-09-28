# this

当函数被调用时会自动取得两个特殊变量：this和arguments，内部函数在搜索着两个变量时，只会搜索到其活动对象为止，因此永远不可能直接访问外部函数中的这两个变量。

```js
var name = "The Window";
var object = {
    name : "My Object",
    getNameFunc : function(){
        return function(){
            return this.name;
        };
} };
alert(object.getNameFunc()()); //"The Window"(在非严格模式下)
```



稍微修改如下：

```
    var name = "The Window";
    var object = {
        name : "My Object",
        getNameFunc : function(){
          var that = this;
            return function(){
              return that.name;
            }; }
    };
    alert(object.getNameFunc()());  //"My Object"
```

```
当然，在通过 call()或 apply()改变函数执行环境的情况下，this 就会指向其他对象。
```



