## FormData方法

为序列化表单以及创建与表单格式相同的数据提供了遍历。

```
var data = new FromData();
data.append(key,value)
```

使用append可以添加多个键值对，然后直接传递给send\(\)方法即可。

通过对new FormData\(\)中传递表单元素，也可以直接序列化为相应的字符串，可以直接传递给send\(\)方法调用。

使用FormData时，不需要特别的设定HTTP头部信息的Content-type属性。

## 超时设定

timeOut属性和ontimeout事件监听，可以用于设定发送请求后超出一定时间后结束请求。





## overrrideMimeType\(\)方法

用于设定XMR对象对于响应会数据的MIME类型，比如服务器返回的MIME类型是''text/plain,但是实际包含的是xml，那么就可以通过修改XMR.overrideMimeType\('text/xml'\)来改变。



