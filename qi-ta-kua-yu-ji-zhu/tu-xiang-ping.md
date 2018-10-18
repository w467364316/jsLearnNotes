使用img标签实现跨域发送请求

通过对img元素的load事件处理程序和设置src

```
var img = document.createElment('img')
img.onload = function () {
    alert('done')
}
img.onerror = function () {
    alert('error')
}
img.src = 'http://www.example.com/test?name=123'
```

常用于跟踪统计用户点击页面或动态广告曝光次数，

主要的缺点为：

* 只能发送get请求。
* 无法访问服务器的响应文本。





