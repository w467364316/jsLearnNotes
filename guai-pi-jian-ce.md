# 怪癖检测

简单的讲就是检测浏览器的bug

比如IE8以及更早版本有一个bug。即如果某个实例属性与\[\[enumerable\]\]标记为false的原型属性同名，那么就不能被for-in循环出来。

```
var hasDontEnumQuirk = function(){
        var o = { toString : function(){} };
        for (var prop in o){
          if (prop == "toString"){
            return false;
} }
    return true;
}();
```

另外一个是safari3之前的版本会枚举被隐藏起来的属性。



