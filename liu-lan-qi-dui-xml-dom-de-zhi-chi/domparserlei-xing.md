用于将XML解析成DOM文档：

1. 首先创建一个DOMParse实例
2. 然后调用parserFromString\(\)
   1. 第一个参数为要解析的xml字符串
   2. 第二个参数为内容类型（内容类型始终都是‘text/xml’）
3. 会返回一个Document实例



发生错误时，任然会返回一个Document对象，但是是以&lt;parsererror&gt;元素为根元素。但是IE9会直接在调用parserFromString时抛出错误，所以最好的方法就是使用一个try-catch语句块。如果没有错误，则从返回的Document对象找寻是否有parsererror元素。



