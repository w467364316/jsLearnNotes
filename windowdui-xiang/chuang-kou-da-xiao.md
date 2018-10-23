# 窗口大小

虽然IE chrome  opera firefox safari等浏览器都提供了innerWidth，innerHeight，outerWidth，outerHeight属性，但是但是因为浏览器的差异，所以得到的值并不是统一的。

## 页面视口大小

**众多浏览器都提供了 document.documentElement.clientHeight和document.documentElement.clientWidth来获取页面视口的大小。**但是对于IE6，在混杂模式下，必须通过document.body.clientWidth和Height来获取，因此可以如下方法表示：

```js
 var pageWidth = window.innerWidth,
        pageHeight = window.innerHeight;
    if (typeof pageWidth != "number"){
        if (document.compatMode == "CSS1Compat"){  //判断是否标准模式
            pageWidth = document.documentElement.clientWidth;
            pageHeight = document.documentElement.clientHeight;
        } else {
            pageWidth = document.body.clientWidth;
            pageHeight = document.body.clientHeight;
        }
}
```

* resizeTo\(\)和resizeBy\(\)
  * 调整浏览器窗口的大小，都接受两个参数，前者接受浏览器窗口的新宽度和新高度，后者接受浏览器窗口宽高要减去的值。



