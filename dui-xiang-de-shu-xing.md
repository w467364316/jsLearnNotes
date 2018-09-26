# 理解对象

## 1 对象的属性类型

* 对象的属性类型分为数据属性和访问器属性
* 每一个属性都有对应的特性，比如是否可以删除，是否可以改变，是否可以通过for-in循环等特性

### 1.1 数据属性

数据属性包含一个数据值的位置，再找个位置可以读取和写入值。主要有4个描述行为的特性

* \[\[Configurable\]\] :  能够修改属性的特性，能够通过delete将属性删除。直接在对象上定义的属性，该特性默认为true
  * 如果为false，那么不能通过delete将该属性删除，同时此时再调用defineProperty是，智能修改writable特性，不能修改其他的特性。
* \[\[Enumerable\]\] : 能够通过for-in进行循环遍历将属性返回。 直接在对象上定义的属性，该特性默认为true
  * 如果为false，则不能通过for-in将属性返回。
* \[\[Writable\]\]: 表示能够修改属性的值。 直接在对象上定义的属性，该特性默认为true
  * 如果为false，则属性值不能修改
* \[\[value\]\]: 包含属性的数据值，特性的默认值为undefine

对于直接使用对象字面量或者new Object\(\)设置的属性，Configurable Writable Enumerable 默认都是true，value特性被设置为指定的值。

要修改默认属性的特性，必须使用Object.defineProperty\(\)方法，主要有3个参数

* 第一个参数为属性所属的独享
* 第二个参数为要设置的属性名
* 第三个参数为一个特性描述符对象，该对象的属性必须是 configurable, writeable,value,enumerable
* ```js
  var book = {}
  Object.defineProperty(book,'name',{
      value: 'name',
      writable: true,
      enumerable: false,
      configurable: true
  })
  ```
* 在调用该方法是，如果不设置描述符对象，那么默认都是false

* 可以通过多次调用defineProperty方法修改属性

### 1.2 访问器属性

包含一对getter和setter函数（不是必须要编写的），特性主要有

* \[\[Configurable\]\]
* \[\[Enumerable\]\]
* \[\[getter\]\] 默认值为undefine，值为function函数
* \[\[setter\]\] 默认值为undefine，值为function函数

访问属性不能直接定义！！需要使用Object.definProperty（）方法。参数和数据属性的参数是一样的。

* 如果只是定义了getter方法，那么表示该属性不可赋值修改
* 如果只是定义了setter方法，俺么表示该属性不可读取

## 2 定义多个属性

使用Object.definProperties（）方法来定义多个属性，参数为两个

* 第一个参数为要设置的对象
* 第二参数对象为要设置的属性和属性的特性
* ```js
  var person = {}
  Object.definProperties(person,{
      _year: {
          value: 2004
      },
      edition: {
          value: 2
      },
      year: {
          get: function(){
              return this._year;
          },
          set: function (newValue) {
              this._year = newValue;
              this.edition += newValue-2004;
          }
      }
  })
  ```

## 3 读取属的特征

3.1使用Object.getOwnPorpertyDescriptor\(\) 方法读取，会返回一个包含属性特性的对象。

