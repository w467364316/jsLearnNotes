## Comment类型

注释节点使用Comment类型表示，具有一下特征：

* nodeType 为8
* nodeName 为 \#comment
* nodeValue 为注释的内容
  * nodeValue或者data访问可以获取相同的值
* parentNode可能是Document，也可能是Element
* 没有子节点

Comment类型和Text类型继承自相同的基类，因此拥有除splitText\(\)之外的所有字符串操作方法。



## 创建Comment节点

使用document.createComment\(\) 创建注释节点



