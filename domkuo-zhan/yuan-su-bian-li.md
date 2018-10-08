使用chldNodes firstChild lastChild时 ，在众多浏览器中是不会区分文本和注释节点的，所以增加了几个API：

* childElementCount: 表示子元素的个数（比包括文本节点和注释）
* firstElementChild 第一个子元素节点
* lastElementChild  最后一个子元素节点
* previousElementSibling 指向前一个兄弟元素
* nextElementSibling 指向后一个兄弟元素





