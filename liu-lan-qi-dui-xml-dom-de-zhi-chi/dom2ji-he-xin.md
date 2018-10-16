DOM2级在document.implementation中引入了createDocument（）方法。创建一个空白文档，

一般使用方式为：

```
var xmldom = document.implementation.createDocment('','root',null)
```

检查浏览器是否支持DOM2级的XML：

```
var hasXmlDom = document.implementation.hasFeature('xml','2.0')
```





