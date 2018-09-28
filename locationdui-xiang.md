# location对象

location对象提供了当前窗口加载文档有关的信息，还提供了一些导航功能。

location对象是一个特殊的对象，既是window对象的属性，也是document对象的属性。

* window.location和document.location引用的是同一个对象。



## location对象的所有属性

* hash 
  * 返回URL中（\#号后跟零或者多个字符）,如果URL不包含散列，则返回空字符串。
* host
  * 返回服务器名称和端口号
* hostname
  * 返回不带端口号的服务器名称
* href
  * 返回当前加载页面的完整URL，通过location.toString\(\)方法返回的也是完整的URL
* pathname
  * 返回URL中的目录和（或）文件名
* port
  * 返回URL中指定的端口号，如果URL不含端口号，则这个属性返回空字符串
* protocol
  * 返回页面使用的协议。通常是http:或者https:
* search
  * 返回URL中的查询字符串，以？开头
  * ?name=213&password=234





