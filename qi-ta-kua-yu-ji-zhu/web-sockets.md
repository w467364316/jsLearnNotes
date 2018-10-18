使用webSocket创建连接之后，协议会从HTTP升级到Web Socket协议。连接也将从http://变为ws://。

```
var socket = new WebSocket('ws://xxx.xxx.com')
```

必须传入绝对URL，同源策略对Web Socket不适用。



## 发送和接受数据：

* 使用send\(\)发送数据，只能发送纯文本，所以如果是对象，就要使用JSON.stringify\(\)序列化处理。
* 当接收到数据时，会触发对象的message事件，传送的数据在event.data中。



## 其他事件

* open 事件
* error 事件
* close 事件

只能使用DOM0级的方式定义事件处理程序。





