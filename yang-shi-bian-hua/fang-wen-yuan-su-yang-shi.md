## style属性

可以通过元素的style属性访问style特性指定的样式信息，**但是不包含外部的样式表或者是嵌入样式表经过层叠而来的样式**。

```
<div style="width:10px;height:10px;color:red;"></div>

var div = document.getElementByTagName('div')[0]
console.log(div.style.color)  //red
div.style.color = yellow;   //修改样式
```

DOM2对style对象提供的一些属性和方法：

* cssText : 访问到style特性中的css代码
  * 写入模式下，会直接重写覆盖元素之前css属性的值
* length : 应用给css属性的数量
* parentRule：css信息的parentRule对象
* getPropertyCSSValue（propertyName）: 返回给定属性值的CSSRule类型
  * **get等方法设置时的propertyName格式都是小写短线，并不是驼峰格式**
  * **'background-color'而不是backgroundColor‘’**
* getPropertyPriority\(propertyName\): 返回给定属性值的优先级
* getPropertyValue\(propertyName\)：返回给定属性的字符串值
* item\(index\) 返回给定位置的属性值名称
  * 使用item或者方括号都可以直接返回对应位置的css属性名
  * **短线分开的比如‘background-color’在用这个方法获取之后返回的就是‘‘background-color’，并不是‘backgroundColor’**
* removeProperty（propertyName）从样式中删除给定的属性
* setProperty\(propertyName,value,priority\) 将给定的属性设置为相应的值，并加上优先权标志。



## 计算的样式

style可以获取style特性中的样式信息，但是对于其他样式层叠表来的样式信息并不能获取到。

DOM2增强了document.defaultView，提供了getComputedStyle\(\)方法来获取计算样式，有两个参数，第一个参数为要取得计算样式的元素和一个伪元素字符串（比如：after）,如果不需要第二个参数可以是null。

```
var div = document.getElementById('name')
var computedStyle = document.defaultView.getComputedStyle(div,null)
```

IE不支持getComputedStyle方法，但是style对象有一个currentStyle属性，也是CSSStyleDeclaration的实例，包含当前元素全部计算后的样式。

**注意：计算样式不能够进行修改，只是只读的**



