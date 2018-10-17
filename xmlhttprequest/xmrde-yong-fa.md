IE7以上以及其他浏览器，可以直接使用原生的XMR对象，使用XMLHttpRequest创建。

1. 使用new XMLHttpRequest\(\) 创建一个XMR对象
2. 可以添加onreadystatechange事件处理程序来监控XMR请求的状态
   1. 一般为通过检测XMR对象的readyState==4时，表示已经接收到全部的相应数据，并且可使用
      1. 然后使用XMR.status（HTTP的响应状态）来判断
      2. 如果status为200或者304，那么就可以使用XMR.responseText读取返回的文本信息，或者通过XMR.responseXML获取返回的XML文档。
3. 使用XMR.open\(\)设置请求，准备发送
   * 第一个参数为请求的类型。post或者get
   * 第二个参数为请求的地址，url
   * 第三个参数为是否异步，true表示异步，false表示同步。
4. 可以使用XMR.setRequestHeader\(key,value\)添加自定义的HTTP请求头信息。
5. 使用XMR.send\(\)发送请求。

## readystatechange事件

以DOM0的方式给XMR对象添加onreadystatechange事件，并且在open\(\)方法之前调用。

**可以调用XMR.abort\(\)方法取消异步请求**

## HTTP头部信息

使用setRequestHeader\(key,value\)必须放在open\(\)之后，send\(\)之前调用。

调用XMR.getResponseHeader\(key\)可以获取相应属性名的信息

调用XMR.getAllResponseHeaders\(）可以获取一个包含着所有头部信息的长字符串。

## GET请求

get请求的请求参数直接跟在url后面，第一个参数和url以？链接，后面的参数与参数之间用&链接。**并且参数都需要使用encodeURIComponent\(\)编码。**

## POST请求

post请求的主体是通过send\(\)方法发送，跟get的直接拼接在url后面不一样。

服务器一般对POST请求和提交web表单的请求不会一视同仁，那么可以将HTTP头部信息之中的Contet-type设置为'application/x-www-form-urencoded'表示提交时的内容类型是表单类型，那么在服务器端就可以通诸如$\_post的形式来获取相应的参数。

