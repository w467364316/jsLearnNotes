# 位置操作

使用location对象有很多方式改变浏览器的位置

* assign\(\) 方法，传递一个URL值
  * location.assign\('[http://www.baidu.com'\](http://www.baidu.com'\)\)
  * 打开新的URL并在浏览器的历史记录中生成一条记录。
  * 如果是直接调用location.href = '[http://xxx.xxx.xxx'或者window.location='http://xxx.xxx.xxx'，也会以该值调用assign\(\)方法。](http://xxx.xxx.xxx'或者window.location='http://xxx.xxx.xxx'，也会以改值调用assign%28%29方法。)
  * 通常使用的比较多的是location.href
* 修改location的其他属性也可以改变当前记载的页面。
  * 比如hash,search,hostname,pathname等
  * 除了has之外，每次需改其他的属性都会以新URL重新加载
  * 这些操作会在浏览器的历史记录中生成一条新的记录，可以通过单击后退按钮返回上一个页面
* replace\(\)接受一个参数，即要导航到的URL
  * 结果会导致浏览器位置的改变，但是不会在历史记录中生成新的记录
* reload\(\)方法，重新加载当前页面
  * 如果不传递参数，默认会从缓存中重新加载
  * 如果传递参数true，则会重新从服务端请求
  * 调用reload方法会后，reload之后的代码可能会也可能不会执行，所以最好将reload方法放在代码最后一行。



