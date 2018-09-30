# Text类型

文本节点由Text类型表示，包含的是可以照字面解释的纯文本内容。可以包含转义后的HTML字符，但是不能包含HTML代码，具有以下特征：

* nodeType为3
* nodeName 为\#text
* nodeValue为包含的文本
  * 可以通过nodeValue或者data属性访问， 返回的值 是一样的。
* parentNode为一个Element
* 没有子节点
* splitText\(offset\) 从offset处的位置将当前文本节点分割成两个节点，返回后面的一个 文本节点
* length 保存着节点中字符的数量

再向DOM文档中插入文本之前，都会先对其进行HTML编码，小于号，大于号等都会被转义



## 创建文本节点

* document.createTextNode\(\)创建新文本节点
  * 创建时也会为其设置ownerDocument属性



## 规范化文本节点

Element元素调用normalize\(\)方法会将其其元素中多个文本节点合并成一个文本节点。



## 分别文本节点

splitText\(\)方法 将当前文本节点分割成两个文本节点。并返回后面的文本节点。





