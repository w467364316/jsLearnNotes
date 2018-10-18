基于js的机制，在处理setInterval\(\)的函数，当代码队列中存在未执行的函数时，就算到了间隔时间点也不会往队列中添加函数。

为了避免这个缺点，我们可以使用setTimeout的链式调用来解决：

```
setTimeout(function(){
    setTimeout(arguments.callee,interval)
},interval)
```





