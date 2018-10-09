CSSStyleSheet类型表示的是样式表CSSStyleSheet继承自CSSSheet类型，继承了一些属性和方法。

文档中包含的样式表，包括使用link或者style引入的都是通过document.styleSheets集合来表示：

* length可以获取文档中样式表的数量
* item\(\)或者方括号index可以获取对应位置的样式表。

也可以通过link或者style元素的sheet或者styleSheet\(IE中\)获取到单个样式表![](/assets/import14.png)

## 1 css规则

如上图所示，单个样式表中包含了很多条CSS规则，为CSSRule类型实例，上图中主要是CSSStyleRule对象，规则对象主要的属性为：

* cssText 返回规则对应的文本表示
  * 这里和元素的style对象的cssText类似，但是有区别
  * ```
    rule对象：
    rule.cssText=> ‘#app{height:100px;width:100px;}’
    元素.style.cssText => ‘height:100px;width:100px;’
    ```
  * 元素style对象的cssText是可以直接写入替换的，但是rule中的cssText仅仅是只读。
* parentRule 如果当前规则是使用import等导入的，那么该属性指向导入规则，否则为null。IE不支持

* parentStyleSheet 当前规则所属的样式表 。IE不支持

* selectorText 返回当前规则的选择文本，比如 '\#app'

* style： 一个CSSStyleDeclaration对象，可以读写规则中的样式

* type :  表示规则类型的常量值

## 2 创建规则

使用sheet.insertRule\(\)创建规则，第一个参数为rule规则的文本表示，第二个参数为插入的位置。

```js
var styleSheet = document.styleSheets[0]
styleSheet.inserRule ('#app{height:100px;width:50px;}',0)  
表示在文档的第一个样式表中的开头位置插入一个style规则
```

在IE中是使用addRule\(\)参数为3个，分别是选择符文本，规则文本，和位置

```
var styleSheet = document.styleSheets[0]
styleSheet.addRule('#app','height:100px;width:100px;',0)
```

所以可以编写一个兼容函数进行相应操作

## 3 删除规则

sheet.deleteRule\(index\) ，IE中是removeRule\(index\)

