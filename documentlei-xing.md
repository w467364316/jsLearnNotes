# Document类型

JS通过Document类型表示文档，浏览器中，document对象是HTMLDocument\(继承自Document类型\)的一个实例，表示整个HTML页面，而且document对象是window对象的一个属性，所以可以作为一个全局对象访问。

Document节点具有下列特征：

* nodeType的值为9
* nodeName值为\#document
* nodeValue值为null
* parentNode值为null
* ownerDocument的值为null

## 文档的子节点

* document.documentElement获取&lt;html&gt;元素或者通过document,childNodes\[0\]访问html元素
* document.body获取body元素
* document还有一个可能的子节点为DocumentType，通常将&lt;!DOCTYPE&gt;标签看成一个与文档其他部分不同的实体。可以通过doctype属性访问它的信息。
  * 因为不同的浏览器对于doctype的解析不相同，所以该属性很少使用。
* 注释节点，在不同的浏览器中解析也是不相同的。
* 多数情况下不同document的appendchld和removechild replaceChild方法，因为文档类型是只读的

## 文档信息

作为HTMLDocument的一个实例，document拥有一些Document对象没有的属性

* document.title 表示title标签中的内容
  * 修改titled额值不会改变&lt;title&gt;元素
* URL 表示完整的URL
* domin表示URL中的域名
  * 
* referrer 来源网页的URL

## 查找元素

* getElementById\(\) 根据元素的id匹配来获取相应的元素
  * 需要大小写严格区分，IE8以及较低版本不会区分大小写
  * 如果页面中多个ID值一样的元素，那么该方法只会返回第一次出现的元素。
* getElementByTagName\(\) 接收元素的标签名
  * 返回一个类似NodeList的对象，为HTMLCollection对象，
    * 与NodeList对象类似的也可以使用item\(index\)和【index】访问具体的项
    * 通过length获取数据项的数量
    * nameItem\(\) 使用这个方法可以通过元素的name特性去的集合中的项。
    * HTMLCollection还支持使用按名称访问项
    * ```
      <img name='myImage'/>
      var imags = document.getElementByTagName('img')
      images['myImage']可以获取上面的img标签
      ```

      方括号中传入数值会默认调用item\(index\)方法，传入字符串会默认调用nameItem\(\)方法
* 要获取文档中的全部元素，可以调用document.getElement\('\*'\)获取文档中全部的元素。

* getElementByName\(\) 返回带有给定name特性的所有元素。常用的是使用该方法取得单选按钮

## 特殊集合

* document.anchors 包含文档中所有带name特性的&lt;a&gt;元素
* .applets 获取文档中全部的applets元素
* .forms 获取文中全部的form
* images 获取文档中全部的img元素
* links获取文档中全部的带href特性的a元素



### DOM一致性检测

因为DOM分为多个级别，因此浏览器需要进行检测实现了DOM的那些部分

使用document.implementation.hasFeature\(\) 检测

* 第一个参数为要检测的DOM功能名称
* 第二个参数为版本号

## 文档写入

document.write ,writen,open,close 四个方法

* write和writen接受一个字符串，可以在页面中动态的加入内容
  * 方法中还可以引入外部的script资源
    * ```
      <script type='text/javascript'>
      注意字符串中最后的</script>需要进行转义为<\/script>，
      不然会被解析为外部script标签的结束
          document.write('<script type='text/javascript' src='xxxx.js'>
                  <\/script>')
      </script>
      ```
  * 等到页面全部加载完成之后，在调用write方法，会重写整个页面内容





