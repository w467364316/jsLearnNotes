# Global对象

可以理解为所有在全局作用域只定义的属性和函数，其实都是Global对象的属性，比如 parseInt\(\) isNaN\(\) 等都是。

## Global对象的其他方法

### 1.URL编码方法

* encodeURL\(\)
  * 对于整个URL进行编码，用特殊的UTF-8字符替换无效的字符，比如空格
* encodeURLComponent\(\)
  * 对于任何非标准的字符都会进行编码
* decodeURL
  * 对应encodeURL方法，对编码的URL进行解码
* decodeURLComponent
  * 对应encodeURLComponent，对编码的URL进行解码

### 2.eval方法

相当于一个ECMAScript解析器，会将参数当做js语句来解析

* 所以eval参数中也可以定义变量，定义函数，在同一个执行环境下定义的变量在其他地方也能使用

### 3.window对象

web浏览器将global全局对象作为window对象的一部分加以实现。

所以，在全局作用域中声明的所有对象和函数，就都成为了window对象的属性。



