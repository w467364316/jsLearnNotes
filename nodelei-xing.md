# Node类型

DOM1定义了一个Node接口，该接口由DOM中所有节点类型实现。在js中是作为Node类型实现的。js中所有节点类型都继承自Node类型，因此所有节点类型都共享着相同的基本属性和方法。



## Node属性

* nodeType属性， 每一个节点多有一个该属性，表明节点的类型。节点的类型有12种，任何节点类型必居其中之一。
  * 一般在判断节点类型的时候，为了兼容IE浏览器，通常将节点的nodeType和数值进行比较。
    * ```
      if(someNode.nodeType === Node.ELEMENT_NODE) {
          是元素节点，但是该方法在IE中无效
      }

      if (someNode.nodeType === 1) {
          //适用于所有的浏览器
      }
      ```
* nodeName和nodeValue

  * 对于元素节点，访问nodeName会返回元素标签名，nodeValue会返回null

  * 对于类似文本节点，访问nodeName会返回\#text，访问nodeValue会返回文本节点内的文本

* 以下为节点之间的关系相关的属性

* childNodes 保存着一个NodeList对象，是一个伪数组，保存着该结点的全部子节点

  * 可以通过方括号\[index\]或者item\(index\)的方式来访问子节点。

  * NodeList对象是实时更新的，不是在第一访问后就固定不变的。

  * 将childNodes转换为数组，对于IE8之前的浏览器和其他浏览器有着区分

    * ```
      function converToArrY (somNode) {
          var array = null 
          try {
               array = [].slice.apply(somNode.childNodes,0)   
          }catch (error) {
          //IE8以及更早的版本由于是使用COM对象，不能像js一样运用，只能通过枚举来获取全部的成员。
              for (var i = 0;i<someNode.childNodes.length;i++) {
                  array.push(someNode.childNodes[i])
              }
          }
          return aray;
      }
      ```

  * **并不是全部类型的节点都会有子节点**

* parentNode 表示该节点的父节点

* previousSibling和nextSibling分别保湿该结点的上一个兄弟节点和下一个兄弟节点

* firstChild和lastChild表示第一个子节点和最后一个子节点

  * 如果没有节点的话，那么访问这两个属性返回null



## 操作节点的方法

* appendChild 向childNodes的末尾添加一个节点， 接受一个参数为要添加的新节点，返回被添加的节点。
  * 添加之后，父节点以及子节点的关系指针都会相应的更新。
* insertBefore\(\) 接受两个参数，将要被插入的节点和参照的节点， 会在参照的节点钱插入节点，返回被插入的节点 。
  * 如果参照节点参数是null，那么等于在末尾插入节点，和appendChild等同
* replaceChild（）接收两个参数。第一个参数为要替换的节点，第二个参数为被替换的节点
  * 被替换的子节点会被返回
  * 使用replaceChild\(\)掺入一个子节点，该节点的素有关系指针都会从被他替换的节点复制过来。被替换的节点任然还在文档中，但是它再文档中已经没有了自己的位置。
* removeChild\(\) 参数为要删除的节点
  * 返回被删除的子节点
  * 节点被删除后，仍然在文档中，只是文档中没有了自己的位置。
* cloneNode\(\) 复制节点，接受一个是否深复制的参数
  * 参数为true，即为深拷贝，会复制节点和其整个子节点树，参数为false，为浅拷贝，只会复制节点自身
* normalize\(\) 唯一的作用就是处理文档树中的文本节点
  * 如果文档树中有空文本节点，调用该方法会删除空的文本节点
  * 如果文档中有相连的文本节点，调用该方法会合并为一个文本节点



