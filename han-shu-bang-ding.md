跟原生函数bin函数类似，用途为创建一个函数，可以在特定的this环境中以指定参数调用另一个函数。

很多js库实现了一个可以将函数绑定到指定执行环境的函数，一般都叫bind\(\)函数。

```
functuon bind (fn,context) {
    return function () {
        return fn.apply(context，arguments);
    }
}
```

上述代码大致描述了bind的实现方式。



ECMAScript5定义了个原生bing方法，进一步简单了操作。只需要调用bind（this值的对象）即可。

```
addEvent(btn,'click',handle.handleClick.bind(handle))
```

最好在必要时使用，因为会比普通函数有更多的开销，需要更多的内存。



