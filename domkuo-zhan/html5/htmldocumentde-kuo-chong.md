## 1 document.readyState

表示document的加载状态:

* loading 正在加载文档
* complete 已经加载完

跟document.onload判断文档加载完毕类似



## 2 document.compatMode 兼容模式

主要分为两种：

* CSS1Compat
* BackCompat



## 3 head属性

新增了document.head属性获取head元素

获取head元素可以采用如下方法：

```js
var head = document.heade || document.getElementByTagName('head')[0]
```



