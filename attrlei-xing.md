# Attr类型

元素的特性以Attr类型表示，在所有的浏览器中都可以访问Attr类型的构造函数和原型。

主要存在于元素的attributes中

具有下列特性：

* nodeName为特性的名字
* nodeType 值为2
* nodeValue值是特性的值
* parentNode的值为null

Attr对象具有三个属性，name，value，specified，

* sepcified可以用于筛选指定的特性

使用document.createAttribute\('name'\)创建一个特性节点

然后可以通过value等赋值

```
var attr = document.createAttribute('aligin')
attr.value = 'left'
element.setAttributeNode(attr)
element.getAttributeNode('aligin').value // left
element.getAttribute('align')  // left
element.attributes['align'].value
```

## 注意点

* 将创建的特性添加到元素，必须使用元素的setAttibuteNode\(\)方法
* 使用element.getAttributeNode\(\) 返回的是特性节点，使用element.getAttribute\['name'\]返回的是特性的值。



