一般服务器会对任意的HTTP请求发送Set-Cookie HTTP头作为响应的一部分。

浏览器会存储这样的会话信息，并在这之后，通过每个请求添加Cookie HTTP头将信息发送给服务器。

## Cookie的限制

cookie是绑定在特定的域名下的，设置一个cooke后，再给创建它的域名发送请求时，都会包含这个cookie。

浏览器不一样，cookie总数限制不一样。

大多数浏览器对cookie整体的大小限制是4095b。

## cookie的构成

* 名称 虽然cookie是不区分大小写的，但是最好区分一下，方便和服务器进行交互。必须进行URL编码
* 值  需要进行URL编码
* 域 可以指定子域和全域
* 路径
* 失效时间  值为GMT格式的日期
* 安全标志

在发送给服务器时，name值对儿会被发送，其他的不会被发送。

## JavaScript中的cookie

* 读取document.cookie返回当前页面可用的所有cookie的字符串，一系列由分号隔开的键值对。
* **利用document.cookie设置cookie时，并不会覆盖已有的cookie，除非name一样，只会加入到document.cookie中。**
* 如果要删除某个name的cookie，可以利用设置对应name cookie的value值为空。

## 子cookie

为了绕开单域名名下的cookie数限制，可以使用子cookie方法，大致形式如下：

```
name=name=value1&name2=value2&name3=value3
```

那么在封装方法的时候，就需要区别对待。

