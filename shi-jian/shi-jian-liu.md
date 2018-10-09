## 事件流

比如点击了一个组同心圆的圆心，那么到底点击的是哪一个圆呢？由此衍生出两种事件事件流的概念：

* 事件冒泡流
* 事件捕获流



## 事件冒泡流

事件开始时由具体的元素接受，然后逐级往上层传播直到不具体的节点（文档）。

```js
<!DOCTYPE html>
    <html>
    <head>
        <title>Event Bubbling Example</title>
    </head>
    <body>
        <div id="myDiv">Click Me</div>
    </body>
    </html>
```

如果单击了div，那么冒牌流传播顺序为：

1. div
2. body
3. html
4. document

IE9，firfox等其他浏览器会将事件一直冒牌到window对象



## 事件捕获流

事件一开始有不确定的节点接收，然后逐层的往下传递直到目标节点。

```
<!DOCTYPE html>
```

```js
    <html>
    <head>
        <title>Event Bubbling Example</title>
    </head>
    <body>
        <div id="myDiv">Click Me</div>
    </body>
    </html>
```

如果单击了div，那么捕获流传播顺序为：

1. document
2. html
3. body
4. div

IE9，firfox等其他浏览器从window对象开始捕获事件



## DOM事件流

DOM2级事件规定事件流包括3个阶段：

1. 事件捕获阶段
2. 目标阶段
   1. 目标接收到事件
3. 事件冒泡阶段

**虽然DOM2级事件规定在捕获阶段不会涉及事件目标节点，但是其他浏览器都会在捕获阶段解除事件对象上的事件。所以导致有两个机会在目标对象上面操作事件。**





