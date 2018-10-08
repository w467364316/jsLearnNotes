# getElementByClassName\(\)

通过传入一个或者多个类名，来寻找匹配的元素，返回的是一个NodeList实例



# classList属性

H5为每个元素都增加了classList属性，用于添加，删除，替换类名。

classList是DOMTokenList实例，也是一个length包含了个数的属性，获取每个元素也可以使用item\(\)或者方括号直接获取。

还定义了其他的一些方法：

* add\(value\) 添加类名到classList中
* remove\(value\) 删除指定的类名
* toggle（value） 切换类型，存在则删除，不存在则添加
* contains\(value\) 是否包含类名



