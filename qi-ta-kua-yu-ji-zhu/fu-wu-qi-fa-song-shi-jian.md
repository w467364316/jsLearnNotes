SSE创建到服务器的单向连接，服务器可以向浏览器发送任意数量的数据。服务器响应的类型必须是text/event-stream，SSE支持短轮询，长轮询和HTTP流，并且可以在断开连接时自动重新连接。

```
var source = new EventSource('xxx.php');
source.onmessage = function (event) {
    var data = event.data
}
```

EventSource实例也有一个readyState属性，0为表示正在连接，1表示打开了连接，2表示关闭了连接。

有三个事件：

* open 建立连接时触发
* message 从服务器接收到新事件时触发
  * 一般使用onmessage事件处理程序来获取传送的值
* error 在无法建立连接时触发

调用close\(\)方法可以强制的断开连接。



事件流：

服务器响应的格式是纯文本。



