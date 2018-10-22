如果某个脚本会运行过长的时间，那么浏览器可能弹出对话框提示用户是否继续，因为js是单线程，那么脚本运行时间越长，意味着用户不可操作的时间越长。

那么如果一个运行时间长的处理满足两个条件：

1. 不是必须同步进行的，不会造成其他运行的阻塞。
2. 数据不必按顺序完成。

那么就可以使用数组分块技术。小块小块的处理数据，基本思路为为要处理的项目创建一个队列，然后使用定时器取出下一个要处理的项目进行处理，接着在设置另外一个定时器：

```
setTimeout (function(){
    var item = array.shift()
    process(item);
    if (array.length>0) {
        setTimeout(arguments.callee,100)
    }
},100)
```

上述代码中的array类似是一个代办事项列表。

数组分块的重要性在于他可以将多个项目的处理在执行队列上分开，在每个项目处理之后，给与其他的浏览器处理机会运行，这样能避免长时间运行脚本的错误。






