对于XMR规定了6个进度事件：

* loadstart  接受响应数据的第一个字节触发
* progress 接受响应期间持续不断的触发
* error  出现错误时
* abort 因为调用abort\(\)方法而终止连接时触发
* load 在接受完整的响应数据时触发
* loadend  在通信完成或者触发error,abort或者load事件后触发 。

常用的为load事件和progress事件。



## load事件

只要浏览器接收到服务器的相应，不管什么状态，都会触发load事件，所以可以用来替换onreadystatechange事件和readystate的判断，但是仍然需要判断status。



## progress事件

会在接受数据期间周期性的触发，而onprogress事件处理程序会接受到一个event对象，其target属性是XHR对象，同时还有其他几个属性：

* lengthComputable 进度信息是否可用
* position 表示已经接受的字节数
* totalsize表示根据Content-length响应头部确定的预期字节数。

那么根据这些信息，就可以创建一个进度进度指示条。

**progress事件也需要在open\(\)方法前定义。**



