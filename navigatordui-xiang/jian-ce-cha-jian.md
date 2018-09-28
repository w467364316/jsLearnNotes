使用navigator的plugins属性进行检测，该方法会返回一个插件数组，数组的每一项都包含下列属性：

* name : 插件的名字
* descriotion: 插件的描述
* filename : 插件的文件名
* length: 插件所处理的MIME类型数量



针对非IE的其他浏览器，可以使用plugins集合中是否有name匹配来检测插件

```
function hasPlugin (name) {
    name = name.toLowerCase();
    for (var i =0;i<navigator.plugins.length;i++) {
        var plugin = navigator.plugins[i]
        if (plugin.name.toLowerCase().indexOf(name)>-1) {
            return true
        }
    }
    return false
}
```

对于IE浏览器来说，IE是根据COM对象实现插件，所以检测IE中插件的方法为是否可以创建COM对象的实例。如下代码所示：

```
function hasIEPlugin(name) {
    try {
        new ActiveXObject(name)
        return true
    }catch(error) {
        return false
    }
}
```



最好的解决方法应该是将两种方法结合起来使用![](/assets/import10.png)



