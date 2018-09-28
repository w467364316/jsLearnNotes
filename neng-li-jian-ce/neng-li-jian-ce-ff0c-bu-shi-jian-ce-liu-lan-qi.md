根据浏览器不同将能力组合起来检测是更加可取的方式，如果你知道自己的应用程序需要安装使用某些特性的浏览器特性，那么最好是一次性检测所有相关特性，而不要分别检测。

```
var hasDOM1 = !!(document.getElement&& docment.createElement
                &&document.getElementByTagNames)
```

在实际开发中，应该讲能力检测作为确定下一步解决方案的依据，而不是用它来判断用户使用的是什么浏览器。







