对于XMR，进行跨域访问时，使用open\(\)中的url为绝地地址，不是相对地址，就可以进行跨域访问。

但是也有一些限制：

* 不能设置自定义头部
* 不能发送和接受cookies
* 调用getAllResponseHeaders\(\)会返回空。



