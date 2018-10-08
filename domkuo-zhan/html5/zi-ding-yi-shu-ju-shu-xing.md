使用data-自定义属性名来为元素添加自定义属性。

通过元素的dataset属性可以访问和设置自定义属性的值。

eg:

```
<div data-myname='name1'></div>

var div = document.getElementByTagName('div')[0]
var myName = div.dataset['myname'] //访问
div.dataset['myname'] = '123'  //设置自定义属性的值
```



