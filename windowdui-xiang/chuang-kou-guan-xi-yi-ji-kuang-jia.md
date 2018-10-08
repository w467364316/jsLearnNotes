# 窗口关系以及框架

如果页面使用框架，则每个框架都有自己的window对象，而且保存在frames集合中，可以直接通过索引值访问相应的window对象，每一个windows对象都有一个name属性，其中包含了框架的名称。

```
<html>
    <head>
        <title>Frameset Example</title>
    </head>
    <frameset rows="160,*">
        <frame src="frame.htm" name="topFrame">
        <frameset cols="50%,50%">
            <frame src="anotherframe.htm" name="leftFrame">
            <frame src="yetanotherframe.htm" name="rightFrame">
        </frameset>
    </frameset>
</html>
```

如上述代码所示为一个框架集合。

* top对象，永远表示最外层的框架，也就是浏览器窗口。
  * 因此可以使用top.frames\[index\]代替window.frames\[index\]来获取window对象
* parent对象，表示当前框架的上一层框架
* self对象，始终指向window，所以self和window可以相互使用。

注意： 如果有多个框架，也就是有多个Global对象，那么每个框架都有一套自己的构造函数，这些构造函数一一对应，但是并不相等。

