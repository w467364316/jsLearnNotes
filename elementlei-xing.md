# Element类型

Document类型是表示文档的，Element类型表示HTML或XML元素，提供的对元素标签名，子节点以及特性的访问。Element节点具有以下特征：

* nodeType的值为1
* nodeName 值为元素的标签名
* nodeValue的值null
* parentNode可能是Document或者Element
* childNodes可能是其他的一些节点

访问元素的标签名可以使用nodeName或者tagName。

```
<div id='app'></div>
var div = document.getElementById('app')
div.nodeName  //DIV
div.tagName //DIV
```

HTML中，标签名始终是以大写表示。在XML中标签名始终会与源代码中的保持一致。

所以在比较时最好是转换为**小写或者大写**，然后在进行比较。

```
if (element.tagName.toLowerCase() === 'div') {
    //是div标签
}
```

## 1 HTML元素

所有的HTML元素都是有HTMLElement类型表示或者它的子类表示。继承了Element类型并添加了一系列方法。添加的属性分别对应为每一个HTML元素中都存在的下列特性：

* id 对应元素的id特性
* title 有关元素的说明，一般通过工具条显示
* lang 元素内容语言代码
* dir 语言的方向，对应元素的dir特性
* className 对应元素的class特性

以上的特性都可以用来获取或者修改相应特性的值。

## 2 获取特性

操作特性的方法主要有三个

* getAttribute\(\)
* setAttribute\(\)
* removeAttribute\(\)

### 2.1 getAttribute\(\)

* 传递给该方法的参数需要和元素的特性名一样，给定的特性不存在，则会返回null
* 通过该方法也可以获取自定义的特性。
* 特性的名称是不区分大小的，而且H5中自定义特性应该加上data-前缀以便于验证

2.1.1 元素的所有特性，也都可以通过DOM元素本身的属性类访问。HTMLElement也会有5个属性与相应的特性一一对应。 **但是**，**只有公认的特性才会以属性的形式添加到DOM对象中**。

* 但是在IE中会为自定义的特性创建属性。

2.1.2 有两种特殊的特性，虽然有对应的属性名，但是属性名获取和getAttribute获取的值不一样.

* style特性，直接用属性.style获取的是对象，但是使用getAttri方法获取的是一个css文本
* onclick这样的时间处理程序，在元素上使用时，onclick等包含的是js代码。如果通过getAttri方法获取会返回对应代码的的字符串。但是属性的形式.onclick形式访问返回的是一个js函数。

所以一般不适用getAttribute来获取，而是使用对象的属性获取特性。

### 2.2 设置特性 setAttribute\(\)

接受两个参数：要设置的特性和值

* 如果特性已经存在，则覆盖
* 如果特性感不存在，则添加上

对于公认的特性来说，也可以直接通过对象的属性来设置，但是自定的特性不能通过属性的形式来设置，只能通过setAttr的形式设定。

```
var div = document.getElementByTagName('div')[0]
div.className = 'top'
div.my_color = 'red'

console.log(div.getAttribute('id')) //top
console.log(div.getAttibute('my_color')) //null 自动的特性不能通过对象属性的形式设置
```

* 但是自定义属性在IE中会被当做元素的特性

### 2.3 removeAttribute\(\)

彻底删除元素的特性。不常用，但是在序列化DOM元素时，可以用来指定要包含哪些特性

## 3 attributes属性

attributes属性中包含一个NamedNodeMap，与NodeList类似，也是一个动态的集合，元素的每一个特性都是一个attr节点，每个节点保存在NamedNodeMap中，NamedNodeMap对象的方法：

* getNamedItem\(name\)：返回nodeName属性等于name的节
* setNamedItem\(node\): 传入一个特性节点，添加到NamedNodeMap
* removeNamedItem\(name\)  移除nodeName为name的节点

  * 返回值为移除的特性节点

* item\(pos\): 返回位于数字pos位置的节点

attr节点的属性：

* nodeName 特性名
* nodeValue 特性值
* specified 用于过滤IE中specified为false的特性节点

一般在遍历元素特性时，使用该方法可以有效地得到特性字符串

## 4 创建元素

使用document.createElement（）创建元素，参数可以为标签名或者直接传入一个字符串表示的标签

```
document.createElement('div')
document.createElemnet('<div clas=\'app\'></>')
```

## 5 元素的子节点

元素可以有任意数组的子节点和后代节点，子节点可能是元素，文本节点，注释或者处理指令。

```
 <ul id="myList">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
</ul>
var ul = document.getElementById('myList')
console.log(ul.childNodes.length)
```

如上代码在IE中会打印3个，但是在其他浏览器中会返回7个（包括li之间的空白），换行空白以text节点的形式存在。

因此最好遍历是，对节点的nodeType进行判断，然后在执行某些操作

如果想通过某个特性的标签名去获取他的子节点或者后代节点时。元素可以向document一样，调用getElementById和byTabName这些方法。

