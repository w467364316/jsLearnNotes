通过使用ActivexObjecct（类型）创建返回一个Document实例对象。

```js
function createDocument(){
    if (typeof arguments.callee.activeXString != "string"){
    var versions = ["MSXML2.DOMDocument.6.0", "MSXML2.DOMDocument.3.0", "MSXML2.DOMDocument"],
     i, len;
    for (i=0,len=versions.length; i < len; i++){
        try {
            new ActiveXObject(versions[i]);
            arguments.callee.activeXString = versions[i];
            break;
        } catch (ex){ //跳过
            } }
    }
    return new ActiveXObject(arguments.callee.activeXString);
}
```

使用loadXML\(xml字符串\)来加载xml。

如果出错，那么可以在parserError属性中找到错误信息

```js
if (xmlDom.parserError.errorCode != 0) {
    有错误发生
}
```



## 序列化XML

IE中每个DOM结点都有一个xml属性，其中保存着该节点的xml字符串。



## 加载XML文件

使用load\(xml地址\)加载xml文件，async属性表示是否异步，true为异步，false为同步。

同步状态下会根据代码逐句执行，如果是异步加载的情况下，使用想XML DOM 的onreadystatechange事件处理，有4个就绪状态（readyState属性），一般是判断值为4的时候，表示DOM已经可以完全使用了。

```js
var xmlDom = createDocument();
xmlDom.asyn = true;
xmlDom.onreadystatechange = function () {
    if (xmlDom.readyState == 4) {
        if (xmlDom.parseError.errorCode != 0) {
            alert('出错')
        }else {
            正常操作XML DOM对象。
        }
    }
}
```

**注意：在 XML DOM的事件处理程序内部不能使用this，只能使用代表XML DOM的变量。**



